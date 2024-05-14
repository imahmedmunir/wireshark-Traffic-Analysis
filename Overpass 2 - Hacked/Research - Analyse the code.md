## This part was very interesting specilly to crack the hash and find the password

### What's the default hash for the backdoor?
Answer: bdd04d9bb7621687f5df9001f5098eb22bf19eac4c2c30b6f23efed4d24807277d0f8bfccb9e77659103d78c56e66d2d7d8391dfc885d0e9b68acd01fc2170e3

Solution: you can clone the git repository which you read in previous task. you'll see file written in go language "main.go"
Read the coding and see you can see the default hash

### What's the hardcoded salt for the backdoor?
Answer: 1c362db832f3f864c8c2fe05f2002a05

Solution: it was also in the last of "main.go" file , as question itself indicates "hardcoded"

### What was the hash that the attacker used? - go back to the PCAP for this!
Answer: 6d05358f090eea56a238af02e47d44ee5489d234810ef6240280857ec69712a3e5e370b8a41899d0196ade16c0d54327c5654019292cbfe0b5e98ad1fec71bed

Hint: go back to upload.php and see how the attacker runs ss_backdoor. Before hash he uses "-a"

### Crack the hash using rockyou and a cracking tool of your choice. What's the password?
Answer: november16

Solution: this was very interesting question
You've the hash of the attacker which he used while running ssh_backdoor. But it won't work out as their is trick here. When you went to check on "main.go" file, 
you found that whatever hash is being used, it's being salted. Now question arise which salt? Same salt which is hard coded in "main.go".
So, save the hash of the attacker and salt from "main.go" into a new file like password.txt. After that know the type of hash it is and run the command accordingly.

**hashid -m password.txt                                                                                                                            
--File 'password.txt'--
Analyzing '6d05358f090eea56a238af02e47d44ee5489d234810ef6240280857ec69712a3e5e370b8a41899d0196ade16c0d54327c5654019292cbfe0b5e98ad1fec71bed:1c362db832f3f864c8c2fe05f2002a05'
[+] SHA-512 [Hashcat Mode: 1700]
[+] Whirlpool [Hashcat Mode: 6100]**

From this you can see that hash identified as **sha512** but as we know we've also attached the salt. 
now [hashcat hash list](https://hashcat.net/wiki/doku.php?id=example_hashes) to check the mode number of sha512 with salt, which is 1710.

**─(root㉿kali)-[~/Desktop]
└─# hashcat -m 1710 -o cracked.txt password.txt /root/Desktop/wordlists/rockyou.txt
hashcat (v6.2.6) starting**

**(root㉿kali)-[~/Desktop]
└─# cat cracked.txt 
6d05358f090eea56a238af02e47d44ee5489d234810ef6240280857ec69712a3e5e370b8a41899d0196ade16c0d54327c5654019292cbfe0b5e98ad1fec71bed:1c362db832f3f864c8c2fe05f2002a05:november16**
