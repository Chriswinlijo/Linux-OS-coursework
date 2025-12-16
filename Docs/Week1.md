Week 1-System Planning And Initial Setup
------------------------------------------------------------------------------------------------------------------------------------------------------------------------

1. System architecture diagram
<img width="860" height="476" alt="image" src="https://github.com/user-attachments/assets/10ff80c4-920a-4ce0-960f-2837696a456c" />

------------------------------------------------------------------------------------------------------------------------------------------------------------------------
2. Distrubution secection justification

I have chosen Ubuntu server LTS for this coursework as it provides a strong balance of stability and fast access to commonly required packages and tooling for headless server managed by SSH. Ubuntus LTS also has constand security updates which supports the laster coursework where patching.

I did not choose Debian as its more conservative package cadence can slow down setup and will not help me as much. i needed something with faster configuration and troubleshooting with widly avalable documentation and straightforward package management and thats why i chose Ubuntu server.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
3. Workstation Configuration Decision

I have chosen option b using my host machine as the workstation with Powershell as the SSH client as i would no longer need to run another VM, it also has lower resource usuage and much easier workflow as it allows me to copy and paste.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
4. Network Configuration Documentation VirtualBox Network Setup
Adapter 1 (NAT): Internet access
<img width="953" height="596" alt="Task 1 NAT" src="https://github.com/user-attachments/assets/31b17fc0-67e5-47fb-9343-d2e0a148c14f" />


Adapter 2 (Host-Only Adapter – vboxnet0): Secure internal SSH network
<img width="961" height="588" alt="task 1 host only" src="https://github.com/user-attachments/assets/43353063-cfe7-48ea-a0b9-921d5a22beec" />

Server Network Output
From ip addr command:
enp0s8 = 192.168.56.3/24 (Host-Only Network)
<img width="812" height="523" alt="Task 1 Getting ip via ipaddr" src="https://github.com/user-attachments/assets/752a8aee-f1d0-4f6e-8fb1-ae64e7d2e53c" />

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

5. System Specifications (CLI Evidence) Kernel Info (uname -a)

<img width="927" height="65" alt="Task 1 uname -a" src="https://github.com/user-attachments/assets/009d22c8-5788-41c3-b18d-9168b18ef8e9" />

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Memory info (free-h)

<img width="977" height="123" alt="Task 1 free -h" src="https://github.com/user-attachments/assets/03964ea1-0616-4082-beb4-8c74b887ef49" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Disk Info (df -h)

<img width="637" height="207" alt="Task 1 df- h" src="https://github.com/user-attachments/assets/7934dc7a-dd14-47b8-97e5-0a857042152f" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Network Info (ip addr)

<img width="1152" height="512" alt="tast 1 ipaddr" src="https://github.com/user-attachments/assets/d78d6243-2832-4589-af97-d5fa47cd0fe8" />

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Release Info (lsb_release -a)

<img width="560" height="132" alt="Task 1 lab_release -a" src="https://github.com/user-attachments/assets/163effbb-1f3d-4c89-9fc2-b18940a8e128" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

7. Reflection

This week I set up my Ubuntu Server VM in VirtualBox and connected to it from my host PC using SSH (PowerShell). I enabled two network adapters: NAT for internet updates and Host-Only so my host computer could reach the VM. I checked the VM’s IP address using ip addr and confirmed SSH was working. I ran commands like uname, free -h, df -h, ip addr, and lsb_release to collect system information and added an architecture diagram to my journal.






