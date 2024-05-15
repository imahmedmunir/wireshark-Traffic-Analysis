## All this has been very interesting, we made forensic to look into details what happened. we used enumerated knowledge to analyse what has been done. This is task to get back in to overpass-production server

### The attacker defaced the website. What message did they leave as a heading?
Answer: H4ck3d by Cooctusclan

Hint: you can look this into wireshark logs http or run the target machines IP address on browser

**make your way back in, connect back in**

if you run "nmpa -sC -sV target$IP ", you can see the ports opened to connect. 
However if you look into main.go code from previous task, it also listed port.

use password: november16

**──(root㉿kali)-[~/Desktop]
└─# ssh -oHostKeyAlgorithms=+ssh-rsa -p 2222 james@10.10.157.164
The authenticity of host '[10.10.157.164]:2222 ([10.10.157.164]:2222)' can't be established.
RSA key fingerprint is SHA256:z0OyQNW5sa3rr6mR7yDMo1avzRRPcapaYwOxjttuZ58.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[10.10.157.164]:2222' (RSA) to the list of known hosts.
james@10.10.157.164's password: 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.**

**james@overpass-production:/home/james/ssh-backdoor$**

### + 15 What's the user flag?
Answer: thm{d119b4fa8c497ddb0525f7ad200e6567}

Hint: go to home directory

###  + 15 What's the root flag?
Answer: thm{d53b2684f169360bb9606c333873144d}

Hint: run the command "ls -la " and you'll see SUID set for a file. However run it with "-p" flag which preserve the EUID of the binary, which is root.
