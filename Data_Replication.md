# Data Replication

**Replication** refers to the process of sharing data across redundant resources—such as software or hardware components—to enhance **reliability**, **fault-tolerance**, and **accessibility**.

In database management systems (DBMS), replication is commonly implemented using a **primary-replica** model:  
- **Primary server**: Handles all updates.  
- **Replica servers**: Receive and store updates propagated from the primary server.  
- Each replica confirms successful receipt of updates, ensuring consistency and enabling the system to process subsequent updates reliably.
