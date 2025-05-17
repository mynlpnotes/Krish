# LangGraph - Memory Saver

* &#x20;Every chat will be a thread
* Since we have added interrupt before tool. so tool is not executed — This can be seen in bangalore example
* We can again call app2.stream so that tool gets executed
* We can use get\_state to get entire memory details

```python
tavily=TavilySearchResults()

tools = [tavily]

llm_with_tools=openai_model.bind_tools(tools)

def ai_assistant(state: AgentState):
    return {"messages": [llm_with_tools.invoke(state["messages"])]}

memory=MemorySaver()

graph_builder = StateGraph(AgentState)
graph_builder.add_node("ai_assistant", ai_assistant)

tool_node = ToolNode(tools=tools)
graph_builder.add_node("tools", tool_node)

graph_builder.add_edge(START, "ai_assistant")

graph_builder.add_conditional_edges(
    "ai_assistant",
    tools_condition,
)
graph_builder.add_edge("tools", "ai_assistant")

app2=graph_builder.compile(
    checkpointer=memory,
    interrupt_before=["tools"]
)

user_input = "famous places of the bangalore and must visit restaurants?"
config = {"configurable": {"thread_id": "1"}}

events = app2.stream(
    {"messages": [("user", user_input)]}, config, stream_mode="values"
)

for event in events:
    print(event)
# {'messages': [('user', 'famous places of the bangalore and must visit restaurants?')]}
#{'messages': [('user', 'famous places of the bangalore and must visit restaurants?'),
# AIMessage(content='', additional_kwargs={'tool_calls': [{'id': 
# 'call_NheTr6jPV4EZPe0g1Xluhdhy', 'function': {'arguments': 
#'{"query": "famous places to visit in Bangalore"}', 'name': 'tavily_search_results_json
#'}, 'type': 'function'}, {'id': 'call_UoOT3m5svSe0vMILWeIx6l75', 'function': 
# {'arguments': '{"query": "must visit restaurants in Bangalore"}', 'name': 
# 'tavily_search_results_json'}, 'type': 'function'}], 'refusal': None},
# response_metadata={'token_usage': {'completion_tokens': 63, 'prompt_tokens': 91,
# 'total_tokens': 154, 'completion_tokens_details': {'accepted_prediction_tokens': 0,
# 'audio_tokens': 0, 'reasoning_tokens': 0, 'rejected_prediction_tokens': 0},
# 'prompt_tokens_details': {'audio_tokens': 0, 'cached_tokens': 0}},
# 'model_name': 'gpt-4o-2024-08-06', 'system_fingerprint': 'fp_92f14e8683',
# 'finish_reason': 'tool_calls', 'logprobs': None},
# id='run-afa8bec0-9f5c-4783-94df-7beb2bb893d7-0', tool_calls=[{'name':
# 'tavily_search_results_json', 'args': {'query': 'famous places to visit in Bangalore'
#}, 'id': 'call_NheTr6jPV4EZPe0g1Xluhdhy', 'type': 'tool_call'}, {'name': 
# 'tavily_search_results_json', 'args': {'query': 'must visit restaurants in Bangalore'}
#, 'id': 'call_UoOT3m5svSe0vMILWeIx6l75', 'type': 'tool_call'}], usage_metadata=
#{'input_tokens': 91, 'output_tokens': 63, 'total_tokens': 154, 'input_token_details':
# {'audio': 0, }, 'output_token_details': {'audio': 0, 'reasoning': 0}})]}

snapshot=app2.get_state(config)
snapshot.next
# ('tools',)

last_message=snapshot.values["messages"][-1]
last_message.tool_calls
#[{'name': 'tavily_search_results_json',
#  'args': {'query': 'famous places to visit in Bangalore'},
#  'id': 'call_NheTr6jPV4EZPe0g1Xluhdhy',
#  'type': 'tool_call'},
# {'name': 'tavily_search_results_json',
#  'args': {'query': 'must visit restaurants in Bangalore'},
#  'id': 'call_UoOT3m5svSe0vMILWeIx6l75',
#  'type': 'tool_call'}]

events = app2.stream(None, config, stream_mode="values")

user_input = "what is a weather there?"
config = {"configurable": {"thread_id": "1"}}

events = app2.stream(
    {"messages": [("user", user_input)]}, config, stream_mode="values"
)

snapshot = app2.get_state(config)
snapshot.next
# ('tools',)

last_message=snapshot.values["messages"][-1]
last_message.tool_calls
#[{'name': 'tavily_search_results_json',
#  'args': {'query': 'Bangalore weather today'},
#  'id': 'call_0NLdfZAg6hKgq0QpJ0GSNSYM',
#  'type': 'tool_call'}]

events = app2.stream(None, config, stream_mode="values")

app2.get_state(config)


```

*

    <figure><img src="../.gitbook/assets/image (571).png" alt=""><figcaption></figcaption></figure>
