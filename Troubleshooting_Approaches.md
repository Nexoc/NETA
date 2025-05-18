## Topic H: Troubleshooting Approaches and Tools

**Covers:** Structured troubleshooting methods, failures in approach, common CLI tools  
_Asked in both 2022 and 2024 exams_

---

### 24. Which troubleshooting approach would you use? Why?

**Answer:**  
Troubleshooting can be done using structured approaches depending on the scenario:

| Approach               | Description                                                        | When to use                               |
|------------------------|---------------------------------------------------------------------|--------------------------------------------|
| **Top-down**           | Start at **application layer** and move downward                   | Browser/email issues                       |
| **Bottom-up**          | Start at **physical/network layer** and move upward                | Interface down, cable, no IP               |
| **Divide-and-conquer** | Start at a middle layer (e.g., IP) and decide direction            | Efficient in mixed-layer issues            |
| **Follow-the-path**    | Trace traffic hop-by-hop                                           | For routed/multi-hop network issues        |
| **Compare-working**    | Compare working vs non-working setups                              | One PC works, another doesn't              |
| **Swap the problem**   | Replace/swaps hardware/software to isolate                         | Bad cables, ports, NICs                    |

> 📌 **Divide-and-conquer** is the most flexible and commonly used method.

---

### 25. Which approach didn't work and why?

**Answer:**  
Unstructured or **intuition-only approaches** often fail.

**Example:**
You assumed it was a DNS issue based on past experience, but the real problem was a **firewall rule blocking port 443**.

> 📌 A structured approach (like top-down or divide-and-conquer) would have caught the issue sooner.

---

### 26. What tools can be used in troubleshooting?

**Answer:**

| Tool               | Use Case                                              |
|--------------------|--------------------------------------------------------|
| `ping`             | Test basic IP reachability and packet loss             |
| `traceroute` / `tracert` | Trace the path packets take to the destination     |
| `netstat` / `ss`   | View open connections and listening ports              |
| `ip a` / `ipconfig`| View local IP settings and interfaces                  |
| `ip route`         | Show routing table                                     |
| `dig` / `nslookup` | Check DNS records and resolution                       |
| `tcpdump` / `wireshark` | Capture and analyze network packets               |

> 📌 Use a **combination** of tools depending on where the issue appears in the OSI model.

---

### Summary Example:

**Issue:** A user cannot open a website.  
**Actions:**
1. `ping` → server reachable ✅  
2. `curl` → connection refused ❌  
3. Check `iptables` → port 443 blocked ❌

> 📌 Applied: **divide-and-conquer + ping + curl + firewall rule check**
```
