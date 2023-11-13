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

## PROGRAM:
Find out the ip address of the attackers system

## OUTPUT:

![244912300-b4069541-3b92-4003-8b62-a8802181e4ba](https://github.com/KRISHNARAJ-D/Metasploit-for-reconnaissance/assets/119559695/6afd91ea-02c6-4c01-a7fb-7ab79f2b0189)


### Invoke msfconsole:

## OUTPUT:
![244912302-329df4fa-d60d-40f0-b73f-99eb08ad34c3](https://github.com/KRISHNARAJ-D/Metasploit-for-reconnaissance/assets/119559695/def84753-0368-44b0-8803-2238eb874ce9)





### Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![244912498-28f8f4e2-1b2b-4f10-a526-f9ac1bbb5de6](https://github.com/KRISHNARAJ-D/Metasploit-for-reconnaissance/assets/119559695/3ac90008-4507-40f4-b6d0-21e33e02ba17)




## Port Scanning:
### Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
### msf >  nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:

![244912303-6ca2d9ae-c61c-4533-95ce-d9ef2861573d](https://github.com/KRISHNARAJ-D/Metasploit-for-reconnaissance/assets/119559695/743beee3-2446-4375-991b-1da4a045f52d)




### step 4:
### use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

### scan the targets with the command db_nmap as follows.
### msf > db_nmap 192.168.181.0/24
## OUTPUT:


![244912569-9118b2c2-ea43-4b64-bf5e-33616089e9b8](https://github.com/KRISHNARAJ-D/Metasploit-for-reconnaissance/assets/119559695/c86fb35d-7e46-47ec-8bd7-228e7b196abc)






Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:


![244912304-8d6772bb-22fc-48ad-8ca6-bfaa916e8274](https://github.com/KRISHNARAJ-D/Metasploit-for-reconnaissance/assets/119559695/530f9c06-7163-4b7d-972b-dad55343a3d5)





Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit


![244912309-1eec15ac-f151-47b2-9b9b-08e4bd115b8f](https://github.com/KRISHNARAJ-D/Metasploit-for-reconnaissance/assets/119559695/6a73222d-607b-4c56-bf80-db5b67ba7c43)




The info command provides information regarding a module or platform,

## OUTPUT

![244912311-d838ad1b-910b-473b-975c-1beb88a8e608](https://github.com/KRISHNARAJ-D/Metasploit-for-reconnaissance/assets/119559695/8c7692ab-9271-420d-bfc7-dcd461ab6e22)



Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>


![244912323-3f864ba1-c0b9-4568-836b-2d567f63e98f](https://github.com/KRISHNARAJ-D/Metasploit-for-reconnaissance/assets/119559695/dcb4a081-248c-4b05-8f30-33d5c2badbd8)


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql




![244912312-05deb83c-a488-465e-98ee-83195e163903](https://github.com/KRISHNARAJ-D/Metasploit-for-reconnaissance/assets/119559695/cbe672f5-c96b-4626-b45d-1602a1db293b)




use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version



![244912315-88e8cbf7-1d72-4cdd-8fa3-01d5ddf2719a](https://github.com/KRISHNARAJ-D/Metasploit-for-reconnaissance/assets/119559695/21e5bdc8-b657-4a91-a3b6-67709ef16feb)





Use the set rhosts command to set the parameter and run the module, as follows:



![244912317-a3ddcc64-a0b7-4b62-9685-29b0e58fec8f](https://github.com/KRISHNARAJ-D/Metasploit-for-reconnaissance/assets/119559695/52964e6c-8e7e-430b-9b2a-d0d93a0e3917)







After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.



![244912318-b0f0a571-a306-4a0f-97d7-4bda19b1676c](https://github.com/KRISHNARAJ-D/Metasploit-for-reconnaissance/assets/119559695/b8538174-1400-4adb-b56f-757cd3c1f6c0)







set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true




![244912321-967aca0b-45b6-4e70-8a06-d611c11b1c0f](https://github.com/KRISHNARAJ-D/Metasploit-for-reconnaissance/assets/119559695/eef5da6f-54e8-4231-b46d-5880ca000d5f)











## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
