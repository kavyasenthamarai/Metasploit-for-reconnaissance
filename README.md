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
![1](https://github.com/user-attachments/assets/68b576ac-2d78-48c6-b410-372b45047ae3)


Invoke msfconsole:
## OUTPUT:
![2](https://github.com/user-attachments/assets/870f241e-416a-41e9-bcf1-4ca24d43ea1b)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![3](https://github.com/user-attachments/assets/2c9214cf-1ac4-42f7-93d2-440913880a33)




Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
![4](https://github.com/user-attachments/assets/dce1971e-b54d-4971-9cda-47cbe346ec9e)

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
![5](https://github.com/user-attachments/assets/26a71852-09f5-46de-9638-5bd6342d481b)



Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
![6](https://github.com/user-attachments/assets/f68bb281-1c70-4a5c-ba4e-1df49a835e8b)



Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

![7](https://github.com/user-attachments/assets/44d3ae1b-2366-47f8-8968-cbac96a6686f)


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:
![8](https://github.com/user-attachments/assets/4ad66cbc-4b02-4ee1-bf56-6efa0624b309)




## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
![9](https://github.com/user-attachments/assets/6a94858d-cf40-4779-8bb1-7d9377092dce)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
![10](https://github.com/user-attachments/assets/e8cfbc94-6977-4e48-9ac6-e4a42b3b699f)


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:


![11](https://github.com/user-attachments/assets/aa506798-31df-455c-b825-943f9855098b)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:

![12](https://github.com/user-attachments/assets/d397155d-947e-41bc-99dd-17b57d2d18c2)



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
