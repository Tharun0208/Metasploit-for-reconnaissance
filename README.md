# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting
 
# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:
<img width="603" height="357" alt="image" src="https://github.com/user-attachments/assets/fa0287b2-b5a9-41a4-83e2-26bde017d94a" />


Invoke msfconsole:
## OUTPUT:
<img width="755" height="711" alt="image" src="https://github.com/user-attachments/assets/00773c60-5113-4996-85e8-da21095cdf04" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


<img width="733" height="800" alt="image" src="https://github.com/user-attachments/assets/142317ee-2200-4af3-8c9c-99695805f03f" />


Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:

<img width="547" height="188" alt="image" src="https://github.com/user-attachments/assets/5d6059f1-4d68-4850-94e8-e99d410e1b4a" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="658" height="117" alt="image" src="https://github.com/user-attachments/assets/bc3253d0-e843-4c98-82ed-c4ad8d00e9a7" />




Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="943" height="787" alt="image" src="https://github.com/user-attachments/assets/43d524eb-77ff-4baa-9aa2-1eeb1dc8a2ab" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="668" height="227" alt="image" src="https://github.com/user-attachments/assets/b0a10653-0c94-436a-a0f0-e0d79ed3b5d4" />



## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:

<img width="741" height="135" alt="image" src="https://github.com/user-attachments/assets/e1a8f352-2e1a-4a2d-8d1f-5e5f668a3fd7" />

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql

## OUTPUT:

<img width="967" height="572" alt="image" src="https://github.com/user-attachments/assets/720c40dc-b5d9-460c-bcdd-234ba967d8a5" />

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version

## OUTPUT:



<img width="605" height="57" alt="image" src="https://github.com/user-attachments/assets/7776ab14-20aa-4c17-9a2a-51f48a1b272e" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="567" height="122" alt="image" src="https://github.com/user-attachments/assets/59024823-553b-479c-ba78-d6e530883de7" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:

<img width="555" height="97" alt="image" src="https://github.com/user-attachments/assets/9aad778b-691d-4cdd-a140-03b3d5828b47" />



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:



<img width="772" height="457" alt="image" src="https://github.com/user-attachments/assets/42456ae3-75cc-4629-af83-10195725cf90" />



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
