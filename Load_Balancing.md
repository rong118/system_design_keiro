# Load Balancing

A **Load Balancer (LB)** is a critical component of distributed systems, ensuring traffic is evenly distributed across a server cluster. This improves the responsiveness and availability of applications, websites, or databases. Load balancers also monitor resource health, directing traffic away from servers that are unavailable, unresponsive, or experiencing elevated error rates.

## How Load Balancers Work

A load balancer operates between the client and backend servers, distributing incoming network and application traffic using various algorithms. By balancing requests across multiple servers, it reduces individual server load, eliminates single points of failure, and enhances overall availability and responsiveness.

### Key Layers for Load Balancers
Load balancing can be applied at different layers of a system to maximize scalability and redundancy:
1. **Between users and web servers**
2. **Between web servers and internal platform layers (e.g., application or cache servers)**
3. **Between internal platform layers and databases**

---

## Benefits of Load Balancing

1. **Enhanced User Experience**: Faster, uninterrupted service by redirecting requests to available resources.
2. **Higher System Availability**: Seamless routing around failed servers ensures minimal downtime.
3. **Reduced Administrative Overhead**: Simplifies handling of incoming requests and reduces wait times.
4. **Predictive Analytics**: Smart LBs identify traffic bottlenecks in advance, offering actionable insights for automation and optimization.
5. **Improved Component Longevity**: Distributes work evenly, preventing stress on individual devices.

---

## Load Balancing Algorithms

Load balancers forward requests only to healthy servers, verified through regular **health checks**. Once verified, they use specific algorithms to distribute traffic:

- **Least Connection Method**: Routes traffic to the server with the fewest active connections.
- **Least Response Time Method**: Sends traffic to the server with the fewest connections and the lowest average response time.
- **Least Bandwidth Method**: Selects the server handling the least traffic (in Mbps).
- **Round Robin Method**: Cycles through servers sequentially, ideal for equally configured servers.
- **Weighted Round Robin Method**: Distributes traffic based on server capacity, with higher-weight servers receiving more connections.
- **IP Hash**: Maps client IP addresses to specific servers using a hash function.

### Health Checks
Load balancers perform regular health checks to ensure backend servers are responsive. If a server fails these checks, it is removed from the pool until it passes again.

---

## Redundant Load Balancers

To avoid a load balancer becoming a single point of failure, redundancy can be implemented by clustering two load balancers. Each LB monitors the other's health, and in case of failure, the secondary LB seamlessly takes over.

---
