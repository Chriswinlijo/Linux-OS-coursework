Week 5 – Advanced Security and Monitoring Infrastructure
-

I will be using AppArmor and implementing advanced security controls and building automation to verify security posture and monitor system performance remotely. 

----------------------------------------

Track and report on access control settings
-
Actions Taken

I confirmed that AppArmor is enabled on the Ubuntu server and that its profiles are running in enforce mode.

Command Purpose

The aa-status command summarises AppArmor’s current state, showing whether the AppArmor module is loaded, the number of loaded profiles, and how many are enforcing restrictions.

Security Relevance

AppArmor adds an extra security layer by limiting what processes can read, write, or execute. This helps contain the impact of an exploit by reducing what a compromised service is permitted to access.


<img width="481" height="152" alt="3cc63670-011d-4767-93f9-c0df8497f64f_black_more_green" src="https://github.com/user-attachments/assets/6f3682f4-0ae7-4af6-899c-be62d7c544c3" />


-
<img width="1207" height="390" alt="a4ed27d3-de0e-4729-b2cf-245880d7ca1a_black_more_green" src="https://github.com/user-attachments/assets/74c18e77-7c7f-4381-a214-1e3905d9c1f1" />

----------------------------------------------------------------------------------------------

Actions Taken

I enabled unattended security updates so the server can automatically install important security patches.

Command Purpose

Installing unattended-upgrades sets up the automatic upgrade service.
dpkg-reconfigure unattended-upgrades turns it on, and checking the config file confirms the update schedule is enabled.

Security Relevence

Automatic updates reduce the time the system stays vulnerable to known issues by applying security fixes without needing constant manual checks.


<img width="772" height="357" alt="f32d32e7-7d52-4864-8abc-2fb18dbcbc4b_black_more_green" src="https://github.com/user-attachments/assets/595071b7-5e6e-479c-8ab2-c8fd9e6d8a45" />

----------------------------------------------

Configure fail2ban
-
Fail2ban was installed so enabled so that it can portect the SSSH service from the brute force login attemps, it monitors logs and will block any attepms which input wrong login attemps. This means there will be a reduced amouth of unauthrised access over time.


This is me install fail2ban

<img width="1206" height="508" alt="365c6411-b04f-4c6d-9922-f5f9ca7f3707_black_more_green" src="https://github.com/user-attachments/assets/4af6b9aa-2db2-4e53-81fb-d768ddfbb94a" />



This is me activating it and starting it up, i have also shown that it is still running and that its active.

<img width="1213" height="707" alt="34e5dcdc-2e30-4135-a60c-a23617bfeaf7_black_more_green" src="https://github.com/user-attachments/assets/505a8cfd-e26b-4c4c-92f5-4561feff74f7" />

---------------------------------------------------------------------------------

Creating a security baseline verification script
----


I made a script so that it can automatically verify that all the security controls are active, it basically checks SSH configuration, firewall, AppArmor status and more in just one run. This is good because it improvs relaibility and quick verification after system changes or reboots.
<img width="548" height="36" alt="week 5 minorter" src="https://github.com/user-attachments/assets/18b6bfb3-7947-48d3-999b-a88ac0926b50" />

<img width="615" height="47" alt="e9951ee7-e7f6-489c-90c0-85a394117e87_black_more_green" src="https://github.com/user-attachments/assets/d502b0ea-6ac3-4593-ae98-9ab10680a9ad" />

----------------------------------------------------------

<img width="553" height="27" alt="50399ae6-6025-4051-b58e-d456be7e98a4_black_more_green" src="https://github.com/user-attachments/assets/719fb858-6915-4dfa-8125-9e6d78927326" />

-------------------------------------------------------------------------------

Creating a monitoring script
-------------

I made a remote monitoring script that connects to the server through SSH and gets live performance metrics. The script remotely executes commands such as uptime, free -h, df -h, and ps to collect system performance data without logging into the server interactively.



Here i created the script

![Uploading week 5 minorter.png…]()


This is all the running of the script and the output

<img width="921" height="76" alt="week 5 mon" src="https://github.com/user-attachments/assets/3c9077e8-5c2a-41b4-8023-538dd883555e" />

----------------------------------------------------------------------------------

Reflection
--

Week 5 was about improving security and adding more automation. I checked AppArmor was enforcing profiles, enabled unattended upgrades to reduce patching delays, and set up Fail2Ban to help block brute-force SSH attacks. I also created simple scripts to verify security settings and support remote monitoring, which made admin tasks more relaible.

