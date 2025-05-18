
## Topic B: DNS and Email Communication

**Covers:** DNS hierarchy, MX records, email agents (UA, MTA), protocols (SMTP, IMAP, POP3)

---

### 8. Who is responsible for a domain in DNS hierarchy? (Root, TLD, Authoritative)

**Answer:**  
The Domain Name System (DNS) has a hierarchical structure, with each level responsible for specific zones:

| Server Type         | Role and Responsibility                               |
|---------------------|--------------------------------------------------------|
| Root Server         | Top of the hierarchy; redirects to TLD servers         |
| TLD Server          | Responsible for top-level domains like .com, .org, .at |
| Authoritative Server| Knows final DNS records (A, MX, CNAME) for a domain    |

**Example:**  
For `mail.fh-campuswien.ac.at`:
- Root → points to `.at` TLD servers  
- TLD `.at` → points to authoritative server for `fh-campuswien.ac.at`  
- Authoritative → returns IP or MX record for `mail.fh-campuswien.ac.at`

---

### 9. From DNS records, determine the mail server name and IP

**Answer:**  
To send email to someone in a domain (e.g., `@example.com`), the sender’s SMTP server looks up the **MX record** via DNS.

**Steps:**
1. DNS query for MX record of `example.com`
2. DNS server replies with `mail.example.com` (priority + hostname)
3. A second DNS query is made for the **A record** of `mail.example.com` to get its IP
4. The IP is then used by the SMTP server to deliver the email

📌 **MX = Mail Exchange**  
🧪 Tools to test:  
```bash
dig example.com MX
nslookup -type=MX example.com
````

---

### 10. Email delivery: Alice → Bob — draw and explain agents and protocols

**Answer:**

**Email path:**

1. Alice composes an email in a **User Agent (UA)** — e.g. Thunderbird, Outlook
2. The message is sent via **SMTP** to her organization's **Mail Transfer Agent (MTA)**
3. That MTA delivers the message to **Bob's MTA** using SMTP again
4. Bob retrieves it using **IMAP** or **POP3** with his **UA**

**Agents involved:**
UA → MTA (SMTP) → MTA → MDA → UA (via IMAP/POP3)


| Agent     | Role                                                |
| --------- | --------------------------------------------------- |
| UA        | User Agent – Email client (Alice, Bob)              |
| MTA       | Mail Transfer Agent – SMTP mail server              |
| MDA       | Mail Delivery Agent – optional: moves mail to inbox |
| SMTP      | Used between UA → MTA and MTA → MTA                 |
| IMAP/POP3 | Used by Bob to read messages from the server        |

**Protocols:**

* SMTP: sending
* POP3: download and delete from server
* IMAP: synchronize and manage mailbox

---

### 11. What protocols and agents are involved in email delivery?

**Answer:**

**Protocols:**

* **SMTP (Simple Mail Transfer Protocol):**
  Used for sending email — from client to server, and between MTAs.
  Ports: 25 (server–server), 587/465 (client–server)

* **IMAP (Internet Message Access Protocol):**
  Used for reading and syncing email on the server.
  Ports: 143 (unencrypted), 993 (SSL)

* **POP3 (Post Office Protocol v3):**
  Downloads email and removes it from the server.
  Ports: 110 (unencrypted), 995 (SSL)

**Agents:**

* **UA (User Agent):** for sending and reading email
* **MTA (Mail Transfer Agent):** for relaying emails (e.g., Postfix, Sendmail)
* **MDA (Mail Delivery Agent):** optional component to deliver to mailboxes

📌 **SMTP is used only to send**, while **IMAP/POP3 are used to receive**.


