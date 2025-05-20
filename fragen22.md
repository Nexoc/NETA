# NETA  22

---

### 1. Which of the following statements regarding client-server architectures for network applications are true or false? (2 points)

- ✅ Der Server hat eine permanente (statische) IP-Adresse.
- ✅ Der Client initiiert die Verbindung.
- ❌ Der Server initiiert die Verbindung zum Client.
- ❌ Client und Server haben gleichberechtigte Rollen.

---

### 2. Which of the following are application layer protocols (Layer 7)? (1 point)

| Yes | No | Protocol |
| --- | -- | -------- |
| ☑   |    | HTTP     |
|     | ☑  | IP       |
| ☑   |    | FTP      |
|     | ☑  | UDP      |
| ☑   |    | POP3     |

---

### 3. What is the main task of the transport layer compared to the network layer? Name at least two transport layer protocols. (1 point)


- Der Transport Layer ist für die Ende-zu-Ende-Kommunikation zwischen Prozessen zuständig. 
- Er stellt durch Fehlererkennung, Flusskontrolle und ggf. Wiederholung sicher, dass Daten zuverlässig ankommen.
	
- Der Network Layer ist für die Übertragung von Paketen zwischen Hosts verantwortlich und kümmert sich um Routing und IP-Adressierung.
	
- Zwei Transportprotokolle: TCP und UDP


---

### 4. Draw and explain the UDP header. Name and explain all UDP header fields. (2 points)

- 1. Source Port (16 Bit) – Portnummer des Absenders
- 2. Destination Port (16 Bit) – Portnummer des Empfängers
- 3. Length – Länge des gesamten UDP-Headers und der Nutzdaten
- 4. Checksum – zur Fehlererkennung (Integritätsprüfung der Daten)

---

### 5. Given are the following DNS entries for the domain "mycampus.ac.at". 
### You want to write an email to [marie.curie@mycampus.ac.at](mailto:marie.curie@mycampus.ac.at). 
### What are the name and IP address of the responsible mail server? (1 point)

- **Mailserver-Name:** post.mycampus.ac.at
- **IP-Adresse:** 192.168.0.80

---

### 6. The following HTTP message was transmitted. What is the full URL of the requested document? Was the message sent from a server or from a client? Which HTTP method was used? (2 points)

- 1. `www.example.com/index.html`
- 2. Von Client gesendet
- 3. HTTP-Methode: GET

---

### 7. Name and explain three (3) HTTP/1.1 Methods. (3 points)

* **GET:** Ruft Daten vom Server ab. Beispiel: Website anzeigen (Status 200).
* **POST:** Sendet Daten an den Server, z. B. zum Speichern in der Datenbank (Status 201).
* **DELETE:** Löscht Ressourcen auf dem Server (Status 204).

---

### 8. Amanda ([amanda@cannelloni.it](mailto:amanda@cannelloni.it)) sends an email from her email-client to Frederic ([frederic@gyoza.com](mailto:frederic@gyoza.com)). Frederic receives the email with his email client. Which services (agents) and which application layer protocols are used? Draw a sketch of the delivery process. (3 points)

**Agents:**

* MUA (Mail User Agent) – amanda & frederic
* MTA (Mail Transfer Agent)
* MDA (Mail Delivery Agent)

**Protokoll:** SMTP und IMAP/POP3

**Skizze:**
UA (amanda@cannelloni.it) -> durch SMTP -> MTA -> durch SMTP -> MTA -> durch IMAP/POP3 -> UA (frederic@gyoza.com)


---

### 9. Which DNS servers form the DNS hierarchy, and for which domains are these servers responsible? (2 points)

**Root DNS:** zuständig für .com, .de, .ru usw.
**TLD DNS:** zuständig für Top-Level-Domain (z. B. example.at)
**Authoritative DNS:** enthält die konkreten Einträge wie MX, A, AAAA usw.

---

### 10. What is the difference between Static NAT and Dynamic NAT? Describe a use case for both technologies and explain the technologies based on these use cases. (4 points)

- **Static NAT:** 1 private IP = 1 öffentliche IP → sinnvoll für Server
- **Dynamic NAT:** mehrere interne Geräte nutzen dynamisch zugewiesene öffentliche IPs

- **Szenario Static:** Webserver ist öffentlich erreichbar → braucht feste IP
- **Szenario Dynamic:** internes Netzwerk mit mehreren Geräten

---

### 11. What is a DMZ? 
### Which Hosts/Servers/Services would you place in a DMZ? 
### Justify your answer. (3 points)

- **DMZ (Demilitarisierte Zone)** ist ein Netzwerkbereich zwischen dem internen Netzwerk und dem Internet, der als Pufferzone dient.

- **Typische Hosts/Services in der DMZ:**

* 1. Webserver
* 2. Mailserver
* 3. DNS-Server

- **Begründung:**
* Diese Server müssen von außen erreichbar sein, sollen aber bei einem Angriff das interne Netzwerk nicht gefährden. 
* Durch die Platzierung in der DMZ wird verhindert, dass ein kompromittierter öffentlicher Server direkten Zugriff auf interne Systeme erhält.


---

### 12. Explain the terms Fault, Error and Failure using an example from the labs. (3 points)

- **Fault:** Fehler im Code
- **Error:** sichtbarer Fehler, aber unklar ob Ursache Server
- **Failure:** z. B. Server ist komplett offline
- 1

- **Fault:** Falsche IP im DNS-Record eingetragen  
- **Error:** Browser zeigt „Seite nicht erreichbar“  
- **Failure:** Webserver nicht erreichbar / keine Antwort


---

### 13. Describe a problem you (could have) had during the labs. 
### Which structured troubleshooting approach fits well to fix the problem?
### Which not? 
### Justify your answer. (3 points)

- **Problem:** ping auf 8.8.8.8 nicht möglich
- **Geeignet:** Divide and Conquer
- **Nicht geeignet:** Top-Down
- **Begründung:** Schicht 3 war betroffen. schneller Fokus auf Routing/IP


---

### 14. Firewall 
- a. What is the difference between a stateful inspection firewall and a packet filtering firewall?
- b. Describe an attack on a packet filtering firewall, which can be avoided by a stateful inspection firewall. (2 + 2 points)

- a) Stateful erkennt Verbindungsstatus, Packet Filter nur IP/Port
- b) Angriff: IP Spoofing – Paket sieht vertrauenswürdig aus, ist aber gefälscht
