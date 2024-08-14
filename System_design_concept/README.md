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

4. Replication

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
