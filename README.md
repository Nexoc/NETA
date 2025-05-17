
## Topic A: Network Architectures and OSI/Internet Layers

**Covers:** client-server, P2P, application layer, TCP/UDP, OSI levels, UDP header.

---

### 1. Which statements describe the client-server architecture?

**Answer:**  
Client-server architecture is a communication model where the server provides services or resources, and the client initiates the connection to use them.

**Key characteristics:**
- Server usually has a static IP, constantly listening on a port.
- Clients often use dynamic IPs and initiate connections.
- The server waits for incoming requests, while clients send them.

**Examples of correct/incorrect statements:**
- [x] "The server has a static IP."
- [x] "The client initiates the connection."
- [ ] "The server connects to the client first."
- [ ] "Client and server have equal roles."

---

### 2. Who is the client in Publish/Subscribe (Pub/Sub)?

**Answer:**  
In Pub/Sub architecture:
- The **publisher** sends data (events, messages) to a **broker**.
- The **subscriber** registers interest in specific topics with the broker.
- **Both** publisher and subscriber are clients of the **message broker**.

So in this model, both publisher and subscriber act as clients. The server is the broker (e.g., MQTT server).

---

### 3. Explain the P2P (Peer-to-Peer) architecture: advantages and disadvantages

**Answer:**  
In P2P architecture, all devices (peers) are equal — each can act as both a client and a server.

**Advantages:**
- No central server — higher resilience
- Good scalability — more peers = more resources
- Shared responsibility — peers contribute bandwidth/storage

**Disadvantages:**
- Harder to secure and manage
- Complex NAT traversal (e.g., port forwarding)
- Not ideal for applications requiring central coordination

**Example:** BitTorrent — all users download and upload simultaneously.

---

### 4. Which of these protocols belong to the Application Layer?  
*(HTTP, FTP, IP, UDP, POP3)*

**Answer:**  
Application Layer protocols (OSI Layer 7) directly interact with user applications.

**Application Layer:**
- [x] HTTP – web browsing
- [x] FTP – file transfer
- [x] POP3 – email retrieval

**Not Application Layer:**
- [ ] UDP – Transport Layer (Layer 4)
- [ ] IP – Network Layer (Layer 3)

---

### 5. What is the difference between the transport and network layers?

**Answer:**

| Category   | Transport Layer (L4)                  | Network Layer (L3)                      |
|------------|----------------------------------------|------------------------------------------|
| Purpose    | End-to-end communication between apps | Host-to-host packet delivery             |
| Protocols  | TCP, UDP                              | IP, ICMP, ARP                            |
| Features   | Flow control, error recovery, ports   | Routing, IP addressing, fragmentation    |

**Example:**
- TCP ensures a reliable stream between browser and web server  
- IP delivers packets between devices (e.g., from 192.168.1.10 to 142.250.184.4)

---

### 6. Draw and explain the UDP header (source port, dest port, length, checksum)

**Answer:**

**UDP Header Structure (8 bytes total):**

```

0       7 8      15 16     23 24     31
+--------+--------+--------+--------+
\| Source Port     | Destination Port |
+--------+--------+--------+--------+
\| Length          | Checksum         |
+-----------------+------------------+

```

| Field             | Description                                           |
|------------------|--------------------------------------------------------|
| Source Port       | The sender’s port number                              |
| Destination Port  | The target service’s port (e.g., 53 for DNS)          |
| Length            | Length of UDP header + data in bytes                  |
| Checksum          | Optional integrity check of header and payload        |

UDP is connectionless and does not guarantee delivery — reliability must be handled by the application.

---

### 7. Analyze the UDP header: ports, protocol, layer, RFC, IETF

**Answer:**
- **Source Port:** Port used by sender (e.g., 50674)  
- **Destination Port:** Port used by service (e.g., 53 for DNS)  
- **Protocol:** UDP  
- **OSI Layer:** Layer 4 (Transport Layer)  
- **Defined in:** RFC 768  
- **Maintained by:** IETF (Internet Engineering Task Force)

**Common use cases:** DNS, VoIP, DHCP, online games — where low latency is more important than guaranteed delivery.
```

