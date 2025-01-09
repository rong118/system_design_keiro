# **Consistent Hashing**

Learn about **Consistent Hashing** and its applications in distributed systems.  

---

## **Background**

In scalable systems, **data partitioning** and **replication** are crucial for improving performance, availability, and reliability:  

- **Data Partitioning**: Distributes data across servers to enhance scalability and performance.  
- **Data Replication**: Creates multiple copies of data on different servers to ensure availability and durability.  

Efficient partitioning and replication strategies define how well a system scales and manages resources. Introduced by **David Karger et al. (1997)**, Consistent Hashing addresses challenges in data partitioning and replication and has become a core strategy in distributed systems.  

---

## **What is Data Partitioning?**

**Data Partitioning** is the process of distributing data across nodes. Two main challenges:  
1. Identifying the node where a specific piece of data resides.  
2. Minimizing data movement when adding or removing nodes.  

### **Traditional Hashing Challenges**
A naive approach uses a hash function (e.g., modulo operation) to map data keys to servers. However, adding or removing servers breaks existing mappings, requiring complete remapping of data—leading to inefficiency.  

---

## **Consistent Hashing to the Rescue**  

**Consistent Hashing** maps data to nodes in a way that minimizes data movement when servers are added or removed.  
- Data is stored in a **ring structure**, with nodes assigned specific ranges.  
- Only a small subset of keys is affected during changes.  

### **How it Works**  
1. Divide the hash ring into predefined ranges.  
2. Assign tokens to each node, defining their range of responsibility.  
3. Use a hash function (e.g., MD5) on the data key to determine its range and the responsible node.  

This ensures efficient data distribution and minimal disruption during node changes.  

---

## **Virtual Nodes (Vnodes)**  

To address inefficiencies in basic Consistent Hashing, **Vnodes** subdivide hash ranges into smaller segments. Each physical node manages multiple Vnodes.  

### **Advantages of Vnodes**  
1. **Load Balancing**: Spreads load evenly across nodes, reducing hotspots.  
2. **Scalability**: Simplifies node addition/removal by redistributing only a small subset of data.  
3. **Fault Tolerance**: Multiple nodes participate in rebuilding failed nodes, reducing pressure on replicas.  
4. **Heterogeneous Clusters**: Distributes more Vnodes to powerful servers and fewer to less capable ones.  

---

## **Data Replication Using Consistent Hashing**  

To achieve high availability and durability:  
- Data is replicated across **N nodes**, where **N** is the replication factor.  
- A **coordinator node** stores the data and replicates it to **N-1** clockwise successors on the ring.  

Replication ensures fault tolerance and high availability, often employing **eventual consistency** to allow asynchronous updates.  

---

## **Consistent Hashing in System Design Interviews**  

Consistent Hashing is integral to systems requiring scalability, high availability, or dynamic resource management:  
- **Scalable storage systems**: Add or remove storage servers dynamically.  
- **Distributed caches**: Adjust cache usage based on traffic load.  
- **Data replication**: Efficiently replicate shards for fault tolerance.  

---

## **Use Cases**  

- **Amazon Dynamo** and **Apache Cassandra**: Use Consistent Hashing for data distribution and replication.  
- Systems requiring:  
  - Scalability during high traffic (e.g., seasonal peaks).  
  - Dynamic cache adjustments.  
  - High availability through efficient replication.  
