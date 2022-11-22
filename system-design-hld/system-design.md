# Chapter

**1. Scale from zero to million of users**


# 1. Scale from zero to million of users

> A journey of a thousand miles begin with a single step, and building a complex system is no different.


### Single Server Setup

Below is an example of single server setup:

<img width="616" alt="Screenshot 2022-11-21 at 11 58 42 PM" src="https://user-images.githubusercontent.com/84272788/203132332-eaf6761d-a311-465a-a1dd-c17fc51a52f4.png">

The request flow os the above single server setup is as follows:

1. Users (mobile app or web browser) will access the website through domain name such as api.mysite.com.
2. Domain Name System (DNS), a paid service provided by third party, returns Internet Protocol (IP) address to the user device. In this case IP address 15.125.23.214 is returned.
3. Hypertext Transfer Protocol (HTTP) request is sent from user device to the web server.
4. The web server returns HTML page or JSON response for rendering.

**NOTE**: Web server can receive traffic from two sources: mobile application or web application.


### Database

With the growth of user base, one server is not enough and we need multiple servers: one for web/mobile traffic and the other for the database. Separating web tier and data tier allows us to scale them independently.

<img width="673" alt="Screenshot 2022-11-22 at 12 13 13 AM" src="https://user-images.githubusercontent.com/84272788/203134810-010725ef-b733-4517-a266-cde177c665a9.png">

There are two types of databases:

1. Relational Database
  - It's also called relational database management system (RDMS) or SQL databse.
  - Popular RDBMS are MySQL, Oracle database, PostgreSql, etc.
  - Relational DB represent or store data in table and rows.
  - We can perform join operation using SQL across different tables.

2. Non-Relational Database
  - It's also called NoSQL DB
  - Popular ones are CouchDB, Neo4j, Cassandra, HBase, Amazon Dynamo DB, etc.
  - This is grouped into four categories: key-value stores, graph stores, column stores and document stores.
  - Join operation are generally not supported in non-relational DB.

Non-relational databases might be the right choise if:
- the application requires super low latency.
- the data is unstructured abd there's no relational data.
- there's a need to store a massive amount of data.


### Vertical Scaling vs Horizontal Scaling

Vertical scaling, also referred to as "scale up", means the process of adding more power (CPU, memory) to the existing server. Horizontal scaling, also referred to as "scale out" means adding more servers into the resource pool.

When traffic is low, vertical scaling is preferred and simplicity of vertical scaling is its main advantage. But it comes with some serious limitations:

- Vertical scaling has a hardware limit. It's impossible to add unlimited CPU or memory to a single server.
- Vertical scaling does not have failover and redundancy. If one server goes down, the whole website/app goes down with it.

Horizontal scaling is more desirable for large applications due to the limitations of vertical scaling.


### Load Balancer

<img width="616" alt="Screenshot 2022-11-22 at 1 00 01 AM" src="https://user-images.githubusercontent.com/84272788/203142561-5ef4dd28-fc7b-4f38-b244-5db8e631072c.png">


Details are explained below:
- If server 1 goes offline, all the traffic wil be routed to server 2. This prevents the website from going offline.
- If the website traffic grows rapidly, and two servers are not enough to handle the incoming traffic, then we can add more web server to the existing resource pool and the load balancer will start routing traffic to the newly added web server.

A load balancer evenly distributes incoming traffic among web servers that are defined in a load-balanced set. Users connect to the public IP of the load balancer directly. Load balancer will communicate to different web servers using private IP which is completely unreachable by clients anymore. A private IP is an IP address reachable only between servers within the same network.


### Database Replication

> Database replication can be used in many database management systems, usually with a master/slave relationship between the original (master) and the copies (slaves).

<img width="511" alt="Screenshot 2022-11-22 at 1 19 58 AM" src="https://user-images.githubusercontent.com/84272788/203145874-d1078f1e-daae-4d96-9450-2e816503b29c.png">

Advantages of database replication:

- **Better Performance**: In the master-slave model, all write and update operations happens in master nodes; whereas all read operations are distributed across slave nodes. This model improves the performance because it allows more queries to be processed in parallel.
- **Reliability**: If one of the databases is destroyed because of some natural disaster, data is still preserved in other nodes because data is replicated across multiple locations or nodes.
- **high Availibility**: By replicating data across different location, the website remains in operation even if a database is offline as we can access data stored in another database server.

Let's see what really happens if one of the databases goes offline:

- If only one slave database is available and that also goes offline, read operations will be redirected to the master database temporarily. As soon as the issue is found, a new slave database will replace the old one. In case multiple salve databases are available, read operations are redirected to other healthy databases.
- If the master database goes offline a slave database will be promoted to the new master. All the read/update operations will be temporarily executed on the new master database. A new slave database will replace the old one for data replication immediately.
- In production systems, promoting a new master is more complicated as the data in a slace database might not be up to date. The missing data needs to be updated by running data recovery scripts.


Below design shows the system design after adding the load balancer and database replication:

<img width="450" alt="Screenshot 2022-11-22 at 8 38 00 AM" src="https://user-images.githubusercontent.com/84272788/203211657-8c3d490c-e3f7-4063-a66a-5534bef023a5.png">


### Cache

A cache is a temporary storage area that stores the result of most expensive response or frequently accessed data in memory so that subsequent requests are served more quickly. The application performance is greatly affected by calling database repeatedly.

The cache tier is a temporary data store layer, much faster than the database. The benefits of having cache tier include better system performance, ability to reduce database workloads and the ability to scale cache tier independently.

<img width="635" alt="Screenshot 2022-11-22 at 9 20 31 AM" src="https://user-images.githubusercontent.com/84272788/203216962-68011cb5-0975-490f-93df-dbd0c1002188.png">

After receiving a request, a web server first checks if the cache has the available response. If it has, it sends data back to the client. If the cache doesn't have the required response, web server queries the database, stores the response in the cache, and sends it back to the client. This caching strategy is called read-through cache.

**Considerations for using cache**

- **Decide when to use cache**: Consider using cache when data is read frequently and modified infrequently. Cached data is stored in volatile memory, all data in memory is lost if the server is restarted. Thus, important data should be saved in persistent data stored.
- **Expiration policy**: When cache data is expired, it should be removed from the cache memory otherwise it'll take space in cache memory unnecessarily. It's advisable not to make the expiration date too short as this will cause the system to load data from database frequently. Meanwhile, it's advisable not to make the expiration date too long as the data can become stale.
- **Consistancy**: This involves keeping the data store and the cache in sync. Inconsistancy can happen because data-modifying operations on the data store and cache are not in single transaction.
- **Eviction policy**: Once the cache is full, any request to add items to the cache might cause existing items to be removed. This is called cache eviction. Least-recently-used (LRU) is the most popular cache eviction policy. Other evictions policies like Least Frequently Used (LFU) or First In First Out (FIFO) can be adopted to satisfy different use case.

Reference study: [Scaling Memcache at Facebook](https://www.usenix.org/system/files/conference/nsdi13/nsdi13-final170_update.pdf)
