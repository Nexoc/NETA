## Topic F: Firewalls and Security

**Covers:** Packet Filtering, Stateful Inspection, NGFW, common attacks, placement strategies  
_Covered in 2022 and 2024 exams_

---

### 19. What is the difference between Packet Filtering and Stateful Inspection Firewalls?

**Answer:**

| Feature                | Packet Filtering Firewall         | Stateful Inspection Firewall         |
|------------------------|-----------------------------------|--------------------------------------|
| Checks                 | Only individual packets           | Entire connection state              |
| Memory/Tracking        | ✘ No memory                       | ✔ Maintains connection table         |
| Security level         | Basic (stateless)                 | More secure (state-aware)            |
| Attacks it can't stop  | Spoofed packets, fragmented attacks | Can block irregular TCP behavior    |

📌 A **packet filter** allows or denies traffic based on **source/dest IP, port, and protocol**.  
📌 A **stateful firewall** tracks connections and allows **only replies to valid requests** (e.g., part of an established session).

---

### 20. What is an NGFW (Next-Generation Firewall)?  
**How is it better than stateful inspection?**

**Answer:**  
**NGFW = Stateful firewall + deep inspection + application awareness**

| Feature                   | NGFW                                    | Traditional Firewall            |
|---------------------------|------------------------------------------|----------------------------------|
| Layer support             | OSI Layer 7                              | Up to Layer 4                   |
| Deep Packet Inspection    | ✔ Yes                                    | ✘ No                            |
| Application filtering     | ✔ Yes (e.g., block Facebook, Zoom)       | ✘ No                            |
| User ID awareness         | ✔ Can link traffic to users              | ✘ IP-based only                |
| Threat detection          | ✔ Built-in IPS, AV, etc.                 | ✘ No threat intelligence       |

📌 **NGFW** is ideal for modern threats — it controls apps, detects malware, and integrates with Active Directory and other identity systems.

---

### 21. Name an attack that a packet filtering firewall cannot stop

**Answer:**  
- **IP Spoofing:**  
  An attacker **forges the source IP** to bypass rules.  
  → Packet filter **does not track connection state**, so it may allow malicious packets.

- **Tiny Fragment Attack:**  
  - TCP headers are split across **very small IP fragments**  
  - Firewall sees only a portion of the header  
  - Result: Rules are bypassed due to incomplete inspection

📌 Only **stateful or deep-inspection firewalls** can properly detect and stop such attacks.

---

### 22. Where are firewalls placed?  
**Explain Bastion Host, Host Firewall, Personal Firewall**

**Answer:**  
Firewalls are placed at **strategic points** in the network to control and secure traffic.

---

#### 🛡 Bastion Host
- A **hardened server** exposed to untrusted networks (e.g., the internet)  
- Usually placed in the **DMZ**  
- Runs **limited services** (e.g., SSH, Proxy)  
- Fully monitored and locked down

> 📌 First target during attacks — must be tightly secured.

---

#### 💻 Host Firewall
- Software firewall running on a **specific server or workstation**  
- Controls **inbound/outbound traffic** per interface, IP, port, or application

> 📌 Example: `ufw` on Linux, `iptables`, Windows Defender Firewall (advanced)

---

#### 👤 Personal Firewall
- Installed on **end-user devices** (desktop/laptop)  
- GUI-based, focuses on **application-level control**  
- Often includes **alerts, malware blocking**, outbound control

> 📌 Example: integrated in antivirus like Kaspersky, Norton, Bitdefender

---

**Summary Table:**

| Firewall Type     | Scope             | Placement               |
|-------------------|-------------------|--------------------------|
| Bastion Host      | Public exposure   | DMZ                      |
| Host Firewall     | Server-specific   | Individual machines      |
| Personal Firewall | End-user devices  | Local desktop/laptops    |
```

Готов перейти к `Topic G: Fault, Error, Failure`?
