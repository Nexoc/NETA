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

* Alle Geräte sind gleichberechtigte Knoten
* Jeder Knoten kann gleichzeitig Client und Server sein

**Vorteile:**

* Skalierbar bei steigender Nutzeranzahl
* Redundanz, da kein zentraler Ausfallpunkt
* Verteilte Ressourcen

**Nachteile:**

* Weniger Kontrolle und Verwaltung
* NAT/Firewall-Komplikationen
* Potenziell unsichere Verbindungen

Beispiel: BitTorrent

---

### 3. In the following an internet standard protocol header is defined. 
### What protocol does this header belong to? 
### What network layer does this protocol belong to? 
### In what kind of documents are such standards defined? 
### Which organization publishes these standards? (2 points)

**Protokoll:** UDP (User Datagram Protocol)
**OSI-Schicht:** Layer 4 – Transportschicht
**Standardisierung:** Definiert in RFCs (Request for Comments)
**Organisation:** IETF (Internet Engineering Task Force)

---

### 4. What is a DHCP protocol? 
### Name 4 parameters that can be configured via DHCP. (3 Points)

**DHCP:** Ein Protokoll zur automatischen Vergabe von IP-Konfigurationsdaten an Clients in einem Netzwerk.

**Konfigurierbare Parameter:**

* IP-Adresse
* Subnetzmaske
* Standard-Gateway
* DNS-Server

---

### 5. What is the TCP Flow Control mechanism? 
### Is the TCP Flow Control regulated by the sender or by the receiver? (3 points)

TCP Flow Control ist dafür verantwortlich, dass ein Sender den Empfänger nicht mit Daten überflutet.

**Mechanismus:**

* Der Empfänger teilt dem Sender über das "Receive Window" mit, wie viel er verarbeiten kann.
* Der Sender passt seine Geschwindigkeit entsprechend an.

✅ Kontrolle erfolgt durch den Empfänger.

---

### 6. Explain the architecture of the Domain Name System! 
### Which DNS servers from the DNS hierarchy are responsible for which domains? (3 points)

**DNS-Architektur:**

* Root-Server: kennt zuständige TLD-Server
* TLD-Server: zuständig für Domains wie .com, .org, .at
* Authoritative Nameserver: kennt die tatsächliche IP für die Domain (z. B. A, MX Record)

Beispiel: [www.fh-campus.at](http://www.fh-campus.at) → Root verweist auf .at → TLD verweist auf fh-campus.at → Authoritative liefert IP

---

### 7. Alice ([alice@cannelloni.it](mailto:alice@cannelloni.it)) sends an email to Bob ([bob@lee.com](mailto:bob@lee.com)). 
### Which services (agents) and which application layer protocols are used? 
### Draw a sketch of the delivery process, including the protocols and services (agents) for each step. (3 points)

**Dienste:**

* MUA: Mail User Agent (Alice & Bob)
* MTA: Mail Transfer Agent
* MDA: Mail Delivery Agent

**Protokolle:**

* SMTP: Übertragung von Alice bis Bob-Server
* POP3/IMAP: Abholung durch Bob

**Skizze:**
Alice (MUA) → SMTP → MTA → SMTP → MDA → POP3/IMAP → Bob (MUA)

---

### 8. How does PAT differ from traditional NAT? 
### Provide a scenario where each would be preferable. (3 points)

**NAT (Network Address Translation):**

* 1:1-Zuordnung (private → öffentliche IP)

**PAT (Port Address Translation):**

* 1\:n-Zuordnung über Portnummern

**Beispiele:**

* NAT: Öffentlich erreichbarer Webserver
* PAT: Heimnetzwerk mit mehreren Clients

---

### 9. Where can you place a firewall? 
### Describe all three placements by a use case. (3 points)

1. Zwischen Internet und internem LAN
   → Schutz vor externen Angriffen
2. Zwischen DMZ und internem Netz
   → Absicherung des internen Bereichs
3. Auf dem Host-System
   → Schutz bei mobilen Geräten in öffentlichen Netzwerken

---

### 10. Name and explain 3 types of failures by an example. (3 Points)

* **Crash Failure:** Server fällt komplett aus
* **Omission Failure:** Antwort oder Nachricht fehlt
* **Timing Failure:** Antwort kommt zu spät

---

### 11. Describe a problem you (could have) had during the labs. 
### Which structured troubleshooting approach fits well to fix the problem? Which not? Which tools can be used for these approaches? 
### Justify your answer. (3 Points)

- **Problem:** Webserver konnte keine Verbindung zu 8.8.8.8 herstellen
- **Geeignet:** Divide and Conquer → Analyse ab Layer 3 (Netzwerk)
- **Nicht geeignet:** Top-down, weil kein Layer-7-Problem
- **Tools:** ping, traceroute, ip route

---

### 12. 
### a) Name and explain three differences between a Next Generation Firewall (NGFW) and a stateful inspection firewall. (3 Points)

### b) Name and describe one attack for packet filtering firewalls. (1 Point)

**NGFW:**

- * Erkennt Anwendungen unabhängig von Ports
- * Unterstützt Deep Packet Inspection (Layer 7)
- * Enthält IDS/IPS, URL-Filterung, Antivirus

**Stateful Firewall:**

* Prüft nur Verbindungsstatus (Layer 4)

**Angriff:** IP Spoofing – Angreifer fälscht IP-Adresse, um Zugriff zu erhalten
