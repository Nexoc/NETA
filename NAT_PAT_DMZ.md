✅ Topic E: NAT, PAT, and DMZ
Темы из экзаменов 2022 и 2024 — Static/Dynamic NAT, PAT, сценарии использования и DMZ.

16. What is the difference between Static NAT and Dynamic NAT? 
Where are they used?

✅ Answer:
Feature	Static NAT	Dynamic NAT
Mapping	One-to-one	Many-to-pool
Address translation	Fixed IP ⇄ Fixed IP	Internal IP ⇄ Any available public IP
Use case	Servers with public IP	Clients accessing internet
Example	192.168.0.10 ⇄ 203.0.113.5	192.168.0.10 ⇄ random from pool
📌 Static NAT is useful for making internal servers reachable from the internet, while Dynamic NAT is used to outbound traffic translation.



17. Explain the difference between NAT and PAT. Give a scenario

✅ Answer:
NAT (Network Address Translation):
Translates private IP addresses to public ones — lets internal devices access the internet.

PAT (Port Address Translation):
An extension of NAT that also translates port numbers, allowing multiple devices to share one public IP.

Feature	NAT	PAT
IP mapping	One-to-one or many-to-one	Many-to-one with unique ports
Port change	❌ No	✅ Yes
Use case	Basic IP mapping	Home/office networks with 1 IP

📌 PAT scenario:
	• 3 devices: 192.168.0.10, .11, .12
	• All use one public IP: 203.0.113.5
	• Translations:
		○ 192.168.0.10:5000 → 203.0.113.5:40001
		○ 192.168.0.11:5000 → 203.0.113.5:40002
Router remembers which internal device maps to which port.



18. What is DMZ? 
What services are placed there and why?
✅ Answer:
DMZ (Demilitarized Zone) — a special network zone that separates external-facing services from the internal network.

📌 Purpose:
Minimize risk — even if the public service is compromised, the attacker cannot access the LAN.
🧱 Typical setup:
	• Two firewalls (or zones in one firewall):
		○ One between internet ⇄ DMZ
		○ One between DMZ ⇄ internal LAN

🖥️ Common services in DMZ:
	• Web servers (HTTP/S)
	• Mail servers
	• DNS servers
	• VPN gateways
	• Proxy servers
📌 Internal databases and sensitive systems must NOT be placed in the DMZ.

