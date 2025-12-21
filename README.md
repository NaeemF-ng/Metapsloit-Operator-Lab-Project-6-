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

• To gain a foothold onto the target machine I chose samba because I know that samba has a lof of known exploits, with one being exploit/multi/samba/usermap_script as the target is succeptible to, for the samba version 3.0.20

• The exploit only required me to fill in the RHOSTS(Metasploitable-IP) and my LHOST(Kali-IP). I ran the exploit and it was successful allowing me to gain initial access through a shell.

[]()


## Post Exploitation Activities

## Persistence & Re-Entry
## Cleanup & Restoration
## Findings
## Lessons Learned / Conclusion
