# LangGraph - Human in Loop

* Here we will be needing tavily API key&#x20;
* [https://tavily.com/](https://tavily.com/)
* Tavily is a search engine optimized for LLMs, aimed at efficient, quick and persistent search results. Unlike other search APIs such as Serp or Google, Tavily focuses on optimizing search for AI developers and autonomous AI agents
* Human in loop means we want manual intervention
* Here we are asking user for prompt for y/n for expensive web search — This is known as human in loop

```python
from typing import Annotated
import operator,json
from typing import TypedDict, Annotated, Sequence
from typing_extensions import TypedDict
from langchain_core.messages import BaseMessage
from langgraph.checkpoint.memory import MemorySaver
from langgraph.graph import StateGraph,END,START
from langgraph.graph.message import add_messages
from langgraph.prebuilt import ToolNode, tools_condition
from langchain_core.tools import tool
from langchain_community.tools.tavily_search import TavilySearchResults

import os
from langchain_community.tools.tavily_search import TavilySearchResults
TAVILY_API_KEY="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"
os.environ["TAVILY_API_KEY"]=TAVILY_API_KEY

import os
os.environ["TAVILY_API_KEY"]=TAVILY_API_KEY

@tool
def multiply(first_number:int, second_number:int)->int:
    """multiply two integer number"""
    return first_number * second_number

@tool
def search(query:str):
    """perform the web search on the user query"""
    tavily=TavilySearchResults(tavily_api_key="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")
    result=tavily.invoke(query)
    return result

search.invoke("who is a current PM in india?")
#[{'title': 'Prime Minister of India - Wikipedia',
#  'url': 'https://en.wikipedia.org/wiki/Prime_Minister_of_India',
#  'content': "Rao, Atal....",
#  'score': 0.8827621},
# {'title': "PM Sangrahlaya - a Tribute to India's Prime Ministers",
#  'url': 'https://www.pmsangrahalaya.gov.in/prime-ministers-of-india',
#  'content': 'Shri Narendra Modi ....',
#  'score': 0.83710164},
# {'title': 'Narendra Modi - Wikipedia',...]

tools=[search,multiply]
model_with_tools=openai_model.bind_tools(tools)

model_with_tools.invoke("who is a cuurent pm of japan?").tool_calls
#[{'name': 'search',
#  'args': {'query': 'current Prime Minister of Japan'},
#  'id': 'call_iMGTBCIRmIvdL5t3OyXfKUCr',
#  'type': 'tool_call'}]

tool_mapping={tool.name: tool for tool in tools}
# {'search': StructuredTool(name='search', description='perform the web search on the
#  user query', args_schema=<class 'langchain_core.utils.pydantic.search'>, 
# func=<function search at 0x0000017563031990>),
# 'multiply': StructuredTool(name='multiply', description='multiply two integer number',
# args_schema=<class 'langchain_core.utils.pydantic.multiply'>, func=<function multiply
# at 0x0000017560700B80>)}

response=model_with_tools.invoke("who is a current president of uk?")
tool_details=response.additional_kwargs
#{'tool_calls': [{'id': 'call_tanGhlPkC5GFIsk5g68KSgMd',
#   'function': {'arguments': '{"query":"current president of UK 2023"}',
#    'name': 'search'},
#   'type': 'function'}],
# 'refusal': None}

tool_details=tool_details.get("tool_calls")
tool_details[0]["function"]["name"] # 'search'
tool_details[0]["function"]["arguments"]  # '{"query":"current president of UK 2023"}'
json.loads(tool_details[0]["function"]["arguments"]) # {'query': 'current president of UK 2023'}
tool_mapping[tool_details[0]["function"]["name"]].invoke(json.loads(tool_details[0]["function"]["arguments"]))
# Above statement will return the results from tool by passing function and query

class AgentState(TypedDict):
    messages:Annotated[Sequence[BaseMessage], operator.add]
    
def invoke_model(state:AgentState):
    messages = state['messages']
    question = messages[-1]   ## Fetching the user question
    return {"messages":[model_with_tools.invoke(question)]}
    
def invoke_tool(state:AgentState):
    print("****my state*****")
    print(state['messages'][-1])
    tool_details= state['messages'][-1].additional_kwargs.get("tool_calls", [])[0]
    
    if tool_details is None:
        raise Exception("no tool call found")
    
    print(f'Selected tool: {tool_details.get("function").get("name")}')
    
    if tool_details.get("function").get("name")=="search":
        print("**********tool detils****")
        print(tool_details)
        response = input(prompt=f"[y/n] continue with expensive web search?")
        if response == "n":
            raise Exception("web search discard")
        
    response = tool_mapping[tool_details['function']['name']].invoke(json.loads(tool_details.get("function").get("arguments")))
    return {"messages" : [response]}
    
def router(state:AgentState):
    tool_calls = state['messages'][-1].additional_kwargs.get("tool_calls", [])
    if len(tool_calls):
        return "tool"
    else:
        return "end"
    
graph=StateGraph(AgentState)

graph.add_node("ai_assistant",invoke_model)
graph.add_node("tool",invoke_tool)

graph.add_conditional_edges("ai_assistant",
                            router,
                            {"tool":"tool",
                             "end":END})

graph.add_edge("tool", END)

# graph.add_edge("tool", "ai_assistant")

graph.set_entry_point("ai_assistant")

app=graph.compile()

app.invoke({"messages": ["who is upcoming president of USA?"]})
# This will ask for prompt
#{'messages': ['who is upcoming president of USA?',
#  AIMessage(content='', additional_kwargs={'tool_calls': [{'id': 'call_XQcn9xLA5dz6e2DLYE5qTSPY', 'function': {'arguments': '{"query":"upcoming president of USA 2023"}', 'name': 'search'}, 'type': 'function'}], 'refusal': None}, response_metadata={'token_usage': {'completion_tokens': 21, 'prompt_tokens': 76, 'total_tokens': 97, 'completion_tokens_details': {'accepted_prediction_tokens': 0, 'audio_tokens': 0, 'reasoning_tokens': 0, 'rejected_prediction_tokens': 0}, 'prompt_tokens_details': {'audio_tokens': 0, 'cached_tokens': 0}}, 'model_name': 'gpt-4o-2024-08-06', 'system_fingerprint': 'fp_22890b9c0a', 'finish_reason': 'tool_calls', 'logprobs': None}, id='run-ca64a716-63bf-4f0b-9aae-e52bd8033f66-0', tool_calls=[{'name': 'search', 'args': {'query': 'upcoming president of USA 2023'}, 'id': 'call_XQcn9xLA5dz6e2DLYE5qTSPY', 'type': 'tool_call'}], usage_metadata={'input_tokens': 76, 'output_tokens': 21, 'total_tokens': 97, 'input_token_details': {'audio': 0, 'cache_read': 0}, 'output_token_details': {'audio': 0, 'reasoning': 0}}),
#  [{'title': '2024 United States presidential election - Wikipedia',
#    'url': 'https://en.wikipedia.org/wiki/2024_United_States_presidential_election',
#    'content': '^ Hippensteel,.....',
#    'score': 0.7598145},
#   {'title': 'Joe Biden 2024 presidential campaign - Wikipedia',
#    'url': 'https://en.wikipedia.org/wiki/Joe_Biden_2024_presidential_campaign',
#    'content': '2020 electionselectionconventiondebate.....',
#    'score': 0.7355091},
#   {'title': 'United States presidential election of 2024 - Britannica',
#    'url': 'https://www.britannica.com/event/United-States-presidential-election-of-2024',
#    'content': 'Trump faced far ....',
#    'score': 0.67347145}]]}

app.invoke({"messages": ["what is multiplication of 23 and 46?"]})
# This time multiplication tool will be called

app.invoke({"messages": ["what is today's match score?"]})
# Here search tool will be called


```

*

    <figure><img src="../.gitbook/assets/image (570).png" alt=""><figcaption></figcaption></figure>
