#Bandit Level 20 → Level 21
There is a setuid binary in the homedirectory that does the following:
it makes a connection to localhost on the port you specify as a commandline argument.
It then reads a line of text from the connection and compares it to the password in the previous level (bandit20).
If the password is correct, it will transmit the password for the next level (bandit21).
NOTE: Try connecting to your own network daemon to see if it works as you think
  (echo "0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO"; cat) | nc -l -p 12345
  创建一个监听端口的服务端，在连接建立时自动发送密码，并保持连接不中断，以便你可以进行后续的交互

  (echo "..."; cat)，这是一个子外壳（Subshell），它把两个命令的输出合并成一个连续的流
  echo "0qX..." 连接一旦建立，首先把密码发过去
  ; 代表顺序执行，在echo执行完后，立即执行cat
  cat 当cat后面不跟文件名时，它会读取标准输入（stdin）
    如果只用echo "..." | nc ，echo发完字符串就结束了，管道会关闭，nc也会随之断开
    它的作用：它像一个占位符，让管道一直开着。这样不仅能发送密码，还能在终端输入内容传给nc，
            或者接收并看到nc传回来的下一关密码
  
  Netcat部分，nc -l -p 12345
  nc(Netcat)，用于读写网络连接工具
  -l(Listen)，告诉nc进入监听模式，把自己变成一个服务端（Server），等别人来连
  -p，指定端口
  &，如果你在末尾加上 &，命令会在后台运行，这样就可以在同一个终端窗口继续操作了

#Bandit Level 21 → Level 22
A program is running automatically at regular intervals from cron, the time-based job scheduler.
Look in /etc/cron.d/ for the configuration and see what command is being executed.


#Bandit Level 22 → Level 23
A program is running automatically at regular intervals from cron, the time-based job scheduler.
Look in /etc/cron.d/ for the configuration and see what command is being executed.
NOTE: Looking at shell scripts written by other people is a very useful skill.
The script for this level is intentionally made easy to read.
If you are having problems understanding what it does, try executing it to see the debug information it prints.


#Bandit Level 23 → Level 24
A program is running automatically at regular intervals from cron, the time-based job scheduler.
Look in /etc/cron.d/ for the configuration and see what command is being executed.
NOTE: This level requires you to create your own first shell-script.
This is a very big step and you should be proud of yourself when you beat this level!
NOTE 2: Keep in mind that your shell script is removed once executed,
so you may want to keep a copy around


#Bandit Level 24 → Level 25
A daemon is listening on port 30002 and will give you the password for bandit25
if given the password for bandit24 and a secret numeric 4-digit pincode.
There is no way to retrieve the pincode except by going through
all of the 10000 combinations, called brute-forcing.
You do not need to create new connections each time


#Bandit Level 25 → Level 26  iCi86ttT4KSNe1armKiwbQNmB3YJP3q4
Logging in to bandit26 from bandit25 should be fairly easy
The shell for user bandit26 is not /bin/bash, but something else.
Find out what it is, how it works and how to break out of it.
NOTE: if you’re a Windows user and typically use Powershell to ssh into bandit:
Powershell is known to cause issues with the intended solution to this level.
You should use command prompt instead.


#Bandit Level 26 → Level 27
Good job getting a shell! Now hurry and grab the password for bandit27!


#Bandit Level 27 → Level 28
There is a git repository at ssh://bandit27-git@bandit.labs.overthewire.org/home/bandit27-git/repo via the port 2220.
The password for the user bandit27-git is the same as for the user bandit27.
From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level.
This needs git installed locally on your machine.


#Bandit Level 28 → Level 29
There is a git repository at ssh://bandit28-git@bandit.labs.overthewire.org/home/bandit28-git/repo via the port 2220.
The password for the user bandit28-git is the same as for the user bandit28.
From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level.
This needs git installed locally on your machine.


#Bandit Level 29 → Level 30
There is a git repository at ssh://bandit29-git@bandit.labs.overthewire.org/home/bandit29-git/repo via the port 2220.
The password for the user bandit29-git is the same as for the user bandit29.
From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level.
This needs git installed locally on your machine.


#Bandit Level 30 → Level 31
There is a git repository at ssh://bandit30-git@bandit.labs.overthewire.org/home/bandit30-git/repo via the port 2220.
The password for the user bandit30-git is the same as for the user bandit30.
From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level.
This needs git installed locally on your machine.


#Bandit Level 31 → Level 32
There is a git repository at ssh://bandit31-git@bandit.labs.overthewire.org/home/bandit31-git/repo via the port 2220.
The password for the user bandit31-git is the same as for the user bandit31.
From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level.
This needs git installed locally on your machine.


#Bandit Level 32 → Level 33
After all this git stuff, it’s time for another escape. Good luck!
