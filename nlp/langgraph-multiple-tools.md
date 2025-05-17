# LangGraph - Multiple Tools

* &#x20;We are having 5 tools here
* Instead of manual router, we can use tool\_condition here for toll calling
* It will decide whether tool needs to be called&#x20;

```python
@tool
def multiply(a:int,b:int)->int:
    """multiply a and b"""
    return a*b

@tool
def add(a:int,b:int)->int:
    """adding two numbers a and b"""
    return a+b

@tool
def divide(a:int,b:int)->int:
    """dividing two numbers a and b"""
    return a/b

@tool
def subtract(a:int,b:int)->int:
    """subtracting two numbers a and b """
    return a-b

from langchain_community.tools import DuckDuckGoSearchRun
duckduckgo_search=DuckDuckGoSearchRun()
duckduckgo_search.invoke("who is a current prime minister of USA??")

tools=[multiply, add, divide, subtract, duckduckgo_search]

llm_with_tools=openai_model.bind_tools(tools)

llm_with_tools.invoke("hi").tool_calls
llm_with_tools.invoke("can you add these two number 5 and 40?").tool_calls
# [{'name': 'add',
#  'args': {'a': 5, 'b': 40},
#  'id': 'call_0v1Qi6xpFx9xyOrU7lKTxdAJ',
#  'type': 'tool_call'}]

from langchain_core.messages import HumanMessage, SystemMessage

sys_msg = SystemMessage(content="You are a helpful assistant tasked with using search and performing arithmetic on a set of inputs.")

def assistant(state:MessagesState):
    return {"messages":[llm_with_tools.invoke([sys_msg]+state["messages"])]}

builder=StateGraph(MessagesState)

builder.add_node("assistant",assistant)

builder.add_node("tools",ToolNode(tools))

builder.add_edge(START,"assistant")

from langgraph.prebuilt import tools_condition

builder.add_conditional_edges(
    "assistant",
    tools_condition
)

builder.add_edge("tools","assistant")
react_app=builder.compile()

message=[HumanMessage(content="what is twice of narendra modi's current age?")]

## this below detail is called a agentic flow
# first it will come to assistant
# then it will search narendra modi age
# then it will come to again assistant
# then it wil call the multiply tool for getting twice of age
# then again it will come to assistant 
# then it will generate a final answer

# REACT->> Reasoning+actions

# Thinking, action, observation, thiniking,action, observation---> if everything is going to be full fill
# then generating a final ans

response=react_app.invoke({"messages":message})

for m in response["messages"]:
    m.pretty_print()
#================================ Human Message =================================
#
#what is twice of narendra modi's current age?
#================================== Ai Message ==================================
#Tool Calls:
#  duckduckgo_search (call_No6zjTboZqk3p2UwzO0Lfy5t)
# Call ID: call_No6zjTboZqk3p2UwzO0Lfy5t
#  Args:
#    query: Narendra Modi age 2023
#================================= Tool Message =================================
#Name: duckduckgo_search
#
#Learn about the life and achievements of Narendra Modi, the current Prime Minister of India, who was born on September 17, 1950, in Gujarat. Find out his full name, education, political journey, and constituency. 2023: PM Narendra Modi announced the PM Vishwakarma Yojana to enhance the skilling of craftsmen and artisans in the country. Two key infrastructure projects - India International Convention and ... List of all Prime Ministers of India till 2025: Narendra Modi is the current and 14th Prime Minister of India who assumed office on 10 June 2024. Jawaharlal Nehru is the first and the longest ... Prime Minister Narendra Modi turns 74 today, celebrating another year in a long and impactful public service career. Even on his birthday, Modi is busy with work, launching several welfare schemes, while the Bharatiya Janata Party (BJP) marks the day with their annual 'Seva Parv,' focusing on public welfare initiatives. Born on September 17, 1950, in Mehsana, Gujarat, Modi has served three ... Narendra Modi (born September 17, 1950, Vadnagar, India) is an Indian politician and government official who rose to become a senior leader of the Bharatiya Janata Party (BJP). In 2014 he led his party to victory in elections to the Lok Sabha (lower chamber of the Indian parliament), after which he was sworn in as prime minister of India.Prior to that he had served (2001-14) as chief ...
#================================== Ai Message ==================================
#Tool Calls:
#  multiply (call_5CnHsFEWQgfCaz1MITN7RILb)
# Call ID: call_5CnHsFEWQgfCaz1MITN7RILb
#  Args:
#    a: 74
#    b: 2
#================================= Tool Message =================================
#Name: multiply
#
#148
#================================== Ai Message ==================================
#
#Narendra Modi is currently 74 years old. Twice his age is 148.

messages=[HumanMessage(content="what is current gdp of china and india can you give me difference between them?")]
response=react_app.invoke({"messages":messages})
for m in response["messages"]:
    m.pretty_print()
#================================ Human Message =================================
#what is current gdp of china and india can you give me difference between them?
#================================== Ai Message ==================================
#Tool Calls:
#  duckduckgo_search (call_0ONjcU39PBQslxPd6PCRbmjW)
# Call ID: call_0ONjcU39PBQslxPd6PCRbmjW
#  Args:
#    query: current GDP of China 2023
#  duckduckgo_search (call_bBNSA8mOcuWhxnD9FtYq1bkp)
# Call ID: call_bBNSA8mOcuWhxnD9FtYq1bkp
#  Args:
#    query: current GDP of India 2023
#================================= Tool Message =================================
#Name: duckduckgo_search
#China revised upwards on Thursday the size of its economy by 2.7%, but said the change would have little impact on growth this year, as policymakers pledged more stimulus to spur expansion in 2025. China's gross domestic product (GDP) in 2023 was revised to 129.4 trillion yuan ($17.73 trillion), up 3.37 trillion yuan, or 2.7 percent, from the preliminary figure, data from the National Bureau ... Graph and download economic data for Gross Domestic Product for China (MKTGDPCNA646NWDB) from 1960 to 2023 about China and GDP. China's National Bureau of Statistics (NBS) on Thursday revised the country's GDP to about 129.43 trillion yuan ($17.73 trillion), an increase of around 3.37 trillion yuan from the preliminary ... China's 2023 GDP revision aligns with standard global practice, has no significant impact on 2024 growth rates
#================================= Tool Message =================================
#Name: duckduckgo_search
#Nominal GDP or GDP at Current Prices in Q4 of 2023-24 is estimated at ₹78.28 lakh crore, against ₹71.23 lakh crore in Q4 of 2022-23, showing a growth rate of 9.9%. ... (CGA) and Comptroller and Auditor General of India (CAG) have been used for estimating taxes on products at Current Prices. For compiling taxes on products at constant prices ... The United States upholds its status as the major global economy and richest country, with a GDP of over $30.34 trillion as of 2025, steadfastly preserving its pinnacle position from 1960 to 2025. The growth rate in Real GDP during 2024-25 is estimated at 6.4% as compared to 8.2% in 2023-24. Nominal GDP or GDP at Current Prices is estimated to attain a level of ₹324.11 lakh crore in the year 2024-25, against ₹295.36 lakh crore in 2023-24, showing a growth rate of 9.7%. ... (CGA) and Comptroller and Auditor General of India (CAG) have ... The statistic shows GDP in India from 1987 to 2023, with projections up until 2029. ... Value of PFCE in GDP at current prices India FY 2012-2025; FDI as a share of GDP India 2000-2023; India's Current GDP (FY24): $3.9 trillion India's GDP Growth Rate (FY24): 8.2% Also Read: Unemployment rate in India (2008 to 2023): Current rate, historical trends and more
#================================== Ai Message ==================================
#Tool Calls:
#  subtract (call_lijrfiVIGDZ3cnqNp6EMuOpy)
# Call ID: call_lijrfiVIGDZ3cnqNp6EMuOpy
#  Args:
#    a: 17730000000000
#    b: 3900000000000
#================================= Tool Message =================================
#Name: subtract
#13830000000000
#================================== Ai Message ==================================
#As of 2023, China's GDP is approximately $17.73 trillion, while India's GDP is about $3.9 trillion. The difference in their GDPs is approximately $13.83 trillion, with China's economy being larger than India's by this amount.
#As of 2023, China's GDP is approximately 
#3.9 trillion. The difference in their GDPs is approximately $13.83 trillion, with China's economy being larger than India's by this amount.
```

*

    <figure><img src="../.gitbook/assets/image (569).png" alt=""><figcaption></figcaption></figure>
