✅ Topic F: Firewalls and Security
Покрывает: виды фаерволов (packet filtering, stateful, NGFW), атаки, размещение (DMZ, bastion host, host firewall).
Эта тема была в экзаменах 2022 и 2024.

19. What is the difference between Packet Filtering and Stateful Inspection Firewalls?
✅ Answer:
Feature	Packet Filtering Firewall	Stateful Inspection Firewall
Checks	Only individual packets	Entire connection state
Memory/Tracking	❌ No memory	✅ Maintains connection table
Security level	Basic (stateless)	More secure (state-aware)
Attacks it can't stop	Spoofed packets, fragmented attacks	Can block irregular TCP behavior
📌 Packet filter allows or denies based on source/dest IP, port, protocol.
📌 Stateful firewall allows only responses to valid requests — e.g., only replies to initiated connections.




20. What is an NGFW (Next-Generation Firewall)? How is it better than stateful inspection?

✅ Answer:
NGFW = Stateful firewall + deep inspection + application awareness

Feature	NGFW	Traditional Firewall
Layer support	OSI Layer 7	Up to Layer 4
Deep Packet Inspection (DPI)	✅ Yes	❌ No
Application filtering	✅ Yes (e.g. block Facebook, Zoom)	❌ No
User ID awareness	✅ Can link traffic to users	❌ IP-based only
Threat detection	✅ Built-in IPS, AV, etc.	❌ No intelligence
📌 NGFW is ideal for modern threats — controls apps, detects malware, integrates with Active Directory.


21. Name an attack that a packet filtering firewall cannot stop
✅ Answer:
IP Spoofing or Tiny Fragment Attack
	• IP Spoofing: Attacker forges source IP to bypass IP-based rules
		○ Packet filter cannot verify connection state → allows spoofed packet
	• Tiny Fragment Attack:
		○ TCP headers split into very small IP fragments
		○ Firewall sees only part of the packet → rules are bypassed
📌 Only stateful or deep-inspection firewalls can handle this properly.




22. Where are firewalls placed? 
Explain Bastion Host, Host Firewall, Personal Firewall
✅ Answer:
📌 Firewalls are placed at strategic points to control traffic:

🛡 Bastion Host
	• A hardened server exposed to untrusted networks (e.g., internet)
	• Usually in the DMZ
	• Runs limited services (e.g., SSH, Proxy)
	• Fully monitored and locked down
📌 First target during attacks — must be well protected.

💻 Host Firewall
	• Software-based, runs on a server or workstation
	• Controls inbound/outbound traffic per interface, IP, port, application
📌 Example: ufw on Linux, iptables, Windows Firewall (advanced settings)

👤 Personal Firewall
	• Designed for end-users (desktop/laptops)
	• Focused on application-based rules, often with GUI
	• Includes outbound connection alerts, malware blocking
📌 Example: integrated into antivirus packages like Kaspersky, Norton

Summary:
Firewall Type	Scope	Placement
Bastion Host	Public exposure	DMZ
Host Firewall	Server-specific	Individual machines
Personal Firewall	End-user devices	Local desktop/laptops
