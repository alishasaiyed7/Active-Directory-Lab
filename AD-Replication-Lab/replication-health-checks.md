# Replication Health Checks

## 🎯 Objective
Verify AD replication status between DC01 and DC02.

---

## ✅ Commands
repadmin /replsummary  
repadmin /showrepl  
dcdiag /v  

---

## ✅ What to Look For
- Last success time  
- Failure count = 0  
- No RPC/DNS errors  

---

## 🧠 Explanation
These tools provide visibility into replication partners, failures, and service health.

# Author
Name - saiyed Alisha
