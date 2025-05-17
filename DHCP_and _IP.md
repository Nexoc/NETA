
## Topic C: DHCP and IP Configuration

_Covered in 2024 exam_

---

### 12. What is DHCP? Name 4 parameters it can deliver

**Answer:**  
**DHCP (Dynamic Host Configuration Protocol)** is a client-server protocol that automatically assigns IP configuration to devices on a network.

It simplifies network setup by eliminating the need to manually configure IP settings.

---

### 🔁 DHCP Workflow – The 4-step DORA process:

| Step     | Description                                                                |
|----------|----------------------------------------------------------------------------|
| Discover | Client broadcasts: "Is there a DHCP server?" (UDP port 67 → 68)            |
| Offer    | Server replies with: "Here's an IP, subnet, gateway, etc."                 |
| Request  | Client asks to use the offered configuration                               |
| ACK      | Server confirms and assigns the configuration                              |

---

### 📦 Common parameters delivered by DHCP:

1. **IP Address** (e.g., `192.168.1.101`)  
2. **Subnet Mask** (e.g., `255.255.255.0`)  
3. **Default Gateway** (e.g., `192.168.1.1`)  
4. **DNS Servers** (e.g., `8.8.8.8`, `1.1.1.1`)

**Other optional parameters:**
- Lease time (how long the IP is valid)
- Domain name
- NTP server (for time sync)
- Boot server (for PXE booting)

---

### 📌 Technical Notes:

- **DHCP uses UDP:**
  - Client → Server: port `67`
  - Server → Client: port `68`

💡 The protocol works even before the client has an IP address, by using **broadcasts**.
```
