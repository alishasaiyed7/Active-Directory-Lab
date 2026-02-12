# Break & Fix – Replication Failure Simulation

## ❌ Break Replication
1. Stop AD DS on DC02:
   net stop ntds
2. Or stop DNS service:
   net stop dns

---

## 🚨 Impact
- Changes on DC01 do not reflect on DC02  
- repadmin shows failures  

---

## 🔎 Troubleshooting
repadmin /replsummary  
repadmin /showrepl  
Check Event Viewer → Directory Service & System logs

---

## ✅ Fix
net start dns  
net start ntds  
repadmin /syncall /AdeP  

---

## 🧠 RCA
Replication failed due to AD DS/DNS service outage.

# Author
Name - Saiyed Alisha
