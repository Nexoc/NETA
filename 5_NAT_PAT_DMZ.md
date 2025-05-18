## Topic E: NAT, PAT, and DMZ

**Covers:** Static/Dynamic NAT, PAT, use cases, DMZ  
_Asked in the 2022 and 2024 exams_

---

### 16. What is the difference between Static NAT and Dynamic NAT?  
**Where are they used?**

**Answer:**

| Feature             | Static NAT                | Dynamic NAT                          |
|---------------------|---------------------------|---------------------------------------|
| Mapping             | One-to-one                | Many-to-pool                          |
| Address translation | Fixed IP ⇄ Fixed IP       | Internal IP ⇄ Any available public IP |
| Use case            | Servers with public IP    | Clients accessing the internet        |
| Example             | `192.168.0.10 ⇄ 203.0.113.5` | `192.168.0.10 ⇄ random from pool`     |

📌 **Static NAT** is useful for making internal servers reachable from the internet.  
📌 **Dynamic NAT** is typically used for outbound access by clients using a pool of public IPs.

---

### 17. Explain the difference between NAT and PAT. Give a scenario

**Answer:**

**NAT (Network Address Translation):**  
Translates **private IP addresses to public ones** — allows internal devices to access the internet.

**PAT (Port Address Translation):**  
An extension of NAT that also **translates port numbers**, allowing **multiple devices to share one public IP**.

| Feature      | NAT                          | PAT                                |
|--------------|-------------------------------|-------------------------------------|
| IP mapping   | One-to-one or many-to-one     | Many-to-one with unique ports       |
| Port change  | ✘ No                          | ✔ Yes                               |
| Use case     | Basic IP mapping              | Home/office networks with 1 IP      |

**📌 PAT Scenario:**
- 3 devices: `192.168.0.10`, `.11`, `.12`
- All use **one public IP**: `203.0.113.5`
- Translations:
  - `192.168.0.10:5000 → 203.0.113.5:40001`
  - `192.168.0.11:5000 → 203.0.113.5:40002`

The **router keeps a NAT table** to track which internal port maps to which external one.

---

### 18. What is DMZ? What services are placed there and why?

**Answer:**

**DMZ (Demilitarized Zone)** is a **network zone** that separates **externally accessible services** from the **internal network**.

📌 **Purpose:**  
Minimize risk — even if a public-facing server is compromised, attackers **cannot access the internal LAN**.

🧱 **Typical setup:**
- Two firewalls (or two firewall zones):
  - One between **Internet ⇄ DMZ**
  - One between **DMZ ⇄ Internal LAN**

🖥️ **Common services placed in DMZ:**
- Web servers (HTTP/HTTPS)
- Mail servers
- DNS servers
- VPN gateways
- Proxy servers

> 📌 Internal databases and sensitive systems **must NOT be placed in the DMZ**.
```

