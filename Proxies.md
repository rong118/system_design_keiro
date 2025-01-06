# Proxies  

## What is a Proxy Server?  
A proxy server is an intermediary software or hardware that bridges the gap between clients and servers. It enables clients to request services—such as web pages, files, or connections—from servers. Essentially, a proxy server (also known as a forward proxy) facilitates resource requests on behalf of clients, effectively anonymizing them from the servers.  

---

## Forward Proxy  
A forward proxy acts on behalf of clients, offering functions like:  
- **Caching**: Storing frequently accessed data to improve response times.  
- **Filtering**: Blocking or modifying specific requests.  
- **Logging**: Recording request details for monitoring.  
- **Transformation**: Adjusting requests by adding/removing headers, encrypting/decrypting, or compressing resources.  

Forward proxies also hide the client's identity from the server by sending requests on their behalf. Beyond anonymity, they optimize system-wide request traffic through techniques like **collapsed forwarding**, which consolidates identical requests from multiple clients into one, reducing redundant resource access.  

---

## Reverse Proxy  
A reverse proxy retrieves resources from one or more servers and delivers them to clients as if they originated from the proxy itself. Unlike a forward proxy, which anonymizes clients, a reverse proxy masks the server's identity.  

### Example:  
- A client requests content from `facebook.com`.  
- Facebook’s reverse proxy retrieves the content from a backend server and sends it back to the client, hiding the origin server.  

Reverse proxies are commonly used for:  
- **Caching**: Improving performance by storing frequently requested resources.  
- **Load Balancing**: Distributing traffic across multiple servers.  
- **Request Routing**: Directing requests to the appropriate servers.  

---

## Summary  
A proxy server acts as an intermediary between clients and servers to manage and optimize traffic.  
- **Forward Proxy**: Hides the client’s identity and is ideal for protecting internal networks.  
- **Reverse Proxy**: Masks the server’s identity and is used to safeguard backend servers.  

Use a forward proxy to protect clients and a reverse proxy to protect servers.  
