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

<img width="792" height="444" alt="Screenshot 2025-11-11 194658" src="https://github.com/user-attachments/assets/b2ff1ede-2236-4089-b936-a5013feaae34" />

Invoke msfconsole:
## OUTPUT:

<img width="1283" height="757" alt="Screenshot 2025-11-11 194801" src="https://github.com/user-attachments/assets/0f9a5465-d655-4fec-9a05-0d0a95aa1467" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="1256" height="674" alt="Screenshot 2025-11-11 194852" src="https://github.com/user-attachments/assets/2a172ba0-740d-468e-a787-cfb58520831a" />



Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="800" height="304" alt="Screenshot 2025-11-11 200115" src="https://github.com/user-attachments/assets/d4590345-322f-4de8-87ba-17c8f0544ecb" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:



Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:


<img width="691" height="336" alt="Screenshot 2025-11-11 201257" src="https://github.com/user-attachments/assets/566c91d2-32ce-446c-a705-ec854ff53f1d" />

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="1281" height="688" alt="Screenshot 2025-11-11 201646" src="https://github.com/user-attachments/assets/f09025e6-3f15-4ce3-8fa9-717f38c83490" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT 


<img width="811" height="286" alt="Screenshot 2025-11-11 204414" src="https://github.com/user-attachments/assets/5a7732e9-f1b4-455f-ba7b-511512dbea81" />

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="1251" height="329" alt="Screenshot 2025-11-11 212701" src="https://github.com/user-attachments/assets/f6579967-5202-4fdd-903a-4cb9b3a6fc03" />

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:

<img width="1271" height="537" alt="Screenshot 2025-11-11 212824" src="https://github.com/user-attachments/assets/e48acc7c-21de-4d4d-a06d-9c58e87d05a8" />

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="1263" height="385" alt="Screenshot 2025-11-11 213051" src="https://github.com/user-attachments/assets/7738b41e-8313-480d-9130-5666f0feb588" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="1279" height="144" alt="Screenshot 2025-11-11 213155" src="https://github.com/user-attachments/assets/63e50e99-3e18-4d53-8c1c-091ef3854fc9" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:


<img width="1234" height="527" alt="Screenshot 2025-11-11 222509" src="https://github.com/user-attachments/assets/fbfbe56c-d623-4d75-ab20-1d968377a090" />


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:


<img width="1281" height="295" alt="image" src="https://github.com/user-attachments/assets/c1746994-9132-4d53-8db1-5613d0472dcc" />




## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
