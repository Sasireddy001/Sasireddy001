# System Design / Behavioral Flash Cards

## System Design - Core Concepts

**Q: What is system design?**  
**A:** System design is the process of defining the architecture, components, modules, interfaces, and data for a system to meet specified requirements.

**Q: What are the key components of system design?**  
**A:** Requirements analysis, architecture design, database design, API design, scalability, reliability, security, and performance.

**Q: What is the difference between functional and non-functional requirements?**  
**A:** Functional requirements specify what the system should do (features). Non-functional requirements specify how the system should perform (scalability, reliability, etc.).

**Q: What is a monolithic architecture?**  
**A:** A monolithic architecture is a single, unified application where all components are tightly coupled and deployed together. Simple to develop but hard to scale.

**Q: What is a microservices architecture?**  
**A:** A microservices architecture is a collection of loosely coupled, independently deployable services that communicate via APIs. Complex but scalable.

## Scalability

**Q: What is scalability?**  
**A:** Scalability is the ability of a system to handle growing amounts of work by adding resources.

**Q: What is the difference between horizontal and vertical scaling?**  
**A:** Horizontal scaling adds more machines (scale out). Vertical scaling adds more power to existing machines (scale up). Horizontal is preferred for distributed systems.

**Q: What is the difference between stateless and stateful systems?**  
**A:** Stateless systems don't store session state between requests, making scaling easier. Stateful systems store state, requiring sticky sessions or state externalization.

**Q: What is load balancing?**  
**A:** Load balancing distributes incoming traffic across multiple servers to improve responsiveness and availability. Common algorithms: round-robin, least connections, IP hash.

**Q: What is the difference between L4 and L7 load balancers?**  
**A:** L4 load balancers operate at the transport layer (TCP/UDP). L7 load balancers operate at the application layer (HTTP) and can route based on content.

## Reliability & Availability

**Q: What is reliability?**  
**A:** Reliability is the ability of a system to function correctly and consistently over time.

**Q: What is availability?**  
**A:** Availability is the proportion of time a system is operational. Measured as uptime percentage (e.g., 99.9% = 8.76 hours downtime/year).

**Q: What is the difference between reliability and availability?**  
**A:** Reliability is about correctness (no errors). Availability is about uptime (system is accessible). A system can be available but unreliable (serving wrong data).

**Q: What is fault tolerance?**  
**A:** Fault tolerance is the ability of a system to continue operating despite component failures. Achieved through redundancy, failover, and graceful degradation.

**Q: What is the difference between failover and failback?**  
**A:** Failover switches to a backup system when the primary fails. Failback switches back to the primary after it recovers.

**Q: What is a single point of failure (SPOF)?**  
**A:** A SPOF is a component whose failure causes the entire system to fail. Systems should be designed to eliminate SPOFs through redundancy.

## Data Storage

**Q: What is the CAP theorem?**  
**A:** CAP theorem states that a distributed system can only guarantee two of Consistency, Availability, and Partition tolerance at a given time.

**Q: What is the difference between SQL and NoSQL databases?**  
**A:** SQL databases are relational, use fixed schemas, and support ACID transactions. NoSQL databases are non-relational, use flexible schemas, and prioritize performance over ACID.

**Q: What are the types of NoSQL databases?**  
**A:** Document (MongoDB), Key-Value (Redis), Column-family (Cassandra), Graph (Neo4j).

**Q: What is the difference between eventual consistency and strong consistency?**  
**A:** Strong consistency ensures all nodes see the same data at the same time. Eventual consistency allows temporary inconsistency but converges over time.

**Q: What is the difference between sharding and replication?**  
**A:** Sharding splits data across multiple nodes for scalability. Replication copies data across multiple nodes for reliability and read scalability.

## Caching

**Q: What is caching?**  
**A:** Caching stores frequently accessed data in a fast storage layer (memory) to reduce latency and load on the primary data source.

**Q: What are common caching strategies?**  
**A:** Cache-aside (lazy loading), write-through, write-back, write-around, and refresh-ahead.

**Q: What is the difference between cache-aside and write-through?**  
**A:** Cache-aside loads data on demand (lazy). Write-through updates cache and primary synchronously on every write.

**Q: What is cache invalidation?**  
**A:** Cache invalidation is the process of removing or updating stale data in the cache when the primary data changes.

**Q: What is the difference between TTL and LRU?**  
**A:** TTL (Time To Live) expires cache entries after a fixed time. LRU (Least Recently Used) evicts the least recently used entries when the cache is full.

## Message Queues

**Q: What is a message queue?**  
**A:** A message queue is a component that enables asynchronous communication between services by storing messages until they are consumed.

**Q: What are the benefits of using message queues?**  
**A:** Decoupling, scalability, reliability, buffering, and asynchronous processing.

**Q: What is the difference between a queue and a topic?**  
**A:** A queue delivers each message to one consumer (point-to-point). A topic delivers each message to all subscribers (publish-subscribe).

**Q: What is the difference between RabbitMQ and Kafka?**  
**A:** RabbitMQ is a traditional message broker with rich routing. Kafka is a distributed streaming platform for high-throughput event streaming.

**Q: What is a dead letter queue (DLQ)?**  
**A:** A DLQ stores messages that failed to be processed, allowing later analysis or reprocessing.

## Distributed Systems

**Q: What is a distributed system?**  
**A:** A distributed system is a collection of independent computers that appear as a single coherent system to users.

**Q: What are the challenges of distributed systems?**  
**A:** Network latency, partial failures, consistency, concurrency, security, and complexity.

**Q: What is eventual consistency?**  
**A:** Eventual consistency is a consistency model where updates propagate asynchronously, and all replicas converge to the same state over time.

**Q: What is the difference between synchronous and asynchronous communication?**  
**A:** Synchronous communication requires the sender to wait for a response. Asynchronous communication does not block the sender.

**Q: What is a distributed transaction?**  
**A:** A distributed transaction is a transaction that spans multiple nodes or databases, requiring coordination to ensure ACID properties.

## API Design

**Q: What is REST?**  
**A:** REST (Representational State Transfer) is an architectural style for designing networked applications using HTTP methods (GET, POST, PUT, DELETE) and resources.

**Q: What are REST principles?**  
**A:** Statelessness, client-server architecture, cacheability, uniform interface, layered system, and code on demand (optional).

**Q: What is the difference between REST and GraphQL?**  
**A:** REST uses multiple endpoints for different resources. GraphQL uses a single endpoint with flexible queries, allowing clients to request exactly what they need.

**Q: What is the difference between POST and PUT?**  
**A:** POST creates a new resource (idempotent? no). PUT updates an existing resource (idempotent). PUT can also create if the resource doesn't exist.

**Q: What is idempotency in APIs?**  
**A:** An idempotent operation produces the same result regardless of how many times it is called. PUT and DELETE should be idempotent; POST is not.

## Microservices

**Q: What are the benefits of microservices?**  
**A:** Independent deployment, scalability, technology diversity, fault isolation, and team autonomy.

**Q: What are the challenges of microservices?**  
**A:** Increased complexity, distributed transactions, network latency, testing, monitoring, and operational overhead.

**Q: What is service discovery?**  
**A:** Service discovery is the process of dynamically finding network locations of service instances. Can be client-side or server-side.

**Q: What is the difference between client-side and server-side service discovery?**  
**A:** Client-side: clients query a registry to find services. Server-side: clients call a load balancer that routes to services.

**Q: What is a service mesh?**  
**A:** A service mesh is a dedicated infrastructure layer for managing service-to-service communication, providing features like load balancing, security, and observability.

## Behavioral Questions

**Q: Tell me about yourself.**  
**A:** Briefly describe your background, key achievements, and why you're interested in the role. Focus on relevant experience and enthusiasm.

**Q: Why do you want to work here?**  
**A:** Research the company's mission, products, and culture. Explain how your skills align and how you can contribute to their goals.

**Q: What is your greatest strength?**  
**A:** Choose a strength relevant to the job and provide an example of how you used it to solve a problem or achieve a result.

**Q: What is your greatest weakness?**  
**A:** Choose a real weakness but explain how you're working to improve it. Avoid clichés like "I work too hard."

**Q: Tell me about a time you failed.**  
**A:** Describe the situation, what went wrong, what you learned, and how you applied the lesson to avoid similar failures.

**Q: Tell me about a time you worked in a team.**  
**A:** Describe the project, your role, how you collaborated, challenges faced, and the outcome. Emphasize communication and teamwork.

**Q: Tell me about a time you had a conflict with a colleague.**  
**A:** Describe the conflict, how you approached it respectfully, how you resolved it, and what you learned about conflict resolution.

**Q: Tell me about a time you had to meet a tight deadline.**  
**A:** Describe the situation, how you prioritized tasks, how you communicated with stakeholders, and how you met the deadline without sacrificing quality.

**Q: Tell me about a time you showed leadership.**  
**A:** Describe a situation where you took initiative, guided others, made decisions, and achieved a positive outcome.

**Q: Tell me about a time you had to learn something quickly.**  
**A:** Describe the challenge, how you approached learning (resources, mentorship), and how you applied the new knowledge.

**Q: Where do you see yourself in 5 years?**  
**A:** Align your answer with the role and company growth. Show ambition but also commitment to the current opportunity.

## STAR Method

**Q: What is the STAR method?**  
**A:** STAR is a framework for answering behavioral questions: Situation (context), Task (what you needed to do), Action (what you did), Result (outcome).

**Q: How do you use STAR in interviews?**  
**A:** Structure your answers using STAR. Be specific, use real examples, quantify results, and focus on your contribution.

**Q: Give an example of a STAR answer.**  
**A:** "Situation: Our data pipeline was failing daily. Task: I needed to fix it. Action: I debugged the issue, found a memory leak, optimized the code, and added monitoring. Result: Pipeline uptime improved from 90% to 99.9%."

**Q: What are common mistakes in STAR answers?**  
**A:** Being too vague, not focusing on your contribution, not quantifying results, or taking too long to get to the point.

**Q: How do you prepare for behavioral questions?**  
**A:** Brainstorm examples from your experience, practice STAR answers, and have 3-4 stories for common themes (leadership, conflict, failure, success).

## System Design Interview Questions

**Q: Design a URL shortener (like bit.ly).**  
**A:** Key components: unique ID generation, database (NoSQL for scalability), cache (Redis), load balancer, analytics. Use base62 encoding for short URLs.

**Q: Design a chat application (like WhatsApp).**  
**A:** Key components: real-time messaging (WebSockets), message queue (Kafka), database (Cassandra for time-series), cache (Redis), push notifications, end-to-end encryption.

**Q: Design a news feed (like Facebook).**  
**A:** Key components: feed generation (ranked timeline), caching (Redis), message queue (Kafka), database (Graph DB for social graph), load testing, personalization.

**Q: Design a file storage service (like Dropbox).**  
**A:** Key components: file upload/download (S3), deduplication, versioning, sync (WebSocket), conflict resolution, encryption at rest and in transit.

**Q: Design a rate limiter.**  
**A:** Use token bucket or leaky bucket algorithm. Store counters in Redis with TTL. Implement distributed rate limiting with consistent hashing.

**Q: Design a distributed cache.**  
**A:** Use consistent hashing for key distribution, replication for reliability, eviction policies (LRU), and write-through or cache-aside strategy.

## Behavioral Interview Tips

**Q: How do you research a company before an interview?**  
**A:** Read their website, blog, recent news, products, and competitors. Understand their tech stack, culture, and challenges.

**Q: How do you ask questions in an interview?**  
**A:** Ask thoughtful questions about the role, team, technology stack, challenges, and growth opportunities. Avoid questions easily answered by Google.

**Q: How do you handle stress in interviews?**  
**A:** Take deep breaths, think before answering, ask for clarification if needed, and remember it's okay to say "I need a moment to think."

**Q: How do you follow up after an interview?**  
**A:** Send a thank-you email within 24 hours, reiterate your interest, and mention something specific from the interview.

**Q: How do you negotiate salary?**  
**A:** Research market rates, know your value, be confident but respectful, and consider the entire package (benefits, equity, growth).

## Common System Design Patterns

**Q: What is the publish-subscribe pattern?**  
**A:** Publishers send messages to a topic. Subscribers receive messages from the topic. Decouples producers and consumers.

**Q: What is the observer pattern?**  
**A:** Objects (observers) subscribe to notifications from a subject. Used in event-driven systems and UI frameworks.

**Q: What is the circuit breaker pattern?**  
**A:** Circuit breaker prevents cascading failures by stopping requests to a failing service after a threshold of failures, with automatic recovery attempts.

**Q: What is the bulkhead pattern?**  
**A:** Bulkhead isolates resources (threads, connections) to prevent one component from consuming all resources and affecting others.

**Q: What is the sidecar pattern?**  
**A:** Sidecar deploys a helper process alongside the main application to provide cross-cutting concerns (logging, monitoring, security).
