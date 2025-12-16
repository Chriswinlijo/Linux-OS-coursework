Week 2 — Security planning and testing methodology
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

1. Performance testing plan
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

I will evaluate my Ubuntu Server VM using remote monitoring via SSH from my workstation. I will measure CPU, memory, disk I/O, network throughput, and service response time under both idle and load conditions.

---------------------------------------
Monitoring tools/commands:
---------------------------

CPU: top, htop, vmstat, mpstat

Memory: free -h, vmstat

Disk: iostat, df -h, fio

Network: ping, iperf3, ss, nload

Service response: curl, ab

------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Testing method:
-----------------

Baseline: record statistics while the server is idle

Load tests: run CPU, memory, disk, network, and service workloads

Identify bottlenecks: determine which subsystem becomes saturated

Optimise + re-test: apply changes and compare results across runs

All testing will be executed remotely through SSH.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
2. Security configuration checklist

| Security Area                        | Planned Configuration                                                                                                                         |
| ------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **SSH Hardening**                    | Use SSH key authentication; turn off password logins; block root SSH access; allow SSH only on the Host-Only management network.            |
| **Firewall Configuration**           | Set up `ufw` with a default-deny inbound policy and permit SSH only from my workstation’s Host-Only IP address.                             |
| **User & Privilege Management**      | Create a dedicated admin user (non-root); follow least-privilege; limit sudo rights to required administration tasks only.                  |
| **Automatic Security Updates**       | Enable unattended security patching so critical updates are applied automatically and recorded in system logs.                               |
| **Mandatory Access Control**         | Keep AppArmor enabled and verify profiles are enforcing to reduce application permissions and restrict access to sensitive paths/resources.  |
| **Intrusion Detection & Prevention** | Deploy Fail2Ban to detect repeated SSH failures and temporarily ban offending sources based on defined thresholds.                           |
| **Network Security Measures**        | Remove/disable unused services; audit open ports regularly; ensure only required services are listening on the server.                      

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

| Threat                          | Description                                                                  | Mitigation Strategy                                                                                                                       |
| ------------------------------- | ---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| **Unpatched Vulnerabilities**   | Older packages and services may contain known security flaws that can be exploited. | Enable unattended security updates, run regular `apt update && apt upgrade`, and review update logs to confirm patches are applied.      |
| **Brute-force SSH Attempts**    | Attackers try repeated logins to gain SSH access.                            | Use SSH keys only, disable password authentication, limit SSH to the Host-Only network/workstation IP, and deploy Fail2Ban for bans.     |
| **Privilege Escalation**        | A user with limited access attempts to gain root or broader permissions.     | Use a non-root admin account, apply least-privilege sudo rules, enforce AppArmor profiles, and tighten file/permission ownership settings. |

   

