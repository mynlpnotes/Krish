# Introduction to LangGraph

* Used for building stateful, multi actor application with LLMs
* Agents can also communicate with each other
* Each agent can perform different tasks
* Benefits:
  * Cycle controllability&#x20;
  * Persistence
* It allows to define flows that involve cycles, essential for most agentic architectures, differentiating it from DAG-based solutions.
* Using LangGraph studio we can develop all this workflows using drag and drop
* Using graphDB we can develop graph knowledge

**Why LangGraph?**

* Simplifies the development
  * State management of the agent and agent coordination
    * Agent1: Google search
    * Agent2: Wikipedia search
    * Agent3: VectorDB search
    * Chatbot using all this multi AI agents
    * In such application we have to do statement for all the agents and also agent coordination
  * We need to define workflow, logics without worrying about all this
* Flexibility:
  * Flexibility to define own agents logic and communication protocol
  * This allows highly customized application tailored to use case
* Scalibility:
  * We can build large scale multi agent applications, which can handle large volume of interaction
* Fault tolerance:
  * Handle errors, Reliability
