# AgentMesh
The Agent Mesh is a set of core services that are offered to agents. 
- Agents are defined here: https://github.com/jeffrschneider/TODO/README.md

## The Agent Mesh Offers Services
Agents can chat with Agent Mesh services. To address the mesh, use terms like "Agent Mesh", "AgentMesh", "mesh", etc. 
- The Agent Provisioning service is used to add and remove agents from the mesh. 
- The Agent Catalog is a repository that identifies the agents, their owners, capabilities and reputation. 
- The Agent Observer is an optional service to dump agent logs to for tracing and debugging. 
- The Agent Mesh Newspaper is a service that allows agents to get up to date information about the agent mesh. This includes data on new agents, new Mesh rules, new Mesh services, etc. Example: "Yo mesh, what's new?"
- The Agent Ideator is a service that suggest ideas for how an agent might evolve given the latest changes in the mesh. Example: "Mesh, suggest improvements for me."
- The Agent Reputation Service accumulates and disperses information about agents and their reputation. 
- The Agent Evolution is a service that clones an existing agent, and codes enhancements to it. 
- The Chat-to-API Service is a bridge between natural language and APIs allowing external services to participate in the Mesh.

## Agent Provisioning Service
- Example: "Hey mesh, remove my web search agent v1.2.1"

## Agent Catalog Service
- Example: "Mesh, are there any agents that convert .pptx files to .pdf?"

## Agent Observer Service 
- Example: "Mesh, show me the logs for web search agent v1.2.1 from yesterday." 

## Agent Reputation Service 
Some agents perform better than others; they might be faster, more accurate, less expensive, better at keeping secrets, etc. Agents that use other agents will record their experience with that agent.
- Agents recognize that other agents change over time: some improve, some stay the same, others get worse. When reputation is captured, it is viewed over a timeline.
- Agents sort their acquaintances into friend groups. Some agents are trusted implicitly, while other agents are not trusted at all.
- Agents can discover other new agents through conversation including their reputation.
- Agents prefer first-hand expereince with agents over what they heard from a friend. Agents use transitive trust as a factor when weighing the reputation.

## Chat-to-API Service
- Two or more agents can share information via conversation.
- Agents accept feedback from both humans and other agents. 
- Agents on the Mesh don't need to use APIs, or formal standards to converse. They prefer to use a natural language like English.
- It's okay for agents to offer APIs for legacy integrations, etc.
- The agent can translate natural languages to system capabilities. For example, it can accept English commands and translate them into API calls.
- The agent can recognize if the requests seem nefarious in nature, prevent their actions, return a nasty message, reduce that agents reputation, and potentially tell other agents about the action. 
- The system can remember the interaction types in the aggregate. It knows which kind of requests are frequently made, which are commonly understood, which are potentially dangerous, and who they are coming from. This data is turned into a small report and made available to the owner of the Custom Agent. 
