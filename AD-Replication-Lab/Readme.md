# Active Directory Replication (Multi-DC) – Hands-On Lab

## 📌 Project Overview
This project demonstrates a multi-domain controller (DC) Active Directory setup to understand how AD replication works, why multiple DCs are required in enterprise environments, and how to troubleshoot real-world replication issues.

The lab covers health checks, forced replication, common failure scenarios, and recovery steps using built-in Windows tools and PowerShell.

---

## ❓ What is AD Replication?
Active Directory Replication is the process by which changes made on one Domain Controller (DC) are automatically synchronized to other DCs within the same domain and forest.

Examples of replicated data:
- User account creation/deletion
- Password resets
- Group membership changes
- GPO changes
- Computer objects

---

## 🎯 Why is AD Replication Important?
- **High Availability:** If DC01 fails, DC02 can authenticate users.
- **Load Balancing:** Authentication requests are distributed.
- **Disaster Recovery:** No single point of failure.
- **Consistency:** Ensures all DCs have the same directory data.

---

## 🏗 Lab Architecture
- DC01: Primary Domain Controller  
- DC02: Additional Domain Controller (replication partner)  
- Windows Client joined to the domain

---

## 🧪 Lab Scenarios Covered
- Verify replication health between DC01 and DC02  
- Simulate replication failure  
- Force manual replication  
- Troubleshoot DNS, RPC, and AD DS service issues  
- Understand FSMO role placement impact  
- Monitor replication using repadmin and dcdiag  

---

## 🛠 Tools & Commands Used
dcdiag /v  
repadmin /replsummary  
repadmin /showrepl  
repadmin /syncall /AdeP  
net stop ntds  
net start ntds  

---

## 📚 Real-Life Use Cases
- Enterprise AD environments with multiple DCs per site  
- Branch office replication  
- DR scenarios when primary DC goes down  
- Password reset propagation issues  

---

## 🧠 Learning Outcomes
- Deep understanding of AD replication architecture  
- Ability to detect and fix replication issues  
- Real-world troubleshooting mindset for L2/L3 roles  

---

## Author
Name - Saiyed Alisha
