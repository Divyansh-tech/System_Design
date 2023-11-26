# Scalability
## 1. Single-Server Design:
Single Server Design (Monolithic Architecture),
A monolithic architecture, or single server design, refers to a web application structure where all components—such as the application server, database, web server, and user interface—are housed on a single server. While it offers simplicity and cost-effectiveness.

It may face challenges in scalability and maintenance as the application grows and it has single point of failure. 

## 2. Vertical Scaling:
Vertical scaling, also known as scaling up or upgrading, involves increasing the capacity of a single server or resource to handle greater loads. In this approach, you enhance the power of an individual machine, typically by adding more CPU, RAM, storage, or other resources. Vertical scaling is akin to making a computer more robust by upgrading its components. While it provides a straightforward way to boost performance. 

 It has limits, and there's a ceiling to how much a single server can be scaled vertically. Additionally, it may involve downtime during the upgrade process and still their is single point of failure.

## 3. Horizontal Scaling:
Horizontal scaling, also known as scaling out, is a method of expanding a system's capacity by adding more machines or servers to the network. Rather than upgrading a single server (vertical scaling), horizontal scaling distributes the workload across multiple machines. As demand grows, additional servers are introduced to collectively handle the increased load.

**Components of Horizontal Scaling:**

### 1. Load Balancer:
A crucial component in horizontal scaling is the load balancer. It evenly distributes incoming requests among the available servers, ensuring efficient utilization of resources and preventing any single server from being overloaded.

### 2. Server Nodes:
These are individual machines added to the system to collectively share the workload. Each server node operates independently, contributing to the overall processing capacity of the system.

### 3. Database Sharding:
In horizontal scaling, databases may be horizontally partitioned or sharded. Each shard contains a subset of the data, and multiple database servers collectively manage the entire dataset.


## Database failover strategies
### 1. Cold Standby:
A backup database server in a powered-off state, with periodic data updates from the primary database. Activation involves starting the server, restoring data, potentially leading to downtime.

Periodic Data Update: Backups maintain a snapshot of the primary database at specific intervals.  
Potential Data Loss: Depending on the backup frequency, there may be data loss.

### 2. Warm Standby:
It replicating data from the primary database. Requires synchronization with the primary database before full activation.

Moderate Activation Time: While faster than cold standby, synchronization steps may introduce some downtime.  
Resource Utilization: Consumes resources even when not processing the entire workload.

### 3. Hot Standby:
Here we actively updating backup data simultaneously with the primary database. It is in real-time synchronization and can be seamlessly activated for near-instant failover.

Resource Intensive: Maintaining a fully active duplicate system consumes significant resources.  
Complexity and Cost: Setting up and maintaining a hot standby system can be complex and may incur higher costs due to real-time synchronization.


## Horizontal scaling of Databases: Sharding
Horizontal scaling with sharding is a technique used to handle large amounts of data and increase database performance. Instead of storing all data on a single server, the database is divided into smaller pieces called shards, and each shard is placed on a separate server. This distribution of data across multiple servers allows the database to handle more users and transactions simultaneously, improving performance and scalability. Sharding enables parallel processing, flexibility in adding or removing servers, and efficient management of large datasets.

>**Example of DBs Like**  
**1. MongoDB**   
https://dba.stackexchange.com/questions/82551/data-distribution-in-mongos-with-shards-or-replica-sets  
**2. Cassandra**  
https://cassandra.apache.org/_/cassandra-basics.html


## Downside of NoSQL Database Sharding:
### 1. Complexity of Querying Across Shards:
Querying data that spans multiple shards can be complex. Performing joins or aggregations across shards may require additional effort and can impact performance.  
Example: In a sharded NoSQL database, if you need to perform a query that involves data from multiple shards, you may need to coordinate the query across the shards, which can introduce complexity.

### 2. Data Consistency Challenges:
Achieving strong consistency across shards in a distributed NoSQL database can be challenging. As data is distributed, ensuring that updates are consistent across all shards in real-time may lead to trade-offs in terms of latency or complexity.  
Example: If a write operation occurs on one shard and a read operation immediately follows on another shard, ensuring that the read reflects the most recent write in a consistent manner can be challenging.

### 3. Shard Key Selection Impact:
The choice of shard key is critical, and selecting an inappropriate shard key can lead to uneven data distribution, known as "hotspots," where certain shards handle a disproportionate amount of the workload.  
Example: If a poorly chosen shard key results in a few shards receiving a significantly higher volume of traffic or data, it can impact the overall performance and scalability of the sharded database.

### 4. Limited Support for Transactions Across Shards:
Some NoSQL databases may have limitations on supporting transactions that involve multiple shards. This limitation can impact the atomicity of operations across distributed data.      
Example: If a transaction involves updates to data on multiple shards, ensuring that either all updates succeed or all fail (atomicity) may be challenging in certain NoSQL databases.

### 5. Operational Overhead:
Managing a sharded environment introduces operational complexities. Tasks such as shard management, rebalancing, and ensuring data consistency require careful planning and monitoring.  
Example: Adding or removing shards dynamically to accommodate changes in data volume or traffic patterns requires coordination and may impact the overall operational workload.





