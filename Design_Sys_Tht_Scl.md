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



