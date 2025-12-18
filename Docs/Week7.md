# Week 7 — Security Audit & System Evaluation

## Overview
This week I performed a structured security audit of my Ubuntu server. I ran a baseline security scan, reviewed network exposure, verified access-control settings, audited running services, and remediated key findings. A final audit was then repeated to confirm improvements.

---

Baseline Security Audit (Lynis: BEFORE)

### Commands used
sudo apt update  
sudo apt install -y lynis  

### What I captured
- Lynis hardening index score (before remediation)
- Key warnings and suggestions that were relevant to my configuration

<img width="756" height="106" alt="d7c31605-48bb-448e-8bc4-d0f7931f7115_black_more_green" src="https://github.com/user-attachments/assets/59e3e69f-2b56-45b8-a6d2-f1a07db5215f" />


<img width="1198" height="382" alt="fa1af1db-91e4-4247-bacd-c2874ca497cb_black_more_green" src="https://github.com/user-attachments/assets/3ae7dddc-d255-42a8-9689-1667934201ba" />

---------------------------------------------------------------------------------------

Post-Remediation Audit (Lynis — AFTER)

Lynis was re-run. (i changed a few more things behind)

**Command used**
- `sudo lynis audit system`

<img width="756" height="106" alt="d7c31605-48bb-448e-8bc4-d0f7931f7115_black_more_green (1)" src="https://github.com/user-attachments/assets/26d8acec-acdc-4b24-806e-a49a2d9b642f" />


<img width="1198" height="382" alt="fa1af1db-91e4-4247-bacd-c2874ca497cb_black_more_green (1)" src="https://github.com/user-attachments/assets/910b3e80-17ca-4764-99d2-4e2040a61dbe" />
Output

The hardening index remained unchanged . This highlights a known limitation of automated scoring tools: some improvements (especially audit/compliance changes) may not increase the numerical score even when they are beneficial.

-------------------------------------------------------------------------------------------------

 Network Security Check (nmap)

A port scan was performed to confirm only intended services were visible on the network. This validates that firewall configuration and service management match the intended “minimal exposure” design.

**Command used (host-only network target)**
- `nmap -sS -sV -p- 192.168.56.102`


<img width="797" height="86" alt="c6a72c16-311d-4e4b-a761-68c506706292_black_more_green" src="https://github.com/user-attachments/assets/1461b699-811f-4d0f-851c-fa8012090b7c" />

-------------------------------------------------------------------------------------------------

The scan revealed that only the SSH service was exposed, indicating that the firewall was correctly configured and the network attack surface was minimised.

-------------------------------------------------------------------------------------------------

Remaining Risk Assessment
-

Despite significant hardening, some residual risks remain. SSH access, although restricted and key-based, remains an exposed service. Additionally, as the system operates within a virtualised environment, its security is partially dependent on the host operating system and hypervisor, which are outside the control of the guest OS.






