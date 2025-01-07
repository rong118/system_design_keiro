# Caching  

## Introduction  
While load balancing helps scale horizontally across servers, **caching** optimizes the resources you already have, often making seemingly unattainable product requirements feasible.  

Caches capitalize on the **locality of reference** principle: data recently requested is likely to be requested again. They exist across all layers of computing, including hardware, operating systems, web browsers, and applications. Acting like short-term memory, caches are faster than the original data source but have limited storage capacity, typically holding the most recently accessed items.  

Caches are often located near the front end of an architecture to quickly return data without burdening downstream systems.  

---

## Application Server Cache  
Placing a cache directly on a request-layer node allows for local storage of response data:  
- If data exists in the cache, it is returned quickly.  
- If not, the node fetches the data from the disk.  

Caches can reside:  
- **In memory** (extremely fast).  
- **On local disks** (faster than network storage).  

### Challenges with Multiple Nodes  
Expanding to multiple nodes can lead to cache misses if requests are distributed randomly across nodes. Solutions include:  
- **Global Cache**: Centralized cache accessible by all nodes.  
- **Distributed Cache**: Shared cache system across multiple nodes.  

---

## Content Delivery Network (CDN)  
A **CDN** is a specialized cache designed for serving large volumes of static media:  
1. A request first checks the CDN for static media.  
2. If available, the CDN serves the content.  
3. If not, the CDN retrieves the file from the back-end server, caches it locally, and delivers it to the user.  

### CDN Best Practices  
For smaller systems without a dedicated CDN, serve static media from a subdomain (e.g., `static.yourservice.com`) using a lightweight HTTP server like **Nginx**. Transitioning to a CDN later can be done by updating DNS records to point to the CDN.  

---

## Cache Invalidation  
To maintain consistency between the cache and the source of truth (e.g., database), caches require invalidation when data changes.  

### Common Invalidation Strategies:  
1. **Write-Through Cache**  
   - Data is written to both the cache and database simultaneously.  
   - Ensures data consistency and reliability.  
   - **Drawback**: Higher latency due to double writes.  

2. **Write-Around Cache**  
   - Data is written directly to the database, bypassing the cache.  
   - Reduces unnecessary writes to the cache.  
   - **Drawback**: Higher latency for recently written data, leading to cache misses.  

3. **Write-Back Cache**  
   - Data is written to the cache first and synced to the database later.  
   - Provides low latency and high throughput for write-intensive applications.  
   - **Drawback**: Risk of data loss if the cache fails before syncing.  

---

## Cache Eviction Policies  
Eviction policies determine which items are removed when the cache reaches its storage limit.  

### Common Policies:  
1. **First In, First Out (FIFO)**  
   - Removes the oldest accessed item first.  

2. **Last In, First Out (LIFO)**  
   - Removes the most recently accessed item first.  

3. **Least Recently Used (LRU)**  
   - Removes items that haven’t been accessed recently.  

4. **Most Recently Used (MRU)**  
   - Removes the most recently accessed items first.  

5. **Least Frequently Used (LFU)**  
   - Removes items accessed the least number of times.  

6. **Random Replacement (RR)**  
   - Randomly removes an item to free up space.  

---

## Conclusion  
Caching is a critical technique for enhancing performance and optimizing resources. It reduces latency, minimizes load on downstream systems, and improves user experience. By understanding and implementing caching strategies effectively, you can build systems that are both scalable and responsive.