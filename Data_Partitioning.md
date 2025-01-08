# Data Partitioning  

## Overview  
**Data partitioning** splits a large database (DB) into smaller, more manageable parts, distributing it across multiple machines to enhance manageability, performance, availability, and load balancing. At scale, horizontal scaling (adding more machines) is often more cost-effective and feasible than vertical scaling (upgrading servers).  

---

## 1. Partitioning Methods  

### a. Horizontal Partitioning (Data Sharding)  
- **Description**: Splits rows across different tables based on a range.  
  - Example: Store locations with ZIP codes `< 10000` in one table and those `> 10000` in another.  
- **Challenges**: Imbalanced partitions if data distribution isn’t uniform (e.g., densely populated cities vs. suburbs).  

### b. Vertical Partitioning  
- **Description**: Divides data by feature, storing related tables on specific servers.  
  - Example: In an Instagram-like app:  
    - User profiles → one DB server.  
    - Friend lists → another.  
    - Photos → a third.  
- **Challenges**: As data grows, individual feature-based DBs may need further partitioning (e.g., handling metadata for billions of photos).  

### c. Directory-Based Partitioning  
- **Description**: Uses a lookup service to manage and abstract partitioning schemes.  
  - **Advantages**: Simplifies tasks like adding servers or changing partitioning schemes without impacting the application.  
  - **Trade-Off**: Increases system complexity and introduces a potential single point of failure (the lookup service).  

---

## 2. Partitioning Criteria  

### a. Key or Hash-Based Partitioning  
- **Description**: Applies a hash function to key attributes to determine the partition.  
  - Example: For 100 DB servers, `ID % 100` determines the server for a record.  
- **Challenges**: Adding servers requires changing the hash function, leading to data redistribution and downtime.  
- **Solution**: Use **consistent hashing** to mitigate this issue.  

### b. List Partitioning  
- **Description**: Assigns each partition a list of values.  
  - Example: Store users from Nordic countries (Iceland, Norway, etc.) in a single partition.  

### c. Round-Robin Partitioning  
- **Description**: Distributes data evenly across partitions.  
  - Example: For `n` partitions, assign the `i-th` record to partition `(i mod n)`.  

### d. Composite Partitioning  
- **Description**: Combines multiple partitioning strategies.  
  - Example: First apply list partitioning, then hash-based partitioning.  
  - **Consistent Hashing**: A hybrid of hash and list partitioning, reducing key-space to a manageable size.  

---

## 3. Common Problems of Data Partitioning  

### a. Joins and Denormalization  
- **Issue**: Cross-partition joins are inefficient due to distributed data.  
- **Solution**: Denormalize the database to enable queries from a single table, though this increases the risk of data inconsistency.  

### b. Referential Integrity  
- **Issue**: Enforcing foreign key constraints across partitions is difficult, as most RDBMS do not support cross-DB constraints.  
- **Solution**: Implement integrity checks in application code or run periodic SQL jobs to clean up dangling references.  

### c. Rebalancing  
- **Issue**: Changes in data distribution or load may require rebalancing, necessitating data migration and potential downtime.  
- **Solution**: Use directory-based partitioning to facilitate rebalancing, though it adds complexity and introduces a potential single point of failure.  

---

## Conclusion  
Data partitioning is a powerful tool for scaling databases, but it introduces complexities such as rebalancing, denormalization, and maintaining referential integrity. By carefully choosing partitioning methods and criteria, and planning for common challenges, systems can achieve better performance and scalability at scale.  
