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
![1output](https://github.com/viswapriyaG/Metasploit-for-reconnaissance/assets/131427787/822d42ce-881a-45e7-8118-d9058f0d425d)

Invoke msfconsole:
## OUTPUT:
![2output](https://github.com/viswapriyaG/Metasploit-for-reconnaissance/assets/131427787/ec3be23d-3ebc-44ce-af1d-de3cef490f5e)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![3output](https://github.com/viswapriyaG/Metasploit-for-reconnaissance/assets/131427787/e9aef51c-1134-468f-b757-be09f4696d93)

Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000
## OUTPUT:
![4output](https://github.com/viswapriyaG/Metasploit-for-reconnaissance/assets/131427787/8cee3a0a-a2f8-4a81-97d5-e798bc661d8a)

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
![5output](https://github.com/viswapriyaG/Metasploit-for-reconnaissance/assets/131427787/d33c35df-48f8-4988-9f7a-3aebe8cbfcc4)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
![6output](https://github.com/viswapriyaG/Metasploit-for-reconnaissance/assets/131427787/dbede6d3-71a2-491c-a94c-2cb81ebec7a4)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit

The info command provides information regarding a module or platform,
## OUTPUT:
![7output](https://github.com/viswapriyaG/Metasploit-for-reconnaissance/assets/131427787/8a3adbd5-c2df-4fa6-b871-0bed0adef978)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
![8output](https://github.com/viswapriyaG/Metasploit-for-reconnaissance/assets/131427787/b6691614-ea30-45ee-86c6-6a35baa7d1b1)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
![9output](https://github.com/viswapriyaG/Metasploit-for-reconnaissance/assets/131427787/c6e96a50-acc4-435a-88a8-d7c68bf9182d)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
![10output](https://github.com/viswapriyaG/Metasploit-for-reconnaissance/assets/131427787/bf121663-f52c-4841-a7df-8232a8e3b9fe)

Use the set rhosts command to set the parameter and run the module, as follows:
![11output](https://github.com/viswapriyaG/Metasploit-for-reconnaissance/assets/131427787/e44bb7bd-79c2-4606-be3a-f3187e97151e)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
![12output](https://github.com/viswapriyaG/Metasploit-for-reconnaissance/assets/131427787/48d34939-a0e3-4d68-a6ad-08cecc049b7e)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
![13output](https://github.com/viswapriyaG/Metasploit-for-reconnaissance/assets/131427787/29921cc4-b8f9-4a47-88b3-888175930bb2)


## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
