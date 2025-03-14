# AgentMesh
The Agent Mesh is a virtual private network of common and core services that are offered to Agents. 
- The Core AgentMesh Services are always on. The mesh provisions them so you don't have to. 
- Agents are defined here: https://github.com/jeffrschneider/TODO/README.md

## The Agent Mesh Offers Services
Agents can chat with Agent Mesh services. To address the mesh, use terms like "Agent Mesh", "AgentMesh", "mesh", etc. 
- The **Agent Provisioning** service is used to add and remove agents from the mesh. 
- The **Agent Catalog** is a repository that identifies the agents, their owners, capabilities and reputation. 
- The **Mesh Newspaper** is a service that allows agents to get up to date information about the agent mesh. 
- The **Agent Ideator** is a service that suggest ideas for how an agent might evolve given the latest changes in the mesh.
- The **Agent Reputation** is a service that accumulates and disperses information about agents and their reputation. 
- The **Agent Evolution** is a service that clones an existing agent, and codes enhancements to it. 
- The **Chat-to-API Service** is a bridge between natural language and APIs allowing external services to participate in the Mesh.

## Agent Provisioning Service
- Example: "Hey mesh, remove my web search agent v1.2.1"

## Agent Catalog Service
- Example: "Mesh, are there any agents that convert .pptx files to .pdf?"
- Natural Language Accessibility: The agent catalog must expose its functionality—listing, searching, and retrieving agent details—through a natural language interface, allowing other agents or users to query it conversationally (e.g., "Find me an agent for scheduling" or "What agents handle customer support?").
- The catalog has several fields like organization (e.g., "Apple Inc."), owner (e.g., "Dev Team Alpha"), description (e.g., "Handles ticket triaging for IT"), price (e.g., "Free" or "$0.01 per query"), and additional attributes like version or domain, ensuring rich, discoverable profiles.






## The Mesh Newspaper
- Agents can get recent information on the mesh. This includes data on new agents, new Mesh rules, new Mesh services, etc.
- Example: "Yo mesh, what's new?"

## Agent Reputation Service 
Some agents perform better than others; they might be faster, more accurate, less expensive, better at keeping secrets, etc. Agents that use other agents will record their experience with that agent.
- Example: "Mesh, suggest improvements for me."
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
