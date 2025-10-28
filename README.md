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

<img width="641" height="508" alt="Screenshot 2025-10-28 204338" src="https://github.com/user-attachments/assets/9c0baa87-66cd-4905-b59a-92f090b566d9" />

Invoke msfconsole:
## OUTPUT:
<img width="646" height="512" alt="Screenshot 2025-10-28 204441" src="https://github.com/user-attachments/assets/9bc2fd81-ce6a-4b6c-ae4d-f9fd1ac1e21e" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="654" height="515" alt="Screenshot 2025-10-28 204604" src="https://github.com/user-attachments/assets/0a0e263b-fee4-4c2b-a4a7-6929bf8f2f27" />



Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="677" height="517" alt="Screenshot 2025-10-28 205332" src="https://github.com/user-attachments/assets/7329fef4-af39-46c8-81b6-f6acee4f927a" />


step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img width="654" height="513" alt="Screenshot 2025-10-28 211143" src="https://github.com/user-attachments/assets/2d85320b-eefe-4f2e-8309-b74b6b43abfe" />



Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="653" height="513" alt="Screenshot 2025-10-28 212001" src="https://github.com/user-attachments/assets/50dc7da1-9308-4081-9445-87885e56c8c8" />


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="659" height="519" alt="Screenshot 2025-10-28 212304" src="https://github.com/user-attachments/assets/9ce612f5-d01e-49ea-84b9-6e06c68ffd8b" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="657" height="518" alt="Screenshot 2025-10-28 212629" src="https://github.com/user-attachments/assets/b6f40b0c-93ff-47d2-97dc-8458509f2c3b" />


## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="648" height="624" alt="Screenshot 2025-10-28 215628" src="https://github.com/user-attachments/assets/52be9262-c8a7-4746-a80f-265c953768f1" />


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="997" height="612" alt="Screenshot 2025-10-28 220638" src="https://github.com/user-attachments/assets/eb92001f-7056-4ac5-9ae7-5653490ec94d" />



use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
<img width="974" height="608" alt="Screenshot 2025-10-28 220731" src="https://github.com/user-attachments/assets/baf52a33-e9e0-4bc2-973f-3dd093cc16eb" />




Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="714" height="117" alt="Screenshot 2025-10-28 220859" src="https://github.com/user-attachments/assets/9c86422f-73d3-4f6b-bb43-a9487dfb6119" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:

<img width="969" height="554" alt="Screenshot 2025-10-28 221540" src="https://github.com/user-attachments/assets/3bd1e487-5e8b-49c4-b740-2a8cf0e442b8" />



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:

<img width="921" height="689" alt="Screenshot 2025-10-28 223319" src="https://github.com/user-attachments/assets/e1fe2ee9-dc10-4023-ba42-d36570caf77a" />





## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
