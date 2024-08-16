# System_design

#### Caching

#### Sharding

#### Load balancing

Framework example :
Several frameworks and tools support load balancing, depending on your specific use case, whether it's for web servers, microservices, or cloud environments. Here are some popular options:

### 1. **NGINX**
   - **Type:** Web server, Reverse proxy, Load balancer
   - **Use Case:** HTTP, TCP/UDP load balancing
   - **Features:** Can distribute traffic across multiple servers, supports session persistence, health checks, and SSL termination.

### 3. **AWS Elastic Load Balancing (ELB)**
   - **Type:** Cloud-based load balancer
   - **Use Case:** Auto-scaling applications in AWS
   - **Features:** Supports automatic scaling, integrates with other AWS services, offers Application Load Balancer (ALB) for HTTP/HTTPS traffic and Network Load Balancer (NLB) for TCP traffic.

### 4. **Kubernetes (K8s)**
   - **Type:** Container orchestration platform
   - **Use Case:** Load balancing across containerized applications
   - **Features:** Built-in service load balancing using `Service` objects, supports both internal and external load balancing.

### 5. **Apache HTTP Server with mod_proxy_balancer**
   - **Type:** Web server and reverse proxy
   - **Use Case:** HTTP, HTTPS load balancing
   - **Features:** Can distribute traffic across several backend servers, supports various load balancing algorithms and session stickiness.

These tools and frameworks provide different levels of load balancing capabilities, from simple round-robin strategies to more complex application-aware routing. The choice of tool depends on your infrastructure, specific requirements, and ecosystem (e.g., cloud provider, microservices architecture, etc.).

#### Replication

Replication is a critical feature in databases and distributed systems, ensuring data is copied and maintained across multiple servers or nodes for high availability, fault tolerance, and scalability. Here are some popular frameworks and tools used for replication:

### 1. **MySQL/MariaDB Replication**
   - **Type:** Relational database
   - **Use Case:** Database replication
   - **Features:** MySQL and MariaDB support master-slave and master-master replication. Data is replicated from one primary database server to one or more secondary servers. Replication can be asynchronous or semi-synchronous.

### 2. **PostgreSQL Streaming Replication**
   - **Type:** Relational database
   - **Use Case:** Database replication
   - **Features:** PostgreSQL offers streaming replication, where data changes are sent from the primary server to standby servers in real-time. This supports high availability and failover. PostgreSQL also supports logical replication for selective data replication.

### 3. **MongoDB Replica Sets**
   - **Type:** NoSQL document database
   - **Use Case:** Database replication
   - **Features:** MongoDB uses replica sets for replication. A replica set is a group of MongoDB instances that maintain the same dataset. Replica sets provide automatic failover and data redundancy.

### 4. **Apache Kafka**
   - **Type:** Distributed streaming platform
   - **Use Case:** Data streaming and replication
   - **Features:** Kafka replicates data across multiple brokers in a cluster. It ensures data durability and availability, with configurable replication factors for each topic. It’s widely used for distributed log processing.


### 5. **Hadoop Distributed File System (HDFS)**
   - **Type:** Distributed file system
   - **Use Case:** Data replication in big data environments
   - **Features:** HDFS replicates data blocks across multiple nodes in a Hadoop cluster to ensure data reliability and fault tolerance. The replication factor can be configured for each file.

### 6. **Redis Replication**
   - **Type:** In-memory data store
   - **Use Case:** Data replication for caching
   - **Features:** Redis supports master-slave replication, where data is replicated from a primary server to one or more secondary servers. It’s used for high availability and read scalability.

### 7. **Elasticsearch Cross-Cluster Replication (CCR)**
   - **Type:** Distributed search engine
   - **Use Case:** Data replication across clusters
   - **Features:** Elasticsearch allows you to replicate indices from one cluster to another using Cross-Cluster Replication. This is useful for disaster recovery and data locality.

These frameworks and tools are widely used across various industries, depending on the specific requirements for data replication, consistency, availability, and performance. The choice of framework often depends on the type of data, the scale of the system, and the desired replication strategy.


#### Failover

Failover mechanisms ensure that if a component of the ML pipeline fails, another component can take over without interrupting the workflow.

### **Failover in System Design**

Failover is a critical concept in system design that refers to the process of automatically switching to a standby system or component when the primary system fails. This ensures continuity of service with minimal disruption, maintaining availability and reliability. Failover is essential in high-availability (HA) systems where downtime is unacceptable, such as in financial services, healthcare, and large-scale web services.

**Key Areas in ML Systems Where Failover is Important:**

1. **Model Serving:**
   - When serving machine learning models in production, a failover mechanism ensures that if the primary model server goes down, a backup server can take over and continue serving predictions.

2. **Data Ingestion:**
   - In real-time machine learning systems, data ingestion pipelines must be robust to failures. Failover ensures that if a data source or processing node fails, another node can continue processing incoming data without loss or delay.

3. **Distributed Training:**
   - In distributed training, where multiple nodes or GPUs are used to train a model, failover mechanisms can reassign tasks from a failed node to another, ensuring that training can continue without restarting from scratch.

4. **Data Storage:**
   - Failover in data storage ensures that training data, model parameters, and other critical information remain available even if one storage node fails.

5. **Orchestration:**
   - Machine learning pipelines often rely on orchestration tools to manage tasks like data preprocessing, model training, and deployment. Failover mechanisms in these tools ensure that if one task or service fails, others can take over or the task can be retried automatically.

**Popular Frameworks and Tools for Failover in Machine Learning Systems:**

1. **Kubernetes**
   - **Type:** Container orchestration platform
   - **Failover Features:** Kubernetes manages the failover of containerized applications. If a pod fails, Kubernetes automatically reschedules it on another node. This is particularly useful for ML systems where components like model servers, data processors, or web services are containerized.

2. **Apache Kafka**
   - **Type:** Distributed streaming platform
   - **Failover Features:** Kafka is designed for high availability with built-in failover for brokers. If a broker fails, Kafka automatically redirects the work to other brokers in the cluster, ensuring continuous data streaming. This is crucial for real-time data ingestion in ML systems.

3. **TensorFlow Serving with Kubernetes**
   - **Type:** Model serving system
   - **Failover Features:** TensorFlow Serving can be deployed on Kubernetes to provide high availability and failover for ML models in production. Kubernetes ensures that if one model server fails, another instance can take over seamlessly.

4. **Ray**
   - **Type:** Distributed execution framework
   - **Failover Features:** Ray is designed for distributed computing and provides fault tolerance in distributed machine learning tasks. If a worker node fails during model training or data processing, Ray can reassign the task to another node, preventing job failures.

5. **Apache Hadoop HDFS (Hadoop Distributed File System)**
   - **Type:** Distributed file system
   - **Failover Features:** HDFS is used to store large datasets across multiple nodes. It has built-in failover capabilities, ensuring that if one storage node fails, data can still be accessed from another node. This is important for ensuring data availability during ML training.

6. **Airflow**
   - **Type:** Workflow orchestration tool
   - **Failover Features:** Apache Airflow can be configured to retry tasks upon failure, and it supports distributed execution, which can be leveraged for failover in machine learning pipelines. If a task fails, Airflow can automatically rerun it on another available worker.

7. **Databricks**
   - **Type:** Unified data analytics platform
   - **Failover Features:** Databricks provides built-in high availability for its clusters. It automatically handles failover for Spark jobs and notebooks, ensuring that ML workloads continue running even if some nodes fail.

8. **Amazon SageMaker**
   - **Type:** Managed ML service
   - **Failover Features:** SageMaker provides automatic failover for model endpoints and training jobs. If a model endpoint fails, it automatically redirects traffic to a healthy instance, ensuring continuous availability.

9. **Redis Sentinel**
   - **Type:** In-memory data store
   - **Failover Features:** Redis Sentinel monitors Redis instances and automatically handles failover to a replica if the primary instance fails. This is useful in ML systems that rely on Redis for fast data access or caching.


### **Importance of Failover in ML Systems:**

- **Reliability:** Ensures that machine learning services remain available and reliable, even in the event of component failures.
- **Continuous Operation:** Prevents downtime in critical ML applications, such as real-time predictions or continuous training pipelines.
- **Data Integrity:** Protects against data loss or corruption by ensuring that data processing tasks can continue seamlessly after a failure.
- **User Experience:** Enhances user experience by ensuring that ML-powered features remain accessible and performant, even during infrastructure issues.



#### Scalability

1. Load Balancing:
- Distributes incoming network traffic across multiple servers to ensure that no single server becomes overwhelmed. This helps in maintaining system performance and reliability as the load increases.

2. Partitioning (Sharding):
- Dividing a database or other resources into smaller, more manageable pieces. Each piece (or shard) can be stored on a different server, allowing the system to handle more data and traffic.

3. Caching:
- Storing copies of frequently accessed data in a faster, more accessible location (e.g., in-memory cache) to reduce the load on the main system components.

4. Replication:
- Copying data across multiple servers or locations to ensure availability and reliability. Replication can help balance the load and provide fault tolerance.

5. Elasticity:
- The ability to automatically scale resources up or down based on demand. Elastic systems adjust to workload changes dynamically, ensuring efficient use of resources.

6. Concurrency:
- Managing multiple operations at the same time. A scalable system can handle more concurrent operations as the load increases, ensuring that performance remains consistent.

7. Statelessness:
- Statelessness is a design principle where each request from a client to a server is treated as an independent transaction that is unrelated to any previous request. The server does not store any information about previous requests or client interactions, meaning that every request must contain all the information necessary for the server to understand and process it.

Example of stateless:
- HTTP Protocol: The HTTP protocol is inherently stateless. Each HTTP request is independent, and the server does not retain any information about previous requests. If state is needed, it must be sent by the client with each request (e.g., using cookies or tokens).
- RESTful APIs: REST (Representational State Transfer) is a stateless architecture for designing networked applications. In RESTful APIs, each request from the client to the server must contain all the necessary information, and the server does not maintain session information between requests.
- Microservices: Statelessness is often a key principle in microservices architecture. Each microservice can handle requests independently, which makes it easier to scale and manage the services.

#### Indexing

Indexing is a technique used in system design, particularly in databases and search engines, to improve the speed and efficiency of data retrieval operations. An index is a data structure that stores a small portion of the dataset in a way that makes it quick to search for records, reducing the time required to find data significantly.

How Indexing Works:
1. Data Structure:
- An index is typically implemented using data structures like B-trees, hash tables, or inverted indexes (in search engines). These structures allow for efficient searching, insertion, and deletion operations.
2. Mapping Keys to Values:
- An index maps specific search keys (like a column value in a database table) to the corresponding records or rows. When a query is executed, the system can use the index to quickly locate the relevant data instead of scanning the entire dataset.
3. Reducing Search Space:
- Without an index, a database or search engine might need to perform a full scan of the dataset to find the desired records, which is time-consuming, especially for large datasets. Indexing reduces the search space by organizing data so that relevant records can be found directly.

#### Fault tolerance

Fault tolerance is achieved through a combination of design strategies, technologies, and practices that ensure a system continues to operate correctly even when one or more of its components fail. The solution migh include
- Ensure the compoenent in the system has Replication 
- Error detection : Systems are equipped with tools to detect errors and correct them automatically, such as checksums in data storage or error-correcting codes in communication systems.
- Load balancing : Load balancing distributes the processing load across multiple servers or systems so that if one fails, the others can handle the load without a noticeable impact on performance.
- Using containers: Docker container make sure each micro service work independently,  If one instance fails, others can continue to operate without interruption.
- Checkpoints and Rollbacks : State Checkpoints: Systems can take regular snapshots of their state, allowing them to roll back to a known good state in case of a failure. Futhermore, In databases and financial systems, transactions are designed to be atomic, ensuring that in case of failure, they either complete fully or have no effect, preserving system integrity.
- High-Availability Clusters: Clustered Systems: These systems consist of multiple servers (nodes) that work together to provide continuous service. If one node fails, others in the cluster take over the workload. Geographical Redundancy: Data centers are spread across different geographical locations, so that a failure at one site doesn’t affect the overall system.
- Continuous Monitoring and Management: Continuous monitoring of system performance, health, and errors allows for the early detection and mitigation of issues before they lead to system failure.
- Testing and Validation: Regular Testing: Fault tolerance mechanisms are regularly tested through simulated failures (such as chaos engineering) to ensure that they work as expected in real-world scenarios. Validation: Systems are validated to ensure that they meet the required fault tolerance levels, including meeting SLA (Service Level Agreement) requirements for uptime and performance.


#### Heat beat

The concept of a "heartbeat" in system design, including machine learning (ML) systems, refers to a regular signal or message sent between components of a system to indicate that they are functioning correctly. The heartbeat mechanism is used to monitor the health and status of system components, ensuring they are operational and responsive.

Example in airflow:
1. Scheduler Heartbeat:
- The Airflow scheduler is responsible for triggering tasks and managing the execution of workflows. The scheduler sends heartbeats to the database to indicate that it is alive and functioning. If the scheduler's heartbeat is not detected within a certain period, Airflow assumes that the scheduler is down.

2. Worker Heartbeat:
- Airflow workers (executors) send heartbeats to the scheduler to indicate that they are alive and actively executing tasks. If a worker fails to send a heartbeat, the scheduler will detect this and may take corrective actions, such as reassigning tasks to another worker.

3. Task Heartbeat:
- Each task in Airflow sends a heartbeat to the scheduler while it is running. This helps the scheduler monitor the status of tasks and detect any issues, such as tasks that hang or fail silently.


#### Checksum

A checksum is a simple error-detecting mechanism used to verify the integrity of data. In system design, particularly in machine learning (ML) system design, checksums play a crucial role in ensuring that data, models, and their outputs are accurate and consistent.

Here are some popular frameworks and tools that include checksum mechanisms and are widely used for ensuring data integrity and consistency in machine learning pipelines:

1. Apache Kafka (with Schema Registry)
Use Case: Kafka is a distributed event streaming platform commonly used for real-time data pipelines. It supports checksums for verifying the integrity of data in streams.
Feature: Kafka automatically computes and verifies checksums on each message in its topics to ensure data consistency during transmission. The Schema Registry further helps in validating the format of messages.

2. DVC (Data Version Control)
Use Case: DVC is a version control system specifically designed for managing data and machine learning models.
Feature: DVC uses checksums to track and version data files and models, ensuring that any changes to data or models are easily detected and traced. This helps maintain the consistency and integrity of datasets and model artifacts.

#### API Design

FastAPI allows you to define routes for various HTTP methods, which are crucial in RESTful API design:
- GET: Used to retrieve data from the server.
- POST: Used to send data to the server to create a new resource.
- PUT: Used to update an existing resource entirely.
- DELETE: Used to delete a resource.

These methods map to standard CRUD (Create, Read, Update, Delete) operations in web APIs. FastAPI makes it very straightforward to define these routes, validate inputs, and return responses, all while providing automatic documentation.


#### WebSocket

WebSockets are a communication protocol designed for real-time, bi-directional data transfer between clients (e.g., browsers) and servers. Unlike traditional HTTP requests where communication is initiated by the client, WebSockets allow both the client and server to send messages to each other anytime without needing to open a new connection. This makes WebSockets an excellent choice for use cases requiring real-time updates, such as chat applications, gaming, live streaming, and collaborative platforms. The main features of websocket :

1. Connection Establishment:

WebSocket communication begins with a handshake over HTTP/HTTPS. Once established, the connection is upgraded from HTTP to the WebSocket protocol (ws:// or wss:// for secure connections).
2. Persistent Connection:

Unlike HTTP, which opens and closes connections frequently, WebSockets maintain a persistent connection, reducing latency for ongoing communication.
3. Low Latency:

WebSockets provide lower latency for real-time applications because they eliminate the need for repeated requests and responses.

4. Scalability:

Implementing WebSockets in large-scale systems requires handling multiple open connections concurrently. Solutions often include load balancers and techniques like sharding, horizontal scaling, and using message brokers (e.g., Redis).

5. Backpressure and Flow Control:

In high-throughput scenarios, it’s important to manage the flow of messages and prevent flooding a connection. This involves designing the system to handle network congestion and buffering intelligently.

System Design Considerations
- Load Balancing and Scaling: Using WebSockets at scale requires distributing connections across multiple servers. This involves using load balancers that are WebSocket-aware.
- Message Brokers: To handle high volumes of messages efficiently, message brokers like Redis are used to route messages between clients and servers.
- Fault Tolerance and Reliability: Systems must be designed to handle connection drops and automatic reconnection without losing data.
- Authentication: Secure WebSocket connections often integrate with existing authentication mechanisms (e.g., JWT tokens) to ensure only authorized clients connect.

#### API Gateway

An API gateway accepts API requests from a client, processes them based on defined policies, directs them to the appropriate services, and combines the responses for a simplified user experience. Typically, it handles a request by invoking multiple microservices and aggregating the results. It can also translate between protocols in legacy deployments.

An API Gateway in Kubernetes is a component that manages and routes external traffic into the cluster, acting as a reverse proxy. It handles tasks like authentication, rate limiting, and routing requests to the appropriate microservices. Common API Gateway solutions in Kubernetes include NGINX.

API gateways commonly implement capabilities that include:
- Security policy – Authentication, authorization, access control, and encryption
- Routing policy – Routing, rate limiting, request/response manipulation, circuit breaker, blue-green and canary deployments, A/B testing, load balancing, health checks, and custom error handling
- Observability policy – Real-time and historical metrics, logging, and tracing

For additional app- and API-level security, API gateways can be augmented with web application firewall (WAF) and denial of service (DoS) protection.

Tools :
- NGINX
- Kurbenete API gateway(it's built-in in kubernet)

Reference:

https://www.f5.com/glossary/api-gateway


#### Proxy server

A proxy server is an intermediary server that sits between a client (like a user’s browser) and a backend service (like a machine learning model). In system design, a proxy server is used to control traffic, improve performance, provide additional security, and manage network communication more efficiently.

**Proxy Server in Machine Learning System Design**
In a machine learning system, proxy servers are often used to:

1. Load Balancing: Distribute incoming requests across multiple instances of a model or service.
2. Caching: Cache frequently requested predictions to reduce latency and computational costs.
3. Authentication and Access Control: Enforce security rules before allowing access to the machine learning model.
4. Rate Limiting: Control the number of requests made to the model, preventing overloading or abuse.
5. A/B Testing: Direct a portion of traffic to different model versions for testing.

**Use Case Example: Model Inference with Proxy Server**
Imagine you have a machine learning system that performs real-time predictions for fraud detection. Here’s how a proxy server can be used:
1. Request Handling and Routing:

All prediction requests are first routed through a proxy server.
The proxy server can distribute the requests across multiple model instances based on load, or direct requests to different model versions for A/B testing.
2. Caching:

If certain predictions are repeated often (like checking the same user’s transaction pattern), the proxy server can cache the response, reducing the need to recompute the result.

3. Security and Rate Limiting:

The proxy server can ensure that only authenticated users can access the prediction API and prevent a single user from flooding the system with requests.
**Popular Frameworks for Proxy Servers in ML Systems**

NGINX:

A highly popular web server and reverse proxy. NGINX is commonly used for routing, load balancing, and caching.
Supports advanced features like SSL termination, request filtering, and rate limiting.


#### Boom filter

A Bloom filter is a probabilistic data structure used in system design that allows you to test whether an element is a member of a set. It is very space-efficient but has a trade-off: it may return false positives (indicating an element is in the set when it is not), but it will never return false negatives (indicating an element is not in the set when it actually is). This makes it useful when you want to quickly determine if an element is probably in a set, where occasional false positives are acceptable.

**Use Case Example**
Bloom filters are particularly useful when the data size is large, and memory is limited. Here are some real-world use cases:
- Web Caching: To determine if a URL is in a cache. A Bloom filter can quickly check whether the URL is present in the cache without needing to go to the cache itself, reducing overhead.
- Database Queries: Bloom filters can be used to reduce disk lookups in a database. For instance, when querying if an element exists in a distributed database, a Bloom filter can be used to quickly eliminate non-existent entries, avoiding unnecessary database hits.
- Email Spam Detection: To check if an email sender is blacklisted. Instead of storing all email addresses, a Bloom filter can quickly verify if a sender’s address might be on a blacklist.

**Popular Frameworks & Libraries for Bloom Filters**
- Redis: Redis supports Bloom filters through the redisbloom module, which provides a fast and scalable solution for storing Bloom filters in a distributed system.
- Python Bloom Filter (pybloom): For Python, libraries like pybloom and bloom-filter provide simple and efficient Bloom filter implementations.
- Apache Kafka: Kafka Streams has built-in support for Bloom filters to filter streams of data effectively.

#### REST and RPC
- Use REST when you need a simple, widely accessible API for general-purpose or cross-platform integration, or when the focus is more on resources than actions.
- Use RPC (gRPC, Thrift) when performance, low-latency communication, or internal service communication is critical, especially in real-time ML systems or complex microservice architectures.



#### Idempotency

Idempotency is a key concept in system design, especially in distributed systems, including machine learning (ML) systems. In essence, an operation is considered idempotent if it can be performed multiple times without changing the outcome beyond the initial application. In other words, regardless of how many times you repeat an idempotent operation, the result should be the same.


In ML systems, idempotency is vital in various scenarios such as data processing, model serving, and orchestrating distributed training. Here are some specific areas where idempotency is important:

1. Data Ingestion and Preprocessing Pipelines:

ML systems often process large amounts of data from various sources. If a data preprocessing job or ETL (Extract, Transform, Load) process is retried due to failures, idempotency ensures that the data is not duplicated or corrupted.
Example: A pipeline that processes incoming event logs (e.g., clickstream data) and stores them in a data warehouse. If the ingestion pipeline is retried, idempotent operations ensure that the same events aren’t processed and stored multiple times.

2. Model Training Jobs:

Distributed training systems may face interruptions or require retries. An idempotent training operation ensures that if a job is retried, it picks up where it left off or restarts in a way that produces the same outcome.
Example: Training a model with checkpointing enabled. If a training job fails and is restarted, it can resume from the last checkpoint without redoing the previous steps.

3. Model Serving APIs:

When exposing models via APIs, idempotency is crucial for handling prediction requests. If a request is retried due to network issues, the API should produce the same prediction without causing unintended side effects.
Example: A REST or RPC endpoint serving predictions for a fraud detection model. If the client retries the request due to a timeout, the same response should be returned to prevent double processing of a transaction.

4. Batch Processing and Feature Engineering:

Batch jobs for feature extraction or transformation need to be idempotent to avoid generating duplicate features or incorrect feature sets when jobs are retried.
Example: A batch job that computes derived features like moving averages or aggregations. If the job runs twice, the same feature set should be generated without duplicating values or causing inconsistencies.


**Popular Frameworks and Tools Supporting Idempotency**
Many tools and frameworks facilitate building idempotent operations, especially in the context of ML systems:

- Apache Airflow: Airflow is widely used for orchestrating ML pipelines. It supports idempotency by using task retries, backoff mechanisms, and ensuring that DAG (Directed Acyclic Graph) tasks are re-entrant and produce the same output if retried.

- KubeFlow Pipelines: KubeFlow, designed for orchestrating ML workflows on Kubernetes, supports idempotent pipeline steps and retries. It allows you to implement idempotent steps in complex training, preprocessing, and deployment pipelines.







