#Bandit Level 10 → Level 11
The password for the next level is stored in the file data.txt, which contains base64 encoded data
base64 -d data.txt

#Bandit Level 11 → Level 12
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

这是一个经典的 ROT13（Rotate by 13 places）加密问题。它是凯撒密码的一种特殊形式，通过将字母表向前推进 13 位来替换字母。
因为英文字母表总共有 26 个字母，所以 ROT13 是对称的：对加密后的文本再执行一次 ROT13 就能得到原始明文

cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m' | awk '{print $4}'

tr：用于转换或删除字符。
'A-Za-z'：定义了搜索范围（源字符集）。
'N-ZA-Mn-za-m'：定义了替换目标。
A 对应 N
B 对应 O
以此类推，当到达 M 时，对应 Z；接着 N 回到 A。

#Bandit Level 12 → Level 13
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed.
For this level it may be useful to create a directory under /tmp in which you can work.
Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”.
Then copy the datafile using cp, and rename it using mv (read the manpages!)
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv, file
workdir=$(mktemp -d)
cd $workdir
file data.bin
mv data.bin data.bin.gz
gunzip data.bin.gz
bunzip2 data.bin.bz2
tar -xf data.bin

#Bandit Level 13 → Level 14
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14.
For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level.
Look at the commands that logged you into previous bandit levels, and find out how to use the key for this level.
ssh, scp, umask, chmod, cat, nc, install
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220

#Bandit Level 14 → Level 15
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.
ssh, telnet, nc, openssl, s_client, nmap
cat /etc/bandit_pass/bandit14 | nc localhost 30000

#Bandit Level 15 → Level 16
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.
Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.
ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss
openssl s_client -connect localhost:30001
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

#Bandit Level 16 → Level 17
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000.
First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t.
There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.
Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.
nmap -p 31000-32000 localhost
echo "kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx" | openssl s_client -connect localhost:31790 -quiet > $workdir/keyfile 2>/dev/null
sed -i '/-----BEGIN RSA PRIVATE KEY-----/,$!d' $workdir/keyfile
scp -P 2220 bandit16@bandit.labs.overthewire.org:/tmp/tmp.R136LnxKHp/keyfile .
ssh -i keyfile bandit17@bandit.labs.overthewire.org -p 2220

#Bandit Level 17 → Level 18
There are 2 files in the homedirectory: passwords.old and passwords.new.
The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new
NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19
diff password.new password.old

#Bandit Level 18 → Level 19
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"

#Bandit Level 19 → Level 20
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it.
The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.
./bandit-20 cat /etc/bandit_pass/bandit20
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO