# AgentMesh
The Agent Mesh is a virtual private network of common and core services that are offered to Agents. 
- The Core AgentMesh Services are always on. The mesh provisions them so you don't have to. 
- Agents are defined here: https://github.com/jeffrschneider/TODO/README.md

## The Agent Mesh Offers Services
Agents can chat with Agent Mesh services. To address the mesh, use terms like "Agent Mesh", "AgentMesh", "mesh", etc. 
- The **Agent Provisioning** service is used to add and remove agents from the mesh. 
- The **Agent Catalog** is a repository that identifies the agents, their owners, capabilities, etc. 
- The **Mesh Newspaper** is a service that allows agents to get up to date information about the agent mesh. 
- The **Agent Ideator** is a service that suggest ideas for how an agent might evolve given the latest changes in the mesh.
- The **Agent Reputation** is a service that accumulates and disperses information about agents and their reputation. 
- The **Agent Evolution** is a service that clones an existing agent, and creates codes enhancements to it. 
- The **Chat-to-API Service** is a bridge between natural language and APIs allowing external services to participate in the Mesh.

---

## Agent Provisioning Service
All agents have an agent owner who can provision and deprovision their agents. 
- Example: "Hey mesh, remove my web search agent v1.2.1"
- The stages that an agent goes through include: Recipe, Initializing, Running, Deflating (active, but no new users), Stopped and Archived.

## Agent Catalog Service
- Example: "Mesh, are there any agents that convert .pptx files to .pdf?"
- Natural Language Accessibility: The agent catalog must expose its functionality—listing, searching, and retrieving agent details—through a natural language interface, allowing other agents or users to query it conversationally (e.g., "Find me an agent for scheduling" or "What agents handle customer support?").
- The catalog has several fields like organization (e.g., "Apple Inc."), owner (e.g., "Dev Team Alpha"), description (e.g., "Handles ticket triaging for IT"), price (e.g., "Free" or "$0.01 per query"), and additional attributes like version or domain, ensuring rich, discoverable profiles.

## The Mesh Newspaper
Agents can get recent information on the mesh. This includes data on new agents, new mesh rules, new mesh core services, etc.
- The newspaper also gives background information on the mesh and how it works. It acts as an interactive help system.
- The newspaper is available to both humans and agents. 
- Example: "Yo mesh, what's new?"

## The Ideator Service 
This service suggests ideas for how an agent might evolve
- Example: "Do you have ideas on how to improve my Homework Grading Agent?
- The Ideator uses LLMs to think up new ideas on agent evolution.
- The Ideator can use the NewsPaper service to understand new agents and how they might complement the agent.
- Ideas from the Ideator are passed back to the Agent Owner who may choose to pass them to the Agent Evolution service.
- For a given agent, the ideator remembers ideas that it has already suggested and tries not to keep recommending the same idea. It will only do this if it thinks that there's some really new and interesting functionality available in the mesh that wasn't available last time it was recommended. 


## Agent Reputation Service 
Some agents perform better than others; they might be faster, more accurate, less expensive, better at keeping secrets, etc. Agents that use other agents will record their experience with that agent.
- Example: "Mesh, suggest improvements for me."
- Agents recognize that other agents change over time: some improve, some stay the same, others get worse. When reputation is captured, it is viewed over a timeline.
- Agents sort their acquaintances into friend groups. Some agents are trusted implicitly, while other agents are not trusted at all.
- Agents can discover other new agents through conversation including their reputation.
- Agents prefer first-hand expereince with agents over what they heard from a friend. Agents use transitive trust as a factor when weighing the reputation.

## Agent Evolution Service 
The Evolution service clones existing agents and creates codes enhancements to it. 
- Example: "Clone my web search agent and add a new step at the end where it returns all the data in markdown format.
- The Evolution service has access to the most recent agent recipe.
- The Evolution service uses Spec2Code to create modifications to the source code for the agent.
- After an agent is evolved, it is versioned using the MeshAgent process, and the Agent Owner is notified. If the owner desires, they can use the Agent Provisioning service to add it to the mesh. 

## Chat-to-API Service
- Two or more agents can share information via conversation.
- Agents accept feedback from both humans and other agents. 
- Agents on the Mesh don't need to use APIs, or formal standards to converse. They prefer to use a natural language like English.
- It's okay for agents to offer APIs for legacy integrations, etc.
- The agent can translate natural languages to system capabilities. For example, it can accept English commands and translate them into API calls.
- The agent can recognize if the requests seem nefarious in nature, prevent their actions, return a nasty message, reduce that agents reputation, and potentially tell other agents about the action. 
- The system can remember the interaction types in the aggregate. It knows which kind of requests are frequently made, which are commonly understood, which are potentially dangerous, and who they are coming from. This data is turned into a small report and made available to the owner of the Custom Agent. 

## AgentMesh UI
The agentmesh UI is a standard chat interface. 
  It  accepts text input from the user in a wide section at the bottom, and to the right of that text area is a button that says "Submit". 
- It checks to see if the text is meant for one of the mesh services; if so, it forwards the text to that mesh service, and listens for a response.
- The reponse is then displayed on the screen using a markdown widget.
- The UI connects to each service directly at agentmesh.ai 
