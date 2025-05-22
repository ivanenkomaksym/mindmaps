---
title: Architectures
markmap:
  colorFreezeLevel: 2
---

## Microservices Architecture

- Scalability: individual services can be scaled independently based on their specific load
- Resilience: when one fails, other services can continue to operate
- Technology Diversity: select tech stack
- Faster Development Cycles: smaller teams, faster delivery
- Maintainability: smaller codebases
- Considerations
  - Increased complexity in deployment, monitoring, and inter-service communication
  - Distributed transactions (sagas and 2PC)
	
## Event-Driven Architecture

- Decoupling: Services communicate asynchronously through events
- Responsiveness: Allows for near real-time updates and reactions to changes in the system
- Scalability: Event streams can be processed by multiple consumers in parallel
- Auditability: Events provide a natural audit trail of what happened in the system
- Considerations 
  - Requires robust message brokers
  - Managing event ordering and exactly-once processing can be complex for critical financial events.
  - Debugging can be more challenging due to the asynchronous nature.

## CQRS (Command Query Responsibility Segregation)

- Optimized Data Models: Separates the model for writing data (Commands) from the model for reading data (Queries)
- Scalability: Read and write sides can be scaled independently
- Considerations
  - Increased complexity as you're managing two distinct models
  - Potential for eventual consistency between the write and read models
  
## Database

- NoSQL
  - Schema-on-read (the structure of the data is implicit, and only interpreted when the data is read)
  - They prioritize scalability and availability over strict consistency.
  - Basically Available, Soft state, Eventual consistency
  - Horizontal scalability: well-suited for handling large amounts of data and high levels of traffic
  - Distributed and high availability
  - Types
    - Document-based: MongoDB, CouchDB, Cloudant, DynamoDB
    - Graph-based: Amazon Neptune, Neo4j
    - Key-value-based: Memcached, Redis
    - Column-based: Cassandra, HBase, Big Table
  - When should NoSQL be used:
    - When a huge amount of data needs to be stored and retrieved.
    - The relationship between the data you store is not that important
    - The data changes over time and is not structured.
    - Support of Constraints and Joins is not required at the database level
    - The data is growing continuously and you need to scale the database regularly to handle the data.
- SQL
  - Schema-on-write (schema is explicit and the database ensures all written data conforms to it)
  - They prioritize reliability and strong consistency.
  - Atomicity, Consistency, Isolation, Durability
  - Common use cases:
    - Banking (accurate balances).
    - E-commerce (ensuring inventory integrity).
    - Enterprise systems requiring strict guarantees.

## Database Sharding / Partitioning

- Scalability: Distributes data across multiple database servers
- Performance: Queries can be directed to specific shards
- Considerations
  - Choosing the right sharding key is critical
  - Cross-shard queries can be complex and less performant
  - Operational complexity in managing a sharded database environment

## Transactions

- 2PC Two-Phase Commits: a voting phase and a commit phase
- Sagas
  - Long lived transactions (LLTs): break down these LLTs into a sequence of transactions
  - Orchestration pattern uses an orchestrator (sometimes called a mediator).
    - Advantages
      - Centralized workflow
      - Error handling
      - Recoverability
    - Disadvantages
      - Responsiveness: All communication must go through the mediator
      - Fault tolerance: single point of failure for the workflow, which can be addressed with redundancy but adds more complexity.
      - Scalability: doesn’t scale as well as choreography because it has more coordination points (the orchestrator)
      - Service coupling: higher coupling between it and domain components
  - Choreography pattern: each service participates with the others, similar to dance partners
    - Advantages
      - Responsiveness: has fewer single choke points
      - Scalability: more independent scaling
      - Fault tolerance: The lack of a single orchestrator allows an architect to enhance fault tolerance with the use of multiple instances.
      - Service decoupling: No orchestrator means less coupling.
    - Disadvantages
      - Distributed workflow: No workflow owner makes error management and other boundary conditions more difficult
      - State management: No centralized state holder hinders ongoing state management.
      - Error handling: Error handling becomes more difficult without an orchestrator because the domain services must have more workflow knowledge
      - Recoverability: more difficult without an orchestrator to attempt retries and other remediation efforts.

## Caching (Distributed Caching)

- Performance: Stores frequently accessed data
- Reduced Latency: Delivers data to users much faster
- Considerations 
  - Cache invalidation strategies are crucial to ensure users see up-to-date information 
  - Choosing what to cache and for how long
  - Using distributed caches like Redis or Memcached for scalability and fault tolerance

## Load Balancing

- Distributes incoming traffic across multiple instances of your application servers, database replicas, etc.
- Prevents any single server from being overwhelmed.
- Improves availability by routing traffic away from unhealthy instances.
- Considerations 
  - Session affinity (sticky sessions) might be needed for certain stateful interactions
  - Sophisticated load balancing algorithms that can account for server load, geographic location, etc.

## Fault-Tolerant Systems

- Replication: creating multiple copies of data or services
- Redundancy: having additional components or systems that can take over in case of a failure
- Load Balancing: distribute incoming network traffic across multiple servers
- Failover: automatically switch to a standby system when the primary one fails
- Graceful degradation: ensures that a system continues to operate at reduced functionality
- Monitoring & Alerting: continuosly monitor the system's health and performance