## Topic G: Fault, Error, Failure

**Covers:** Definitions, relations between terms, examples  
_Asked in both 2022 and 2024 exams_

---

### 23. Explain fault, error, and failure. Give an example

**Answer:**

These terms describe **stages of a problem in a system**:

| Term       | Meaning                                                   |
|------------|-----------------------------------------------------------|
| **Fault**  | A defect or root cause in the system                      |
| **Error**  | An invalid or incorrect state caused by a fault           |
| **Failure**| Visible deviation from expected system behavior           |

> 📌 Chain: **Fault → Error → Failure**

---

### 💡 Example 1: Software Bug

| Stage     | Example                                           |
|-----------|---------------------------------------------------|
| Fault     | Programmer writes buggy code (e.g., division by zero) |
| Error     | Division by zero occurs at runtime → crash state  |
| Failure   | The program crashes or hangs                      |

---

### 💡 Example 2: DNS Server (e.g., bind9)

| Stage     | Example                                                      |
|-----------|---------------------------------------------------------------|
| Fault     | Wrong syntax in zone file (e.g., missing semicolon)          |
| Error     | Bind9 loads invalid data → zone not loaded                    |
| Failure   | DNS queries fail → users cannot resolve domain names          |

---

### Types of Faults

| Type          | Description                           | Example                          |
|---------------|---------------------------------------|----------------------------------|
| **Transient** | Temporary, disappears by itself       | Power surge                      |
| **Intermittent** | Appears randomly, comes and goes   | Faulty NIC or loose cable        |
| **Permanent** | Stays until manually fixed            | Burned-out hardware, logic bug   |

---

### Prevention and Recovery Strategies

| Strategy             | What it does                                                  |
|----------------------|---------------------------------------------------------------|
| **Fault prevention** | Avoid faults during design/testing                            |
| **Fault tolerance**  | System keeps working despite faults (e.g., redundancy)        |
| **Fault removal**    | Debugging, patching, correcting errors                         |
| **Fault forecasting**| Predict faults using analysis (e.g., SMART for disks)         |

---

> 📌 On the exam, you may be asked to:  
> - Define the terms clearly  
> - Show the relationship between them  
> - Give a **real-world example**
```


