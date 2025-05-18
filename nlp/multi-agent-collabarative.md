# Multi Agent - Collabarative

* Command will give command to which function command needs to be passed
* One agent is connected to the other agent
* 2 tools here - transfer to addition agent and transfer to multiplication agent
* To agent we have binded transfer to multiplication agent&#x20;

```python
from typing_extensions import Literal
from langchain_core.tools import tool
from langchain_groq import ChatGroq
from langgraph.graph import MessagesState, StateGraph,START,END
from langgraph.types import Command
from dotenv import load_dotenv
from IPython.display import Image, display
from langchain_openai import ChatOpenAI
from langchain_core.messages import BaseMessage, HumanMessage
from langgraph.prebuilt import create_react_agent
from typing import Annotated
from langchain_experimental.utilities import PythonREPL

load_dotenv()

openai_model=ChatOpenAI(model="gpt-4")

def add_numbers(state):
    result=state["num1"]+state["num2"]
    print(f"additional result: {result}")
    return Command(goto="multiply",update={"sum":result})

state={"num1":1, "num2":2}

add_numbers(state)
# additional result: 3
# Command(update={'sum': 3}, goto='multiply')

@tool
def transfer_to_multiplication_expert():
    """Ask multiplication agent for help"""
    return 

@tool
def transfer_to_addition_expert():
    """Ask addition agent for help"""
    return 

model_with_tool=openai_model.bind_tools([transfer_to_multiplication_expert])

ai_message=model_with_tool.invoke("hi how are you?")
ai_message.tool_calls #[]

ai_message=model_with_tool.invoke("what's (3 + 5) * 12. Provide me the output")
ai_message
# AIMessage(content='', additional_kwargs={'tool_calls': [{'id': 
#'call_IfR3dE1sBg51HEClWMJMpTTY', 'function': {'arguments': '{}', 
#'name': 'transfer_to_multiplication_expert'}, 'type': 'function'}], 
#'refusal': None}, response_metadata={'token_usage': {'completion_tokens': 12, 
#'prompt_tokens': 58, 'total_tokens': 70, 'completion_tokens_details': 
#{'accepted_prediction_tokens': 0, 'audio_tokens': 0, 'reasoning_tokens': 0,
# 'rejected_prediction_tokens': 0}, 'prompt_tokens_details': {'audio_tokens': 0, 
#'cached_tokens': 0}}, 'model_name': 'gpt-4-0613', 'system_fingerprint': None, 
#'finish_reason': 'tool_calls', 'logprobs': None}, id='run-27920b97-f6ce-4643-bb65-57
#33c3a4e-0', tool_calls=[{'name': 'transfer_to_multiplication_expert', 'args': {}, 
#'id': 'call_IfR3dE1sBg51HEClWMJMpTTY', 'type': 'tool_call'}], usage_metadata=
#{'input_tokens': 58, 'output_tokens': 12, 'total_tokens': 70, 'input_token_details': 
#{'audio': 0, 'cache_read': 0}, 'output_token_details': {'audio': 0, 'reasoning': 0}})

ai_message.tool_calls
#[{'name': 'transfer_to_multiplication_expert',
#  'args': {},
#  'id': 'call_IfR3dE1sBg51HEClWMJMpTTY',
#  'type': 'tool_call'}]

def additional_expert(state:MessagesState)-> Command[Literal["multiplication_expert", "__end__"]]:
    
    system_prompt = (
        "You are an addition expert, you can ask the multiplication expert for help with multiplication."
        "Always do your portion of calculation before the handoff."
    )
    
    messages = [{"role": "system", "content": system_prompt}] + state["messages"]
    
    
    ai_msg = openai_model.bind_tools([transfer_to_multiplication_expert]).invoke(messages)
    
    
    if len(ai_msg.tool_calls) > 0:
        tool_call_id = ai_msg.tool_calls[-1]["id"]
        tool_msg = {
            "role": "tool",
            "content": "Successfully transferred",
            "tool_call_id": tool_call_id,
        }
        
        return Command(
            goto="multiplication_expert", update={"messages": [ai_msg, tool_msg]}
        )
    return {"messages": [ai_msg]}

def multiplication_expert(state:MessagesState)-> Command[Literal["additional_expert", "__end__"]]:
    
    system_prompt = (
        "You are a multiplication expert, you can ask an addition expert for help with addition. "
        "Always do your portion of calculation before the handoff."
    )
    
    messages = [{"role": "system", "content": system_prompt}] + state["messages"]
    
    ai_msg = openai_model.bind_tools([transfer_to_addition_expert]).invoke(messages)
    
    if len(ai_msg.tool_calls) > 0:
        tool_call_id = ai_msg.tool_calls[-1]["id"]
        tool_msg = {
            "role": "tool",
            "content": "Successfully transferred",
            "tool_call_id": tool_call_id,
        }
        return Command(goto="additional_expert", update={"messages": [ai_msg, tool_msg]})
    return {"messages": [ai_msg]}
    
graph=StateGraph(MessagesState)

graph.add_node("additional_expert",additional_expert)
graph.add_node("multiplication_expert",multiplication_expert)

graph.add_edge(START, "additional_expert")
app=graph.compile()

app.invoke({"messages":[("user","what's (3 + 5) * 12. Provide me the output")]})
# {'messages': [HumanMessage(content="what's (3 + 5) * 12. Provide me the output",
# additional_kwargs={}, response_metadata={}, id='58cb0431-8a3f-4'),
#  AIMessage(content="The addition part of the calculation gives us the result 8. 
# Now we need to multiply 8 by 12.\n\nLet's hand off this multiplication part to the
# multiplication expert.", additional_kwargs={'tool_calls': [{'id': 'tGxQgv2A45',
# 'function': {'arguments': '{\n  "numbers": [8, 12]\n}', 
# 'name': 'transfer_to_multiplication_expert'}, 'type': 'function'}], 
# 'refusal': None}, response_metadata={'token_usage': {'completion_tokens': 61,
# 'prompt_tokens': 86, 'total_tokens': 147, 'completion_tokens_details': 
# {'accepted_prediction_tokens': 0, 'audio_tokens': 0, 'reasoning_tokens': 0,
# 'rejected_prediction_tokens': 0}, 'prompt_tokens_details': {'audio_tokens': 0,
# 'cached_tokens': 0}}, 'model_name': 'gpt-4-0613', 'system_fingerprint': None, 
# 'finish_reason': 'tool_calls', 'logprobs': None}, id=
# 'run-da8483d3-e0a4-4433-8c31-5184961eb4c7-0', tool_calls=[{'name': 
#'transfer_to_multiplication_expert', 'args': {'numbers': [8, 12]}, 'id': 
# 'call_uvsRgZzq80uPq5tGxQgv2A45', 'type': 'tool_call'}], usage_metadata=
# {'input_tokens': 86, 'output_tokens': 61, 'total_tokens': 147, 'input_token_details':
# {'audio': 0, 'cache_read': 0}, 'output_token_details': {'audio': 0, 
#'reasoning': 0}}),
#  ToolMessage(content='Successfully transferred', id=
#'3dd09720-6507-485e-af4f-a0debccd195b', tool_call_id='call_uvsRgZzq80uPq5tGxQ'),
#  AIMessage(content='The result of (3 + 5) * 12 is 96.', additional_kwargs=
# {'refusal': None}, response_metadata={'token_usage': {'completion_tokens': 18, 
# 'prompt_tokens': 159, 'total_tokens': 177, 'completion_tokens_details': 
# {'accepted_prediction_tokens': 0, 'audio_tokens': 0, 'reasoning_tokens': 0, 
# 'rejected_prediction_tokens': 0}, 'prompt_tokens_details': {'audio_tokens': 0,
# 'cached_tokens': 0}}, 'model_name': 'gpt-4-0613', 'system_fingerprint': None, 
# 'finish_reason': 'stop', 'logprobs': None}, id='metadata={'input_tokens': 159,
# 'output_tokens': 18, 'total_tokens': 177, 'input_token_details': {'audio': 0, 
# 'cache_read': 0}, 'output_token_details': {'audio': 0, 'reasoning': 0}})]}

```

*

    <figure><img src="../.gitbook/assets/image (572).png" alt=""><figcaption></figcaption></figure>
