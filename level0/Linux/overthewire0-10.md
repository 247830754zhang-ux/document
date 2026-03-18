#Bandit Level 0 → Level 1
The password for the next level is stored in a file called readme located in the home directory.
Use this password to log into bandit1 using SSH.
Whenever you find a password for a level,
use SSH (on port 2220) to log into that level and continue the game.
ssh bandit0@bandit.labs.overthewire.org -p 2220
password:bandit0
ls , cd , cat , file , du , find
ls [OPTION]... [FILE]...
cd [-L|-P] [directory]
cat [OPTION]... [FILE]...
file  [-bcdEhiklLNnprsSvzZ0]  [--apple]  [--exclude-quiet]  [--extension] [--mime-encoding] [--mime-type]
[-e testname] [-F separator] [-f namefile] [-m magicfiles] [-P name=value] file ...
file -C [-m magicfiles]
file [--help]
du [OPTION]... [FILE]...
du [OPTION]... --files0-from=F
find [-H] [-L] [-P] [-D debugopts] [-Olevel] [starting-point...] [expression]

#Bandit Level 1 → Level 2
The password for the next level is stored in a file called - located in the home directory
"-" 在命令行里表示标准输入，cat - 意思是从键盘输入，然后打印
cat ./-  表示当前文件夹下的-文件

#Bandit Level 2 → Level 3
The password for the next level is stored in a file called --spaces in this filename-- located in the home directory


#Bandit Level 3 → Level 4
The password for the next level is stored in a hidden file in the inhere directory.


#Bandit Level 4 → Level 5
The password for the next level is stored in the only human-readable file in the inhere directory.
Tip: if your terminal is messed up, try the “reset” command.
file inhere/* | grep "ASCII text" | cut -d: -f1 | xargs -I {} cat "{}"

#Bandit Level 5 → Level 6
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
human-readable
1033 bytes in size
not executable
find . -size 1033c ! -executable | xargs cat
-exec cat \;
-exec cat +
-print0 | xargs -0 cat

#Bandit Level 6 → Level 7
The password for the next level is stored somewhere on the server and has all of the following properties:
owned by user bandit7
owned by group bandit6
33 bytes in size
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
0 -> 键盘输入
1 -> 正常输出
2 -> 错误输出
/dev/null -> 文件黑洞，类似垃圾桶。写入它的任何数据都会立即消失，无法读取

grep [OPTION...] PATTERNS [FILE...]
grep [OPTION...] -e PATTERNS ... [FILE...]
grep [OPTION...] -f PATTERN_FILE ... [FILE...]

#Bandit Level 7 → Level 8
The password for the next level is stored in the file data.txt next to the word millionth
grep "millionth" data.txt | awk '{print $2}'

# 基本结构
awk 'pattern {action}' file

# 常用模式
NR==1          # 第一行
NR>10          # 10 行之后
$1=="text"     # 第一列匹配
/regex/        # 正则匹配
$2 > 100       # 数值比较

# 常用动作
print          # 打印整行
print $1       # 打印第一列
print $1,$3    # 打印多列
length($0)     # 行长度
toupper($1)    # 转大写
tolower($1)    # 转小写

man, grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd
man [man options] [[section] page ...] ...
man -k [apropos options] regexp ...
man -K [man options] [section] term ...
man -f [whatis options] page ...
man -l [man options] file ...
man -w|-W [man options] page ...


#Bandit Level 8 → Level 9
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd
sort data.txt | uniq -u


#Bandit Level 9 → Level 10
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd
strings data.txt | grep "="
从二进制文件里提取 “可打印字符序列”