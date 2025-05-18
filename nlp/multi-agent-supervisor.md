# Multi Agent - Supervisor

* &#x20;

```python
from typing import Annotated
from typing import Literal
from langchain_community.tools.tavily_search import TavilySearchResults
from langchain_core.tools import tool
from langchain_experimental.utilities import PythonREPL
from typing_extensions import TypedDict
from langgraph.graph import MessagesState, END,StateGraph, START
from langgraph.types import Command
from langchain_core.messages import HumanMessage
from langgraph.prebuilt import create_react_agent

TAVILY_API_KEY="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"


import os
os.environ["TAVILY_API_KEY"]=TAVILY_API_KEY

tavaily_tool=TavilySearchResults()

@tool
def python_repl_tool(
    code: Annotated[str, "The python code to execute to generate your chart."],
):
    """Use this to execute python code and do math. If you want to see the output of a value,
    you should print it out with `print(...)`. This is visible to the user."""
    
    try:
        result = repl.run(code)
    except BaseException as e:
        return f"Failed to execute. Error: {repr(e)}"
    
    result_str = f"Successfully executed:\n\`\`\`python\n{code}\n\`\`\`\nStdout: {result}"
    return result_str

code = """
x = 5
y = x * 2
print(y)
"""

repl=PythonREPL()
repl.run(code)
# '10\n'

members=["researcher","coder"]
options=members+["FINISH"]
options
# ['researcher', 'coder', 'FINISH']

class Router(TypedDict):
    """Worker to route to next. If no workers needed, route to FINISH."""
    next: Literal['researcher', 'coder', 'FINISH']

class State(MessagesState):
    next:str

system_prompt=f"""
You are a supervisor, tasked with managing a conversation between the following workers: {members}. 
Given the following user request, respond with the worker to act next. 
Each worker will perform a task and respond with their results and status. 
When finished, respond with FINISH.
"""

[{"role": "system", "content": system_prompt},]

def supervisor_node(state: State) -> Command[Literal["researcher", "coder", "__end__"]]:
    
    messages = [{"role": "system", "content": system_prompt},] + state["messages"]
    response = openai_model.with_structured_output(Router).invoke(messages)
    
    goto = response["next"]
    print("below my goto**********************************")
    print(goto)
    
    if goto == "FINISH":
        goto = END
        
    return Command(goto=goto, update={"next": goto})

def research_node(state: State) -> Command[Literal["supervisor"]]:
    
    research_agent = create_react_agent(openai_model, tools=[tavaily_tool], prompt="You are a researcher. DO NOT do any math.")
    
    result = research_agent.invoke(state)
    
    return Command(
        update={
            "messages": [
                HumanMessage(content=result["messages"][-1].content, name="researcher")
            ]
        },
        goto="supervisor",
    )

def code_node(state: State) -> Command[Literal["supervisor"]]:
    
    code_agent = create_react_agent(openai_model, tools=[python_repl_tool])
    
    result = code_agent.invoke(state)
    
    return Command(
        update={
            "messages": [
                HumanMessage(content=result["messages"][-1].content, name="coder")
            ]
        },
        goto="supervisor",
    )

graph=StateGraph(State)
graph.add_node("supervisor",supervisor_node)
graph.add_node("researcher", research_node)
graph.add_node("coder", code_node)

graph.add_edge(START,"supervisor")
app=graph.compile()

for s in app.stream({"messages": [("user", "What's the square root of 42?")]}, subgraphs=True):
    print(s)
    print("----")
#below my goto**********************************
#coder
#((), {'supervisor': {'next': 'coder'}})
#----
#(('coder:929a27fb-660c-b656-a51d-25522ab43a9c',), {'agent': {'messages': [AIMessage(content='', additional_kwargs={'tool_calls': [{'id': 'call_8FiaRQOsZ2UddTEYZzj1th8L', 'function': {'arguments': '{\n  "code": "import math\\nprint(math.sqrt(42))"\n}', 'name': 'python_repl_tool'}, 'type': 'function'}], 'refusal': None}, response_metadata={'token_usage': {'completion_tokens': 25, 'prompt_tokens': 100, 'total_tokens': 125, 'completion_tokens_details': {'accepted_prediction_tokens': 0, 'audio_tokens': 0, 'reasoning_tokens': 0, 'rejected_prediction_tokens': 0}, 'prompt_tokens_details': {'audio_tokens': 0, 'cached_tokens': 0}}, 'model_name': 'gpt-4-0613', 'system_fingerprint': None, 'finish_reason': 'tool_calls', 'logprobs': None}, id='run-bfc005b0-c3a3-4b04-925f-62ee64098dc1-0', tool_calls=[{'name': 'python_repl_tool', 'args': {'code': 'import math\nprint(math.sqrt(42))'}, 'id': 'call_8FiaRQOsZ2UddTEYZzj1th8L', 'type': 'tool_call'}], usage_metadata={'input_tokens': 100, 'output_tokens': 25, 'total_tokens': 125, 'input_token_details': {'audio': 0, 'cache_read': 0}, 'output_token_details': {'audio': 0, 'reasoning': 0}})]}})
#----
#(('coder:929a27fb-660c-b656-a51d-25522ab43a9c',), {'tools': {'messages': [ToolMessage(content='Successfully executed:\n\\`\\`\\`python\nimport math\nprint(math.sqrt(42))\n\\`\\`\\`\nStdout: 6.48074069840786\n', name='python_repl_tool', id='4084e489-8190-4750-8eaf-7429bc8de2c3', tool_call_id='call_8FiaRQOsZ2UddTEYZzj1th8L')]}})
#----
#(('coder:929a27fb-660c-b656-a51d-25522ab43a9c',), {'agent': {'messages': [AIMessage(content='The square root of 42 is approximately 6.48.', additional_kwargs={'refusal': None}, response_metadata={'token_usage': {'completion_tokens': 15, 'prompt_tokens': 166, 'total_tokens': 181, 'completion_tokens_details': {'accepted_prediction_tokens': 0, 'audio_tokens': 0, 'reasoning_tokens': 0, 'rejected_prediction_tokens': 0}, 'prompt_tokens_details': {'audio_tokens': 0, 'cached_tokens': 0}}, 'model_name': 'gpt-4-0613', 'system_fingerprint': None, 'finish_reason': 'stop', 'logprobs': None}, id='run-018f95ff-dac0-44ca-b4b1-bf07155d06b6-0', usage_metadata={'input_tokens': 166, 'output_tokens': 15, 'total_tokens': 181, 'input_token_details': {'audio': 0, 'cache_read': 0}, 'output_token_details': {'audio': 0, 'reasoning': 0}})]}})
#----
#((), {'coder': {'messages': [HumanMessage(content='The square root of 42 is approximately 6.48.', additional_kwargs={}, response_metadata={}, name='coder')]}})
#----
#c:\Complete_Content\GENERATIVEAI\NEW_E2E_COURSE\genai_bootcamp\env\lib\site-packages\langchain_openai\chat_models\base.py:1413: UserWarning: Cannot use method='json_schema' with model gpt-4 since it doesn't support OpenAI's Structured Output API. You can see supported models here: https://platform.openai.com/docs/guides/structured-outputs#supported-models. To fix this warning, set `method='function_calling'. Overriding to method='function_calling'.
#  warnings.warn(
#below my goto**********************************
#FINISH
#((), {'supervisor': {'next': '__end__'}})
#----

```

*

    <figure><img src="../.gitbook/assets/image (573).png" alt=""><figcaption></figcaption></figure>
