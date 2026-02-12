## 🧠 Interview-Ready One-Liners

Why multiple DCs? \
To avoid single point of failure and ensure high availability of authentication services.
\
What is replication? \
Automatic synchronization of AD changes across DCs.
\
What if DC02 changes don’t reflect on DC01?\
Check replication health with repadmin, verify DNS, RPC connectivity, and AD DS service status.
\
RPC over IP (Port 135)?\
AD replication uses RPC for communication between DCs; blocked ports or firewall rules break replication.
