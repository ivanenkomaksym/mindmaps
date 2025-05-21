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

## Database Sharding / Partitioning

- Scalability: Distributes data across multiple database servers
- Performance: Queries can be directed to specific shards
- Considerations
  - Choosing the right sharding key is critical
  - Cross-shard queries can be complex and less performant
  - Operational complexity in managing a sharded database environment

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