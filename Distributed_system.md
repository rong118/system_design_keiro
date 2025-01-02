# Distributed System Key Concepts

## Scalability
Scalability is the ability of a system, process, or network to handle increasing demand. A distributed system is considered scalable if it can continuously evolve to support growing workloads without significant performance degradation.

Reasons for scaling include increased data volume or workload, such as a higher number of transactions. A scalable system should manage growth efficiently without losing performance.

Although systems may be designed to be scalable, performance often declines as the system size grows due to management overhead or environmental factors. For instance, network latency may increase as machines become geographically distant. Additionally, some tasks may be inherently non-distributable due to their atomic nature or design flaws, limiting the benefits of distribution. Scalable architectures address these challenges by distributing loads evenly across all participating nodes.

**Horizontal vs. Vertical Scaling**:
- **Horizontal Scaling**: Adding more servers to the resource pool. This method allows dynamic scaling by integrating additional machines and is generally more flexible.
- **Vertical Scaling**: Enhancing the capacity of a single server (e.g., adding CPU, RAM, or storage). This method has a limit based on the server’s maximum capacity and often involves downtime.

Examples:
- Horizontal Scaling: Cassandra and MongoDB, which allow easy addition of machines to accommodate growing needs.
- Vertical Scaling: MySQL, which supports scaling by upgrading to larger machines, though this may require downtime.

## Reliability
Reliability refers to the likelihood of a system performing without failure over a specified period. A distributed system is reliable if it continues delivering services despite the failure of some hardware or software components. Reliability is crucial in distributed systems because failing components can often be replaced by healthy ones, ensuring uninterrupted task completion.

For example, in an e-commerce platform like Amazon, user transactions must not fail even if a server crashes. A reliable system ensures redundancy in both software components and data. If a server managing a shopping cart fails, another server with a replica of the cart can take over.

However, redundancy has associated costs. A reliable system must invest in eliminating single points of failure to achieve resilience.

## Availability
Availability measures the percentage of time a system remains operational and capable of performing its functions within a specific period. It accounts for factors like maintainability, repair time, and spare availability. For instance, an aircraft that operates for extended hours with minimal downtime is considered highly available.

**Reliability vs. Availability**:
- A reliable system is also available.
- An available system may not be reliable, as availability can be maintained by minimizing repair time or ensuring spare parts are readily available.

Example: An online store with 99.99% availability for two years may still be unreliable if it lacks robust security measures. A subsequent series of security incidents could drastically lower availability, causing reputational and financial damage.

## Efficiency
Efficiency in distributed systems is often measured by:
- **Response Time (Latency)**: Delay in obtaining the first result.
- **Throughput (Bandwidth)**: Number of results delivered per time unit.

These metrics depend on factors like:
- Total number of messages exchanged between nodes.
- Size of these messages.
- Complexity of operations (e.g., searching a distributed index).

While simplified analyses of distributed structures often overlook factors like network topology and hardware heterogeneity, precise cost models are difficult to develop. Consequently, rough but robust estimates are typically used.

## Serviceability or Manageability
Serviceability refers to how easily a system can be operated and maintained. Systems with high serviceability are easier and faster to repair, which improves availability.

Key considerations include:
- Ease of diagnosing and resolving problems.
- Simplicity of updates and modifications.
- Routine operations without failures or exceptions.

Early fault detection can significantly reduce downtime. For instance, some enterprise systems can automatically notify service centers when faults occur, eliminating the need for human intervention.