# Metapsloit-Operator-Lab-Project-6-

## Overview
This project demonstrates an End-to-end attack chain leveraging a vulnerable Samba service, followed by Metasploit-based post-exploitation including credential discovery, network enumeration, privilege-escalation assessment, SSH persistence, data extraction, and cleanup.

## Objective
The objective of this project was to simulate realistic red team and penetration testing methodologies by gaining an initial foothold on a vulnerable target, performing post-exploitation to extract high value information, analyzing privilege escalation opportunities, establishing persistence to enable re-entry, and demonstrating responsible cleanup tehcniques.The focus was on attacker decision making, tradecraft, and manual exploitation instead of using a means of automation such as linpeas.

## Environment & Architecture
• For this project I used both my kali and metasploitble vm's on a NAT Network isolated from the internet creating a safe and ethical environment. 
• Kali = Attacker
• Target = Metapsloitable

## Tools Used
• nmap
• metasploit

## Attack Path / Methodology
• I ran an nmap scan against the target and discovered that the the OS was metasploitable, known for having a large attack surface as there are many msiconfigurations exposed services. 

• To gain a foothold onto the target machine I chose samba because I know that samba has a lot of known exploits, with one being exploit/multi/samba/usermap_script as the target is succeptible to, for the samba version 3.0.20

• The exploit only required me to fill in the RHOSTS(Metasploitable-IP) and my LHOST(Kali-IP). I ran the exploit and it was successful allowing me to gain initial access through from a shell as the root user.



## Findings
• Since I became root after getting a shell, I had searched for the .bak files and I had access to them. The contents of .bak files consisted of usernames and hashes, creating another means of re-entry
• known hosts
• etc resolv.conf
• tec/network//interfaces

## Post Exploitation Activities
• After initial compromise I performed post compromise internal to identify additional services that are not visible from an external standpoint.

• The purpose of running commands such as ip a, ip route, arp -a, netstat -tulpn, ss -tulpn and ip a was to gain more insight on the internal environment including active interfaces, routing paths, neighboring hosts, and services that re listening locally. 

• In a real penetration test, this step is critical because systems usually expose internal only services, management interfaces or trust relationships that cannot be discovered from external recon. Repeating this workflow helps develops muscle memory and mirrors post exploitation techniques within professional engagements. 

## Persistence & Re-Entry
• After achieving full administrative access, I created a persistence mechanism to demonstrate how an attacker could maintain access between sessions. I added a controlled ssh key to the targets authroized_keys file, allowing me to ssh in as the root user without the need of a password

Note: I wasn't able to ssh in because the metasploitable machine is so outdated I tried to generate different keys and troubleshoot but nothing worked, I can't ssh into the metasploitable vm generally, it doesn't seem to work. 

## Cleanup & Restoration
• After completing this project,everything that was introuduced during testing was removed to restore system to itss original state. This included termininating the meterpreter session and removing the previously added ssh public key, which was used solely to simulate persistence techniques in a controlled environment. 

## Lessons Learned / Conclusion
• Gained experience with post-exploitation persistence concepts, including using an ssh keys to maintain controlled re-entry to a compromised system
• Improved familiarity with metasploit workflows, including managing sessions, post exploitation modules, and 
• Practiced data extraction techniques from compromised hosts, highlighting how attackers and red teamers extract files for offline analysis 
