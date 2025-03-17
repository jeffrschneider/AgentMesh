# AgentMesh Reputation Service Functional Requirements

## Information About Agents
- Agents self-evaluate their task performance (e.g., "2 errors in 148 runs over 4 hours") and report this to the Reputation Service via the BaseAgent communication capability.
- Calling agents evaluate responding agents they interact with, assessing dimensions like success (did it work?), speed (was it fast?), side effects (any negatives?), and cost (was it worth it?).
- Evaluation reports can originate from the calling agent’s logic or be provided by the agent owner (human) and submitted through the BaseAgent interface.
- Agents can attribute their own failures to downstream agents in self-reports (e.g., "I failed because Agent X was slow"), including this blame in the report payload.

## The Reputation Service 
- The Reputation Service acts as a centralized broker, collecting and distributing reputation data across the AgentMesh network.
- All reputation reports (self-reports and calling-agent reports) are stored in a database, tracking both calling and responding agents’ perspectives.
- Database records include fields: agent ID (caller/respondent), report type (self/other), timestamp, evaluation dimensions (success, speed, side effects, cost), blame attribution (if any), and raw report text.
- The Reputation Service supports queries like "Which web search agents have the best reputation?" returning ranked results based on aggregated data.
- The service gossips proactively, notifying agents about their own reputation (e.g., "Your speed rating dropped to 3.2/5") when thresholds are crossed.
- Agents can request reputation data about specific peers (e.g., "How reliable is Agent Y?") via an outbound API call to the service.
- The Reputation Service listens for inbound reports from agents over the AgentMesh message bus, processing them in real-time.
- Outbound responses to reputation queries are formatted as concise JSON payloads (e.g., { "agent_id": "X", "success_rate": 0.98, "avg_speed_ms": 120 }).
- The service aggregates reputation data over configurable time windows (e.g., last 24 hours, 7 days) to provide current and historical views.
- Reports are validated for completeness (e.g., missing agent ID or evaluation data triggers an error) before storage.
- The service maintains anonymity options, allowing agents to submit reports without revealing their identity if configured by the agent owner.
- Reputation scores are calculated using a weighted formula (e.g., 40% success, 30% speed, 20% side effects, 10% cost), adjustable via configuration.
- The service exposes APIs for external systems to query or submit reputation data, ensuring interoperability with tools like the Ideator.
- Gossip notifications are throttled (e.g., max once per hour per agent) to prevent overwhelming the mesh with updates.
- The Reputation Service logs all inbound reports and outbound responses for auditing and debugging purposes.
- Agents can subscribe to reputation updates about specific peers, receiving push notifications when their reputation changes significantly.

