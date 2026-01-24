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
- Message Delivery
  - At-most-once
    - The message is sent, and the sender does not wait for an acknowledgement. If there is a network failure, the message is lost.
    - Case: Logging non-critical events or monitoring metrics, 
  - At-least-once
    - The sender waits for an acknowledgement (ACK) from the broker/recipient. If the acknowledgement does not arrive (for example, due to a timeout), the message is sent again.
    - Case: Loyalty points, order status updates. This is the most balanced approach for Highload.
    - Risk: The recipient may receive the message several times if the acknowledgement is lost on the way back.
  - Exactly-once
    - The most complex and expensive guarantee. Requires support from both the broker (e.g. Kafka with transactions) and the consumer (idempotent processing)
    - Case: Financial transactions
    - Risk: Strongly impacts performance and increases latency.
- Duplicates
  - Idempotency Key
    - Consumer checks if RequestID has been processed already from ProcessedMessages tables for example
  - State Machine
    - If incoming status is Paid, while the status was Paid already, we do nothing
  - Upsert (SQL/NoSQL)
    - INSERT ON CONFLICT UPDATE

## CQRS (Command Query Responsibility Segregation)

- Optimized Data Models: Separates the model for writing data (Commands) from the model for reading data (Queries)
- Scalability: Read and write sides can be scaled independently
- Considerations
  - Increased complexity as you're managing two distinct models
  - Potential for eventual consistency between the write and read models

## Event Sourcing

- Instead of storing just the current state of the data, store the full series of actions taken on an object in an append-only store.
- Benefits
  - Makes write operations much faster as there is no read, update, and write required
  - Provide an audit log as a by-product
  - Support temporal queries and achieve time-travel (the domain state at a point in the past)
  - It’s a natural fit for designing loosely coupled components i
- Drawbacks
  - A learning curve associated and a shift in mindset required
  - Rather difficult to handle typical queries
  - it’s more appropriate for the event-based model 
  
## Database

- NoSQL
  - BASE
    - Basically Available: The system guarantees availability of data, even in the face of some failures.
    - Soft state: The system state may change over time, even without inputs (due to eventual consistency).
    - Eventual consistency: Data will eventually reach consistency across nodes, but not necessarily immediately.
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
  - ACID
    - Atomicity: all complete or all fail
    - Consistency: When changes are made to our database, we ensure it is left in a valid, consistent state
    - Isolation: Allows multiple transactions to operate at the same time without interfering
    - Durability: Makes sure that once a transaction has been completed, we are confident the data won’t get lost in the event of some system failure
  - Schema-on-write (schema is explicit and the database ensures all written data conforms to it)
  - They prioritize reliability and strong consistency.
  - Atomicity, Consistency, Isolation, Durability
  - Common use cases:
    - Banking (accurate balances).
    - E-commerce (ensuring inventory integrity).
    - Enterprise systems requiring strict guarantees.
- B-Tree, or Balanced Tree
  - Is a self-balancing tree data structure that maintains sorted data and allows for efficient insertion, deletion, and search operations
  - Each node can contain more than one key and can have more than two children. It is a generalized form of the binary search tree.
  - All leaves are at the same level - this is what makes the tree 'balanced'.
- Types of index 
  - Clustered Index (Primary Key)
    - Determines the physical order of data in a table.
    - Each table can have only one clustered index.
    - When you create a clustered index on a table, the data rows are rearranged in the order of the indexed column(s).
    - records are stored in the leaf nodes.
  - Non Clustered Index (or Secondary Index)
    - Doesn’t change the physical order of data in a table.
    - Table can have multiple non-clustered indexes
    - Stored in a separate data structure that includes a copy of the indexed column(s) along with a pointer to the its address in the storage
  - When adding a new record, database engine
    - Retrieving the relevant index pages
    - Proceeds to restructure the B+ tree to accommodate the new record
    - Once the restructuring is complete, the engine saves the updated pages and writes them back to the storage, ensuring that the B+ tree remains in its optimized state.
  - Indexes types
    - B+ Tree Indexes
      -  is one of the most common index structures
      -  It’s a self-balancing tree structure that allows for efficient data retrieval, insertion, and deletion
   -  Hash Indexes
      -  use a hash function to map keys to locations in the index
      -  very fast for exact-match queries but are less efficient for range queries.
      -  are typically used in memory-based databases or as a secondary index in some databases
   -  Bitmap Indexes
      -  Typically used for low-cardinality columns, which are columns with a relatively small number of distinct values.
      -  Excellent for read-heavy workloads and complex queries, they can be less efficient for write operations.
   -  Sparse Indexes
      -  Stores information about only a subset of the rows in a table, rather than every row

## Database Sharding / Partitioning

- Scalability: Distributes data across multiple database servers
- Performance: Queries can be directed to specific shards
- Considerations
  - Choosing the right sharding key is critical
  - Cross-shard queries can be complex and less performant
  - Operational complexity in managing a sharded database environment

## Transactions

- 2PC Two-Phase Commits: a voting phase and a commit phase. Ensure all nodes in a distributed system either commit or roll back a transaction.
  - Preparation Phase
  - Commit Phase
- Sagas
  - Unlike a two-phase commit, a saga is by design an algorithm that can coordinate multiple changes in state
  - Long lived transactions (LLTs): break down these LLTs into a sequence of transactions pattern uses an orchestrator (sometimes called a mediator).
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
- Cache types
  - In-memory caching
    - Useful for applications that require high-speed access to data, such as web servers and databases
    - Volatile and the data stored in the RAM may be lost if the system is shut down or restarted
  - Distributed caching
    - Storing data across multiple servers or nodes in a network
    - Useful for applications that require high availability and scalability
    - Managing a distributed caching system can be complex, and ensuring consistency across multiple nodes can be challenging
  - Client-side caching
    - Storing data on the client’s device, such as a web browser
    - Useful for web applications that require frequent access to static resources, such as images and JavaScript files
    - Can lead to issues with stale data, as the cached data may not always be up-to-date
- Cache Strategies
  - Cache-Aside
    - When data is requested, the application checks the cache first. If the data is not in the cache, it is retrieved from the database and stored in the cache for future use
  - Write-Through
    - Data is written to both the cache and the database at the same time
    - When data is updated, it is written to the cache and the database simultaneously. This ensures that the cache always contains up-to-date data, but it can slow down write operations.
  - Write-Behind
    - Data is written to the cache first and then to the database at a later time
    - This allows write operations to be faster, but it can lead to data inconsistencies if the cache is not properly managed.
  - Read-Through
    - Cache is used as the primary data source. When data is requested, the cache is checked first. If the data is not in the cache, it is retrieved from the database and stored in the cache for future use.
- Cache Effectiveness
  - Cache hit rate - percentage of requests that are served from the cache instead of the backend data store
  - Cache eviction rate - percentage of cached items that are removed from the cache due to expiration or replacement
  - Cache expiration time - A longer cache expiration time can improve the cache hit rate but increase the risk of stale data. A shorter cache expiration time can reduce the risk of stale data but decrease the cache hit rate.
- Real Life E-commerce website
  - 1. In-memory caching - store frequently accessed product information, such as the price, description, and image of the shoes. This information is stored in the RAM of the web server, which allows for fast access and retrieval.
  - 2. Use a distributed caching system to improve the scalability and availability of the website. They choose a distributed cache that can be accessed by multiple web servers, and configure it to automatically synchronize the data between nodes.
  - 3. Client-side caching - use browser caching to store static resources, such as CSS, JavaScript, and images, on the user’s computer.

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

## BCDR Business Continuity and Disaster Recovery

- Business continuity planning:
  - Risk identification: network issues, hardware failures, human error, region outage
  - Risk classification
  - Risk mitigation: using redundancy, replication, failover, and backups
- Infrastructure risks: network issue, machine reboot, hadrware failure, datacenter outage, region outage
- Security, performance or operational risks: data loss or corruption, software bug, failed deployment, DoS, rouge admin
- Risk classification
  - Common risks are planned and expected: brief network outages, equipment restarts due to patches
  - Uncommon risks are unforeseeable events: natural disaster or major network attack
- Risk mitigation
  - Technology-based risk controls: Redundancy, Data replication, Failover, Backups
  - Human-based risk mitigation
    - Triggering a response playbook
    - Falling back to manual operations
    - Training and cultural changes
- High availability design elements
  - Fault tolerance - continue operating, in some defined capacity, in the event of a failure
  - Redundancy - duplicating instances or data to increase the reliability of the workload
  - Scalability and elasticity - abilities of a system to handle increased load by adding and removing resources (scalability), and to do so quickly as your requirements change (elasticity)
  - Zero-downtime deployment
  - Automated testing
  - Monitoring and alerting
- Disaster recovery
  - Recovery Point Objective (RPO) is the maximum duration of acceptable data loss in the event of a disaster
  - Recovery Time Objective (RTO) is the maximum duration of acceptable downtime in the event of a disaste
  - Disaster recovery plans
    - Failover and failback - provisioning a secondary deployment in another location
    - Backups
    - Automated deployments (IaC)
    - Testing and drills

## Architecture Patterns

- Model—View—Controller(MVC)
  - UI(View) can be "smart" or "passive," often tightly coupled with Controller
  - Many-to-one (one Controller can manage multiple Views)
  - View can interact with Model directly, or through Controller
  - Controller updates View, or View observes Model
- Model—View—Presenter(MVP)
  - UI(View) is passive, exposes an interface for the Presenter to update it
  - One-to-one (one Presenter typically manages one View)
  - Presenter updates View directly
- Model — View — ViewModel (MVVM)
  - UI(View) is passive, binds to ViewModel properties and commands
  - One-to-many (one ViewModel can be used by multiple Views), but ViewModel doesn't know View
  - Automatic via data binding (ViewModel updates reflected in View)
- Circuit Breakers
  - After a certain number of requests to the downstream resource have failed (due either to error or to a time-out), the circuit breaker is blown
  - All further requests that go through that circuit breaker fail fast while the breaker is in its blown (open) state
  - If it gets enough healthy responses it resets the circuit breaker.
- Retries with exponential backoff
  - Retries an operation, with an exponentially increasing wait time, up to a maximum retry count has been reached
  - Cloud resources might intermittently be unavailable for more than a few seconds for any reason
    - Orchestrator might be moving a container to another node in a cluster for load balancing
    - database like SQL Azure, where a database can be moved to another server for load balancing
  
## API Versioning

- Versioning Strategies
  - Additive change
    - Things you can do:
      - Add new optional fields
      - Add new endpoints, and
      - Make features optional with opt-in parameters
    - Things you cannot do:
      - Removing or renaming existing fields
      - Changing data types or error codes
      - Changing how endpoints fundamentally work
  - Explicit versioning
    - New version for a breaking change
    - Maintain multiple versions
- 3 ways of communicating versions:
  - URL: https://api.example.com/v2/stocks
  - Header: Api-Version: 2
  - Query
- Sunset HTTP header in API responses tells when a particular version or endpoint will no longer be available

## Domain-Driven Design
- Bounded Context
  - A specific area within a problem domain where a particular model or language is consistently used.
  - Sets clear boundaries for terms that may have different meanings in different parts of the system.
  - Allows teams to develop models specific to each context, reducing confusion and inconsistency.
Breaks down large, complex domains into smaller, more manageable parts.

## C4 model
- A set of abstractions and diagram types that help you and your team to align on technical decisions quicker. 
  - Level 1 System context diagram. A high-level overview of how your users interact with the internal and external systems to get value.
  - Level 2 Container diagram. A zoomed-in view of one system that shows the running containers inside it.
  - Level 3 Component diagram. A zoomed-in view of one container that shows the components making it up.
  - Level 4 Code diagram. Usually in the form of UML class diagrams that are ideally autogenerated from the actual code. 
  
## Protocols
- MQTT
  - Publish-Subscribe: Devices push data to a "broker."
  - Low overhead: Binary headers. MQTT saves significant money by stripping away the heavy text headers of HTTP.
  - Persistent connection: Stays open for continuous updates. Battery life, the device spends less energy "waking up" the radio to transmit.
  - Bidirectional: Broker can push commands to devices. If you need to send a command to a device (like "Turn off the valve"), MQTT delivers it instantly via an open subscription
  - Quality of Service (QoS): Built-in delivery tiers.
- HTTP
  - Request-Response: Client asks, server answers.
  - Ephemeral: Often opens/closes for each request.
  - High Overhead: Verbose text headers (800+ bytes). If you are uploading an image, a firmware file, or a large log file, the overhead of HTTP headers becomes negligible
  - Unidirectional: Server cannot "push" to device easily.
  - Reliant on TCP/Application logic.