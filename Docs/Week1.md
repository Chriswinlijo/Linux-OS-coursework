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


5.



