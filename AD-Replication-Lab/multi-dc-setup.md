# Multi-DC Setup – Step by Step

## 🎯 Objective
Promote a second server (DC02) as an additional Domain Controller and verify replication with DC01.

---

## ✅ Step 1: Prepare DC02
1. Install Windows Server on DC02
2. Set static IP and DNS pointing to DC01
3. Join DC02 to domain

---

## ✅ Step 2: Install AD DS Role
Server Manager → Add Roles and Features → Active Directory Domain Services

---

## ✅ Step 3: Promote DC02
Server Manager → AD DS → Promote this server to a domain controller  
Select: Add a domain controller to an existing domain

---

## ✅ Step 4: Verify Replication
On DC01 or DC02:
```
repadmin /replsummary
```
Ensure no replication errors.

# Author
Name - Saiyed Alisha
