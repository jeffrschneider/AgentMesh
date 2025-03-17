# AgentMesh
The AgentMesh is an ecosystem for Agents. If an agent joins the mesh, it can access a set of common services. 
- The Core AgentMesh Services are always on. The mesh provisions them so you don't have to. 
- Users create their own agents which interact with the AgentMesh.
- Agents have some required features so they can interact with the AgentMesh. They are defined here: [https://github.com/jeffrschneider/TODO/README.md](https://github.com/jeffrschneider/BaseAgent/blob/main/README.md) 

<img width="690" alt="image" src="https://github.com/user-attachments/assets/3d61b240-6482-494e-9760-1725f5b9911f" />


## The AgentMesh Offers Services
Agents can chat with AgentMesh services. To address the mesh, use terms like "Agent Mesh", "AgentMesh", "mesh", etc. 
- The **Agent Provisioning** service is used to add and remove agents from the mesh. 
- The **Agent Catalog** is a repository that identifies the agents, their owners, capabilities, etc. 
- The **Mesh Newspaper** is a service that allows agents to get up to date information about the agent mesh. 
- The **Agent Ideator** is a service that suggest ideas for how an agent might evolve given the latest changes in the mesh.
- The **Agent Reputation** is a service that accumulates and disperses information about agents and their reputation. 
- The **Agent Evolver** is a service that clones an existing agent, and creates codes enhancements to it. 
- The **Chat-to-API Service** is a bridge between natural language and APIs allowing external services to participate in the Mesh.
- The **Agent Front Door** is an app used by humans to manage the AgentMesh. It communicates with the AgentMesh Core Services.

---
## The AgentMesh Front Door
The AgentMesh Front Door is a web app that is used by humans to manage their agents. 
- The UI connects to each service directly at agentmesh.ai/{agent-name}  
- It shows a catalog of the users agents. Here, agents can be registered and deregistered. It also shows the public catalog of agents. 
- Users can see their agents and provision new versions.
- Users can see their agents reputation.
- Users can see ideas that were generated for their agents by the Ideator.
- Users can approve/deny Ideas. Approved ideas are sent to the Evolver which will clone the existing agent, code the new ideas and redeploy. 
- Users can read the Mesh Newspaper.
- Users can add to the Agent Specification as a "universal diff". These changes act as the basis for changing the code for the Agent. 

## Agent Provisioning Service
All agents have an "agent owner" who can provision and deprovision their agents. 
- Example: "Hey mesh, remove my web search agent v1.2.1"
- The stages that an agent goes through include: Recipe, Initializing, Running, Deflating (active, but no new users), Stopped and Archived.

## Agent Catalog Service
- Example: "Mesh, are there any agents that convert .pptx files to .pdf?"
- Natural Language Accessibility: The agent catalog must expose its functionality—listing, searching, and retrieving agent details—through a natural language interface, allowing other agents or users to query it conversationally (e.g., "Find me an agent for scheduling" or "What agents handle customer support?").
- The catalog has several fields like organization (e.g., "Apple Inc."), owner (e.g., "Dev Team Alpha"), description (e.g., "Handles ticket triaging for IT"), price (e.g., "Free" or "$0.01 per query"), and additional attributes like version or domain, ensuring rich, discoverable profiles.
- The full spec for the Catalog Service is here: https://github.com/jeffrschneider/AgentMesh/blob/main/Catalog/spec.md 

## The Mesh Newspaper
Agents can get recent information on the mesh. This includes data on new agents, new mesh rules, new mesh core services, etc.
- The newspaper also gives background information on the mesh and how it works. It acts as an interactive help system.
- The newspaper is available to both humans and agents. 
- Example: "Yo mesh, what's new?"

## The Ideator Service 
This service suggests ideas for how an agent might evolve. It suggests functional changes to the agent much like a product manager. 
- Example: "Do you have ideas on how to improve my Homework Grading Agent?
- The Ideator uses LLMs to think up new ideas on agent evolution.
- The Ideator uses the NewsPaper service to understand new agents and how they might complement the agent. It uses the Competitor service to consider feature parity with other solutions. 
- Ideas from the Ideator are passed back to the Agent Owner who may choose to pass them to the Agent Evolution service.
- For a given agent, the ideator remembers ideas that it has already suggested and tries not to keep recommending the same idea. It will only do this if it thinks that there's some really new and interesting functionality available in the mesh that wasn't available last time it was recommended.
- The full spec for Ideator is here: https://github.com/jeffrschneider/AgentMesh/blob/main/Ideator/spec.md 


## Agent Reputation Service 
Some agents perform better than others; they might be faster, more accurate, less expensive, better at keeping secrets, etc. Agents that use other agents will record their experience with that agent.
-  Example: "Mesh, which web search agents have the best reputation?" 
- The AgentMesh Reputation service gossips about the agents. Agents can ask it about an agent, and it can notifiy an agent about its reputation. 
- The full spec for the Reputation service is here: https://github.com/jeffrschneider/AgentMesh/blob/main/Reputation/spec.md 


## Agent Evolver Service 
The Evolution service clones existing agents and creates codes enhancements to it. 
- Example: "Clone my web search agent and add a new step at the end where it returns all the data in markdown format.
- The Evolution service has access to the most recent agent specification and change log.
- The Evolution service uses creates modifications to the source code for the agent.
- After an agent is evolved, it is versioned using the MeshAgent process, and the Agent Owner is notified. If the owner desires, they can use the Agent Provisioning service to add it to the mesh. 
- The evolver service:
  - scans all of the agent code and identifies files that have changed
  - creates a markdown description
  - records the interfaces it offers to other parties: UI, API, sockets, sync vs async, streams, auth, etc.
  - records source code info including programming language, lines of code, and approximate token count (for LLMs). 
  - records the the key architectural and design choices; the clouds, geo, etc), the key platforms it uses (DBs), specific libraries used, etc.
- The script saves the results to temp files in the same directory, overwriting the previous version. 
- It can communicate none, some or all of its capabilities and structure to another party. These rules are defined in the "Communication Rules" section.


## Chat-to-API Service
- Two or more agents can share information via conversation.
- Agents accept feedback from both humans and other agents. 
- Agents on the Mesh don't need to use APIs, or formal standards to converse. They prefer to use a natural language like English.
- It's okay for agents to offer APIs for legacy integrations, etc.
- The agent can translate natural languages to system capabilities. For example, it can accept English commands and translate them into API calls.
- The agent can recognize if the requests seem nefarious in nature, prevent their actions, return a nasty message, reduce that agents reputation, and potentially tell other agents about the action. 
- The system can remember the interaction types in the aggregate. It knows which kind of requests are frequently made, which are commonly understood, which are potentially dangerous, and who they are coming from. This data is turned into a small report and made available to the owner of the Custom Agent. 

