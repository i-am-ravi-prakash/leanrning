# Contents

1. Scale from zero to million of users


# Scale from zero to million of users

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
