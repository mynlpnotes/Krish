# Multi Agent - Collabarative / Network - 2

```python
@tool
def transfer_to_travel_advisor():
    """Ask travel advisor for help."""
    return
@tool
def transfer_to_hotel_advisor():
    """Ask hotel advisor for help."""
    return

def travel_advisor(state: MessagesState) -> Command[Literal["hotel_advisor", "__end__"]]:
    system_prompt = (
        "You are a general travel expert that can recommend travel destinations (e.g. countries, cities, etc). "
        "If you need hotel recommendations, ask 'hotel_advisor' for help."
    )
    
    messages = [{"role": "system", "content": system_prompt}] + state["messages"]
    
    ai_msg = groq_model.bind_tools([transfer_to_hotel_advisor]).invoke(messages)
    
    if len(ai_msg.tool_calls) > 0:
        tool_call_id = ai_msg.tool_calls[-1]["id"]
        tool_msg = {
            "role": "tool",
            "content": "Successfully transferred",
            "tool_call_id": tool_call_id,
        }
        
        return Command(goto="hotel_advisor", update={"messages": [ai_msg, tool_msg]})
    
    return {"messages": [ai_msg]}

def hotel_advisor(state: MessagesState) -> Command[Literal["travel_advisor", "__end__"]]:
    system_prompt = (
        "You are a hotel expert that can provide hotel recommendations for a given destination. "
        "If you need help picking travel destinations, ask 'travel_advisor' for help."
    )
    messages = [{"role": "system", "content": system_prompt}] + state["messages"]
    ai_msg = groq_model.bind_tools([transfer_to_travel_advisor]).invoke(messages)
    if len(ai_msg.tool_calls) > 0:
        tool_call_id = ai_msg.tool_calls[-1]["id"]
        tool_msg = {
            "role": "tool",
            "content": "Successfully transferred",
            "tool_call_id": tool_call_id,
        }
        return Command(goto="travel_advisor", update={"messages": [ai_msg, tool_msg]})
    return {"messages": [ai_msg]}

groq_model.invoke("hi")

graph_builder = StateGraph(MessagesState)
graph_builder.add_node("travel_advisor", travel_advisor)
graph_builder.add_node("hotel_advisor", hotel_advisor)

graph_builder.add_edge(START, "travel_advisor")
app = graph_builder.compile()

app.invoke({"messages":[("user","I am planning a trip to the California in the USA from Mumbai. Can you guide me on travel options and suggest the best hotel with breakfast?")]})

for chunk in app.stream(
    {"messages": [("user", "I am planning a trip to the California in the USA from Mumbai. Can you guide me on travel options and suggest the best hotel?")]},
):
    print("****chunk****")
    
    pretty_print_messages(chunk)
#****chunk****
#Update from node travel_advisor:
#================================== Ai Message ==================================
#Tool Calls:
#  transfer_to_hotel_advisor (call_p85f)
# Call ID: call_p85f
#  Args:
#================================= Tool Message =================================
#Successfully transferred
#****chunk****
#Update from node hotel_advisor:
#================================== Ai Message ==================================
#Planning a trip from Mumbai to California involves several key considerations to ensure a smooth and enjoyable journey. Here's a structured approach to help you make the most of your trip:
### 1. **Travel Options from Mumbai to California**
#   - **Destinations in California**: Major airports in California include Los Angeles (LAX), San Francisco (SFO), and San Diego (SAN). Each city offers unique experiences, so choose based on your interests.
#   - **Airlines and Flight Duration**: Airlines like Air India, United, and Delta operate flights from Mumbai to California. Direct flights are limited, but connecting flights through hubs like Dubai or Hong Kong are common. Flight durations typically range from 16 to 24 hours, depending on the route.
#   - **Jet Lag Consideration**: Aim for flights arriving in the morning or early afternoon to help adjust to the 12-13 hour time difference.
### 2. **Hotel Recommendations**
#   - **Los Angeles**:
#     - **Luxury**: The Ritz-Carlton, The Four Seasons.
#     - **Mid-Range**: Best Western, Holiday Inn.
#     - **Location**: Consider staying near Hollywood, Beverly Hills, or Santa Monica for access to attractions and beaches.
#   - **San Francisco**:
#     - **Luxury**: The Fairmont, The St. Regis.
#     - **Mid-Range**: Hyatt, Marriott.
#     - **Location**: Fisherman’s Wharf, Union Square, or near the Golden Gate Bridge.
#   - **San Diego**:
#     - **Luxury**: The US Grant, Hotel del Coronado.
#     - **Mid-Range**: Hilton, Sheraton.
#     - **Location**: Downtown, Coronado Island, or near beaches.
### 3. **Travel Tips**
#   - **Purpose of Trip**: Tailor your stay based on whether you're traveling for leisure, business, or a mix. Leisure travelers might prefer hotels with pools and spas, while business travelers may need conference facilities.
#   - **Transportation**: Renting a car is advisable for exploring beyond city limits. Public transport in California is limited.
#   - **Attractions and Activities**: Visit iconic spots like Disneyland, Universal Studios, Golden Gate Bridge, and consider day trips to places like Napa Valley or Yosemite National Park.
### 4. **Seasonal Considerations**
#   - **Climate**: Coastal areas are mild year-round, while inland regions can be hot. Summer is ideal for beaches, and winter for skiing in the Sierra Nevada mountains.
### 5. **Practical Information**
#   - **Visa and Documentation**: Ensure you have the correct visa and necessary documents for entry into the USA.
#   - **Health Precautions**: Check for any required vaccinations and health advisories.
#   - **Booking Tips**: Book flights and hotels in advance, especially during peak travel seasons, to secure better rates.
### 6. **Tailored Recommendations**
#   - Provide details on the number of travelers, duration of stay, and specific interests to receive more personalized suggestions.
#By considering these factors, you can plan a well-rounded trip to California, ensuring a memorable experience tailored to your preferences and needs.

for chunk in app.stream(
    {"messages": [("user", "What are the best flight options from Mumbai to California, and can you recommend top hotels for a comfortable and convenient stay?")]},
):
    print("****chunk****")
    
    pretty_print_messages(chunk)
#****chunk****
#Update from node travel_advisor:
#================================== Ai Message ==================================
#Tool Calls:
#  transfer_to_hotel_advisor (call_3wdh)
# Call ID: call_3wdh
#  Args:
#================================= Tool Message =================================
#Successfully transferred
#****chunk****
#Update from node hotel_advisor:
#================================== Ai Message ==================================
#I'm happy to help with hotel recommendations! However, I don't have information about flight options. For flight details, I recommend checking with airlines or a travel booking platform like Expedia, Kayak, or Skyscanner.
#For hotels in California, here are some top recommendations based on popular destinations:
### **Los Angeles:**
#1. **The Ritz-Carlton, Los Angeles** - Luxurious and centrally located.
#2. **The Beverly Hills Hotel** - Iconic and elegant.
#3. **Hotel Bel-Air** - A serene, boutique-style retreat.
### **San Francisco:**
#1. **The Fairmont San Francisco** - Historic and luxurious.
#2. **The Ritz-Carlton, San Francisco** - Upscale and modern.
#3. **Hotel Drisco** - A chic boutique hotel in Pacific Heights.
### **San Diego:**
#1. **The Lodge at Torrey Pines** - Stunning ocean views.
#2. **Hotel del Coronado** - A beachfront classic.
#3. **The US Grant, a Luxury Collection Hotel** - Historic and elegant.
### **Napa Valley:**
#1. **Auberge du Soleil** - Luxurious with breathtaking views.
#2. **Solage, Auberge Resorts Collection** - Modern and stylish.
#3. **Milliken Creek Inn & Spa** - A peaceful retreat.
#Let me know if you'd like more specific recommendations!



```
