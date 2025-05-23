# Multi Agent - Research Analyst

* &#x20;

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
from langchain_community.tools import DuckDuckGoSearchRun
from langchain_groq import ChatGroq

groq_model=ChatGroq(model="deepseek-r1-distill-llama-70b")

search_tool=DuckDuckGoSearchRun()
repl=PythonREPL()

@tool
def python_repl_tool(
    code: Annotated[str, "The python code to execute to generate your chart."],
):
    """Use this to execute python code. If you want to see the output of a value,
    you should print it out with `print(...)`. This is visible to the user."""
    
    try:
        result = repl.run(code)
    except BaseException as e:
        return f"Failed to execute. Error: {repr(e)}"
    
    result_str = f"Successfully executed:\n\`\`\`python\n{code}\n\`\`\`\nStdout: {result}"
    return (
        result_str + "\n\nIf you have completed all tasks, respond with FINAL ANSWER."
    )

def make_system_prompt(instruction:str)->str:
    return  (
        "You are a helpful AI assistant, collaborating with other assistants."
        " Use the provided tools to progress towards answering the question."
        " If you are unable to fully answer, that's OK, another assistant with different tools "
        " will help where you left off. Execute what you can to make progress."
        " If you or any of the other assistants have the final answer or deliverable,"
        " prefix your response with FINAL ANSWER so the team knows to stop."
        f"\n{instruction}"
    )

make_system_prompt(
        "You can only do research. You are working with a chart generator colleague."
    )

def research_node(state:MessagesState)->Command[Literal["chart_generator", END]]:
    
    research_agent = create_react_agent(
    groq_model,
    tools=[search_tool],
    prompt=make_system_prompt(
        "You can only do research. You are working with a chart generator colleague."
    ),
    )
    
    result = research_agent.invoke(state)
    
    goto = get_next_node(result["messages"][-1], "chart_generator")
    
    result["messages"][-1] = HumanMessage(content=result["messages"][-1].content, name="researcher")
    
    return Command(update={"messages": result["messages"]},goto=goto)

def chart_node(state:MessagesState)-> Command[Literal["researcher", END]]:
    
    chart_agent = create_react_agent(
    groq_model,
    [python_repl_tool],
    prompt=make_system_prompt(
        "You can only generate charts. You are working with a researcher colleague."
    ),
    )
    result = chart_agent.invoke(state)
    
    goto = get_next_node(result["messages"][-1], "researcher")
    
    result["messages"][-1] = HumanMessage(content=result["messages"][-1].content, name="chart_generator")
    
    return Command(update={"messages": result["messages"]},goto=goto)

from langgraph.graph import StateGraph, START

workflow = StateGraph(MessagesState)
workflow.add_node("researcher", research_node)
workflow.add_node("chart_generator", chart_node)

workflow.add_edge(START, "researcher")
app = workflow.compile()

app.invoke({"messages": [("user","get the UK's GDP over the past 3 years, then make a line chart of it.Once you make the chart, finish.")],})
#{'messages': [HumanMessage(content="get the UK's GDP over the past 3 years, then make a line chart of it.Once you make the chart, finish.", additional_kwargs={}, response_metadata={}, id='019b6e66-774e-4d95-9e50-09abdfafc0a9'),
#  AIMessage(content='', additional_kwargs={'tool_calls': [{'id': 'call_4Ju8sqNadf8dqLLQq7U6cVgS', 'function': {'arguments': '{\n  "query": "UK\'s GDP over the past 3 years"\n}', 'name': 'duckduckgo_search'}, 'type': 'function'}], 'refusal': None}, response_metadata={'token_usage': {'completion_tokens': 27, 'prompt_tokens': 204, 'total_tokens': 231, 'completion_tokens_details': {'accepted_prediction_tokens': 0, 'audio_tokens': 0, 'reasoning_tokens': 0, 'rejected_prediction_tokens': 0}, 'prompt_tokens_details': {'audio_tokens': 0, 'cached_tokens': 0}}, 'model_name': 'gpt-4-0613', 'system_fingerprint': None, 'id': 'chatcmpl-BDWtCq9rbBkAALKEaeKg73LUjlJEd', 'finish_reason': 'tool_calls', 'logprobs': None}, id='run-b7d63a79-c1a5-4ef8-8c39-181c860bb1be-0', tool_calls=[{'name': 'duckduckgo_search', 'args': {'query': "UK's GDP over the past 3 years"}, 'id': 'call_4Ju8sqNadf8dqLLQq7U6cVgS', 'type': 'tool_call'}], usage_metadata={'input_tokens': 204, 'output_tokens': 27, 'total_tokens': 231, 'input_token_details': {'audio': 0, 'cache_read': 0}, 'output_token_details': {'audio': 0, 'reasoning': 0}}),
#  ToolMessage(content="When this issue is amended in The Blue Book 2017 it will reduce the level of GFCF across the period by around 1.1% per year. The average impact on quarter-on-quarter GFCF growth is negative 0.02% and the average impact on quarter-on-quarter GDP growth is 0.00%. Related time series. ... Gross Domestic Product team gdp@ons.gov.uk Telephone : +44 ... UK ends 2023 in recession Although GDP did grow over the whole of year, the UK finished 2023 in a technical recession due to two quarters of negative growth at the end of the year. In Q3 2023, the ... Interest Rates: Long-Term Government Bond Yields: 10-Year: Main (Including Benchmark) for United Kingdom. Household Debt to GDP for United States. Other Formats. Current U.S. Dollars, Annual, Not Seasonally Adjusted. Related Categories. GDP National Accounts Indicators United Kingdom Countries International Data. The United Kingdom's economy grew by 0.9 percent in 2024, after a growth rate of 0.4 percent in 2023, 4.8 percent in 2022, 8.6 percent in 2021, and a record 10.3 percent fall in 2020. This is an alphabetical list of countries by past and projected gross domestic product (nominal) as ranked by the IMF. Figures are based on official exchange rates, not on the purchasing power parity (PPP) methodology. Values are given in millions of United States dollars (USD) and have not been adjusted for inflation. These figures have been taken from the International Monetary Fund's World ...", name='duckduckgo_search', id='a9a157ed-500a-408e-b4f0-116e0be98e2e', tool_call_id='call_4Ju8sqNadf8dqLLQq7U6cVgS'),
#  HumanMessage(content="Based on my research, the GDP growth rate of the UK over the past three years is as follows: \n\n- In 2024, it was 0.9% \n- In 2023, it was 0.4% \n- In 2022, it was 4.8% \n\nI'm passing this data to my colleague who will generate a line chart representing this information. \n\nNote: Due to my current capabilities, I can only acquire the growth rate of GDP, not the absolute GDP value. The growth rate can still give us a sense of the trend over these three years.", additional_kwargs={}, response_metadata={}, name='researcher', id='413bac9c-37d8-4767-8274-38cc2a08d517'),
#  AIMessage(content='', additional_kwargs={'tool_calls': [{'id': 'call_czXoOgxuoiDtHrBugBTp3NJQ', 'function': {'arguments': '{\n  "code": "import matplotlib.pyplot as plt\\n\\nyears = [\'2022\', \'2023\', \'2024\']\\ngdp_growth_rates = [4.8, 0.4, 0.9]\\n\\nplt.plot(years, gdp_growth_rates, marker=\'o\')\\n\\nplt.title(\'UK GDP Growth Rate Over The Past 3 Years\')\\nplt.xlabel(\'Year\')\\nplt.ylabel(\'GDP Growth Rate (%)\')\\n\\nplt.show()"\n}', 'name': 'python_repl_tool'}, 'type': 'function'}], 'refusal': None}, response_metadata={'token_usage': {'completion_tokens': 115, 'prompt_tokens': 722, 'total_tokens': 837, 'completion_tokens_details': {'accepted_prediction_tokens': 0, 'audio_tokens': 0, 'reasoning_tokens': 0, 'rejected_prediction_tokens': 0}, 'prompt_tokens_details': {'audio_tokens': 0, 'cached_tokens': 0}}, 'model_name': 'gpt-4-0613', 'system_fingerprint': None, 'id': 'chatcmpl-BDWtLs2jN5MCkS1jDb9oul8Nc7yZm', 'finish_reason': 'tool_calls', 'logprobs': None}, id='run-27e979b0-0219-4e2d-93e0-2e85e1aca84f-0', tool_calls=[{'name': 'python_repl_tool', 'args': {'code': "import matplotlib.pyplot as plt\n\nyears = ['2022', '2023', '2024']\ngdp_growth_rates = [4.8, 0.4, 0.9]\n\nplt.plot(years, gdp_growth_rates, marker='o')\n\nplt.title('UK GDP Growth Rate Over The Past 3 Years')\nplt.xlabel('Year')\nplt.ylabel('GDP Growth Rate (%)')\n\nplt.show()"}, 'id': 'call_czXoOgxuoiDtHrBugBTp3NJQ', 'type': 'tool_call'}], usage_metadata={'input_tokens': 722, 'output_tokens': 115, 'total_tokens': 837, 'input_token_details': {'audio': 0, 'cache_read': 0}, 'output_token_details': {'audio': 0, 'reasoning': 0}}),
#  ToolMessage(content="Successfully executed:\n\\`\\`\\`python\nimport matplotlib.pyplot as plt\n\nyears = ['2022', '2023', '2024']\ngdp_growth_rates = [4.8, 0.4, 0.9]\n\nplt.plot(years, gdp_growth_rates, marker='o')\n\nplt.title('UK GDP Growth Rate Over The Past 3 Years')\nplt.xlabel('Year')\nplt.ylabel('GDP Growth Rate (%)')\n\nplt.show()\n\\`\\`\\`\nStdout: \n\nIf you have completed all tasks, respond with FINAL ANSWER.", name='python_repl_tool', id='ab512cad-7847-4c69-b9e8-4f1295f42cc3', tool_call_id='call_czXoOgxuoiDtHrBugBTp3NJQ'),
#  HumanMessage(content="FINAL ANSWER\n\nHere is the line chart representing the UK's GDP growth rate over the past 3 years. \n\n![UK's GDP Growth Rate Over The Past 3 Years](data:image/png;base64,iVBORw0KGg...)[alt text](image_url) \n\nPlease note that the values on the y-axis represent the GDP growth rate in percentage and not the absolute GDP.\n\n- In 2022, the GDP growth rate was 4.8%.\n- In 2023, it dropped to 0.4%.\n- In 2024, it slightly increased to 0.9%.\n\nThe trend shows a significant drop in GDP growth rate from 2022 to 2023, followed by a small recovery in 2024.", additional_kwargs={}, response_metadata={}, name='chart_generator', id='982e5870-112b-4807-9514-5a69d314909c')]}
```

*

    <figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>
