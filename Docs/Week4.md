Week 4 Initial system configuration and system implementation
-----------------------------------

SSH keybased authentication

To improve the SSH safety the key based authentication was configured. This stops password based brute forse attacks and only lets people who have acces use the server.

<img width="903" height="463" alt="Task 4 ssh key based" src="https://github.com/user-attachments/assets/5549ed70-3c88-4f6e-a810-5bbb1182a21f" />


The ssh-keygen command was executed on the workstation using PowerShell to generate an Ed25519 key pair.

----------------------------------------------------------
<img width="777" height="336" alt="task 4 logging in without a password" src="https://github.com/user-attachments/assets/2e361644-6cdc-46a3-b943-ae6399556eb3" />

-------------------------------------------------------------

SSH hardening
Before editing

<img width="731" height="713" alt="week 4 before" src="https://github.com/user-attachments/assets/8bf3069b-a9f5-4ddd-af59-9e98aa6eeb8e" />

After editing

<img width="697" height="236" alt="week 4 after" src="https://github.com/user-attachments/assets/70ad5ed5-7a81-4a5a-9f78-a8077a1f7013" />

---------------------------------

<img width="915" height="133" alt="week 4 password" src="https://github.com/user-attachments/assets/93390c82-935d-4800-aa11-177bd1cb0b65" />

The SSH configuration file (/etc/ssh/sshd_config) was modified to disable password authentication and root login, while explicitly enabling public key authentication. 

Key changes included:
PasswordAuthentication no
PermitRootLogin no
PubkeyAuthentication yes

----------------------------------------------------------------------------

SSH Key Permissions Verification
-----------------------------------

Following the correction of the authorised public key, SSH file permissions and ownership were checked to confirm adherence to OpenSSH security standards. The .ssh folder was limited to the user exclusively, stopping other individuals from accessing or altering SSH configuration files. The authorized_keys file was set up with strict permissions to guarantee that only the account owner can change authorized public keys.

This action was required since OpenSSH will deny key-based authentication if the file permissions are too lenient, serving as a safeguard against unauthorized access and privilege escalation.


<img width="893" height="622" alt="week 4 key permission veri" src="https://github.com/user-attachments/assets/06d3f2fe-13ee-45ef-96a9-8b14fc920d2c" />

Firewall permitting SSH from one workstation only
----------

Showing the complete ruleset

<img width="982" height="530" alt="week 4 firewall" src="https://github.com/user-attachments/assets/2ae84954-c1e9-4586-acfe-54bbd25c58a1" />

Also check the firewall status

----------------------------------

ip from config

<img width="862" height="431" alt="week 4 ipconfig" src="https://github.com/user-attachments/assets/8c0f306c-1ede-4c0b-9c62-f6beae860bf2" />

------------------------------------------------------------------------------------------------

Remote Administration Evidence via SHH

This is whoami and hostname

<img width="428" height="120" alt="week 4 who am i" src="https://github.com/user-attachments/assets/9e13b3dd-60ee-47c7-afb1-ecd50be1912c" />

Uptime

<img width="637" height="42" alt="week4_uptime_black_more_green" src="https://github.com/user-attachments/assets/8e7103f9-cefa-43d6-8b33-d6223339239a" />

Commands such as whoami, hostname and uptime status ssh confirm successful remote administration, system identity.

Reflection
-

This week I focused on securing remote access to my Ubuntu server. I set up SSH key login, disabled insecure SSH options, and added firewall rules to limit who can connect. I also created a non-root admin user and used sudo for admin tasks. Doing everything through SSH helped me practice real remote server management and improved my command-line skills.

