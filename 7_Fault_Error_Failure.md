✅ Topic G: Fault, Error, Failure
Одна из ключевых теоретических тем, встречалась в обоих экзаменах (2022 и 2024).


23. Explain fault, error, and failure. Give an example
✅ Answer:
These three terms describe different stages of a system problem — from cause to visible effect:

Term	Meaning
Fault	A defect or problem in the system — the root cause
Error	The system is in an invalid or incorrect state due to a fault
Failure	The system's observable behavior deviates from the expected

📌 Chain: Fault → Error → Failure

💡 Example 1: Software Bug
Stage	Example
Fault	Programmer writes buggy code: division by zero
Error	At runtime, a division-by-zero occurs → invalid state
Failure	The application crashes or hangs

💡 Example 2: Network Service (bind9 DNS server)
Stage	Example
Fault	Wrong DNS zone file config (e.g., missing semicolon)
Error	Bind9 loads incorrect data into memory → DNS zone not loaded
Failure	DNS requests for that domain fail — users cannot resolve names

📌 Types of Faults
Type	Description	Example
Transient	Temporary, disappears by itself	Power surge
Intermittent	Appears randomly, sometimes works	Flaky network card
Permanent	Stays until fixed	Burnt-out cable, software bug

📌 Prevention and Recovery Strategies
Strategy	What it does
Fault prevention	Design and testing to avoid faults
Fault tolerance	System keeps working despite faults (e.g. redundancy)
Fault removal	Debugging and patching
Fault forecasting	Predict future failures (e.g. SMART disks)

