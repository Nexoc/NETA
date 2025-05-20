# NETA

---

### 1. Which of the following are application layer protocols (Layer 7)? (1 point)

| Yes | No | Protocol |
| --- | -- | -------- |
| ☑   |    | HTTP     |
|     | ☑  | IP       |
| ☑   |    | FTP      |
|     | ☑  | UDP      |
| ☑   |    | POP3     |

---

### 2. Explain the P2P architecture for network applications. 
### What are the advantages and disadvantages of this architecture? (3 points)

**P2P-Architektur:**

* Jeder Peer ist gleichberechtigt: kann Daten senden und empfangen
* Kein zentraler Server notwendig
* Jeder Teilnehmer ist sowohl Client als auch Server

**Vorteile:**

* Gute Skalierbarkeit
* Höhere Ausfallsicherheit (kein Single Point of Failure)
* Ressourcen werden geteilt (z. B. Bandbreite, Speicher)

**Nachteile:**

* Schwieriger zu verwalten und zu sichern
* Komplizierte NAT-/Firewall-Durchdringung
* Nicht geeignet für zentrale Kontrolle oder Konsistenz

Beispiel: BitTorrent

---

### 3. In the following an internet standard protocol header is defined. 
### What protocol does this header belong to? What network layer does this protocol belong to? 
### In what kind of documents are such standards defined? 
### Which organization publishes these standards? (2 points)

**Protokoll:** UDP (User Datagram Protocol)
**Netzwerkschicht:** OSI-Schicht 4 (Transportschicht)
**Dokumententyp:** RFC (Request for Comments)
**Organisation:** IETF (Internet Engineering Task Force)

---

### 4. What is a DHCP protocol? 
### Name 4 parameters that can be configured via DHCP. (3 Points)

DHCP (Dynamic Host Configuration Protocol) ist ein Protokoll, das IP-Adressen und andere Netzwerkinformationen automatisch an Geräte im Netzwerk vergibt.

**Vier konfigurierbare Parameter über DHCP:**

* IP-Adresse
* Subnetzmaske
* Standard-Gateway
* DNS-Server

---

### 5. What is the TCP Flow Control mechanism? 
### Is the TCP Flow Control regulated by the sender or by the receiver? (3 points)

TCP Flow Control (Datenflusskontrolle) ist ein Mechanismus, mit dem verhindert wird, dass der Sender den Empfänger mit zu vielen Daten überlastet.

TCP nutzt dazu das "Window"-Feld im Header.
→ Der Empfänger gibt mit dem "Receive Window" an, wie viele Bytes er noch aufnehmen kann.
→ Der Sender passt daraufhin seine Sende­rate an.

✅ Geregelt wird TCP Flow Control vom Empfänger.

---

### 6. Explain the architecture of the Domain Name System! 
### Which DNS servers from the DNS hierarchy are responsible for which domains? (3 points)

**PC → Lokaler DNS → Root DNS (.at, .com, .de) → TLD (example.at) → Authoritative DNS → zurück**

**DNS-Architektur:**

* Root-Nameserver – Zuständig für die Top-Level-Domains (TLDs)
* TLD-Nameserver – Zuständig für Domains unterhalb der TLDs
* Authoritative Nameserver – Enthalten konkrete DNS-Einträge (z. B. A, MX)

**Beispiel:** [www.example.at](http://www.example.at) → Root verweist auf .at → .at verweist auf example.at → liefert IP

---

### 7. Alice ([alice@cannelloni.it](mailto:alice@cannelloni.it)) sends an email from her email-client to Bob ([bob@lee.com](mailto:bob@lee.com)). Stan receives the email with his email-client. Which services (agents) and which application layer protocols are used? Draw a sketch of the delivery process, including the protocols and services (agents) for each step. (3 points)

**Dienste (Agents):**

1. Mail User Agent (MUA) – z. B. Outlook, Thunderbird
2. Mail Transfer Agent (MTA) – z. B. Postfix, Exim
3. Mail Delivery Agent (MDA) – liefert E-Mails ins Postfach
4. Empfänger-MUA – z. B. Thunderbird (Bob)

**Protokolle:**

* SMTP für Versand
* POP3 oder IMAP für Abholung

**Skizze:**
Alice (MUA) → SMTP → MTA → SMTP → MDA → IMAP/POP3 → Bob (MUA)

---

### 8. How does PAT (Port Address Translation) differ from traditional NAT (Network Address Translation)? 
### Provide a scenario where each would be preferable and discuss the technical reasons behind your choices. (3 points)

**NAT:**

* 1:1-Zuordnung (eine private IP wird zu einer öffentlichen IP)

**PAT:**

* 1\:n-Zuordnung (mehrere private IPs teilen sich eine öffentliche IP durch verschiedene Ports)

**Szenarien:**

* NAT: Firma stellt dedizierten Server ins Internet → braucht eigene öffentliche IP
* PAT: Heimnetzwerk mit vielen Geräten → spart öffentliche IPs, skaliert besser

---

### 9. Where can you place a firewall (minimum 3)? 
### Describe all three placements by a use case. 
### Justify your answer. (3 Points)

1. Zwischen Internet und internem Netzwerk
   → Schutz vor externen Bedrohungen
2. Zwischen DMZ und internem Netzwerk
   → Begrenzter Zugriff aus der DMZ auf interne Systeme
3. Host-Firewall am Endgerät
   → Schutz im öffentlichen WLAN

---

### 10. Name and explain 3 types of failures by an example. (3 Points)

* **Crash Failure:** Prozess/Server stürzt ab
* **Omission Failure:** Paket wird nicht gesendet/empfangen
* **Timing Failure:** Antwort kommt zu spät oder zu früh

---

### 11. Describe a problem you (could have) had during the labs. 
### Which structured troubleshooting approach fits well to fix the problem? Which not? 
### Which tools can be used for these approaches? 
### Justify your answer. (3 Points)

**Problem:** Webserver konnte 8.8.8.8 nicht pingen (via Gateway)
**Geeigneter Ansatz:** Divide and Conquer (Layer 3 beginnen)
**Nicht geeignet:** Top-Down (da kein Applikationsproblem)
**Tools:** ping, ip route, traceroute, wireshark
**Begründung:** Netzwerkschicht war betroffen – gezielter Ansatz spart Zeit

---

### 12. 
### a) Name and explain three differences between a Next Generation Firewall (NGFW) and a stateful inspection firewall. (3 Points)

### b) Name and describe one attack for packet filtering firewalls. (1 Point)

**a) NGFW vs Stateful Firewall**

1. Anwendungserkennung – NGFW erkennt Apps unabhängig vom Port
2. Deep Packet Inspection – NGFW prüft Inhalte auf Layer 7
3. Integrierte Sicherheit – NGFW hat IDS, Antivirus, URL-Filter etc.

**b) Angriff:** IP-Spoofing
**Beschreibung:** Angreifer manipuliert Absender-IP, um Filter zu umgehen
