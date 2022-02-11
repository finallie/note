#

## simple commands

- df 查看磁盘剩余
- du -sh 查看文件夹大小
- free 查看内存
- exit 退出窗口
- printenv 环境变量

## 文件系统

- cd ls ll pwd
- cd 更改工作目录到你的家目录。
- cd - 更改工作目录到先前的工作目录。
- cd ~user_name 更改工作目录到用户家目录
- file 查看文件格式
- less 查看文本内容
- mkdir
- cp mv rm
- ln file link 创造硬链接
- ln -s item link 创造符号链接

## 命令

- type – 说明一个命令名是如何被解释的

> 命令4种类别
>
> 1. 程序
> 2. shell内部命令
> 3. shell函数
> 4. 别名

- which – 显示会执行哪个可执行程序
- man – 显示命令手册页
- apropos – 显示一系列适合的命令
- info – 显示命令 info
- whatis – 显示一个命令的简洁描述
- alias – 创建命令别名
- help 查看shell命令列表
- alias foo='cd /usr; ls; cd -' 创建别名
- unaliase foo 删除别名
  
## 重定向

- \>
- \>\>
- 2>&1
- &>
- \> /dev/null
- cat
- cat < in.txt
- sort | uniq
- wc -l -w -c
- grep -i -v
- tail -f
- tee
- echo *
- echo ~
- echo ~foo
- echo $((expr))
- echo {a,b,c}
- echo {1..5}
- echo {A{1,2},B{3,4}}
- ls -l $(which cp)
- <
- << _EOF_
- <<- _EOF_
- <<<strings

```bash
[me@linuxbox ~]$ echo text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER
text /home/me/ls-output.txt a b foo 4 me
[me@linuxbox ~]$ echo "text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER"
text ~/*.txt   {a,b} foo 4 me
[me@linuxbox ~]$ echo 'text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER'
text ~/*.txt  {a,b} $(echo foo) $((2+2)) $USER
```

## 权限

- id
- chmod
- umask
- su
- sudo
- chown
- chgrp
- passwd

## 进程

- ps aux
- top
- jobs
- bg
- fg
- kill
- killall
-shutdown

## sehll环境

- printenv | less
- echo $PATH
- alias
- export
- source .bashrc

## Vim

- :q
- :q!
- ^ 移动到当前行的第一个非空字符。
- $ 移动到当前行的末尾。
- w 移动到下一个单词或标点符号的开头。
- W 移动到下一个单词的开头，忽略标点符号。
- b 移动到上一个单词或标点符号的开头。
- B 移动到上一个单词的开头，忽略标点符号。
- numberG 移动到第 number 行。例如，1G 移动到文件的第一行。
- G 移动到文件末尾
- A 行末插入
- o 当前行的下方另起一行。
- O 当前行的上方另起一行。

### 删除

- x 当前字符
- 3x 当前字符及其后的两个字符。
- dd 当前行。
- 5dd 当前行及随后的四行文本。
- dW 从光标位置开始到下一个单词的开头。
- d$ 从光标位置开始到当前行的行尾。
- d0 从光标位置开始到当前行的行首。
- d^ 从光标位置开始到文本行的第一个非空字符。
- dG 从当前行到文件的末尾。
- d20G 从当前行到文件的第20行。

### 复制黏贴

- 黏贴 p 光标后 P 光标前
- y 复制 用法与删除d类似
- J 链接行
- /Line 查询
- n 执行上次查询
- :%s/line/Line/gc
  - % 操作范围
  - s 指定操作替换
  - /line/Line 替换文本
  - g 全局
  - c 用户确认
- :buffers :buffer1 多文件操作

## 软件包管理

- debian apt
- red-hat yum

## 网络

- ping
- traceroute
- netstat
- ftp
- ssh
- scp

## 文件搜索

- locate (不推荐用 用find替换)
- find -type -name
- xargs
- grep -l bzip dirlist*.txt 查询包含bzip的文件名

## 压缩归档

- gzip gunzip 压缩 解压
- ls -l /etc | gzip > foo.txt.gz
- zcat zless
- bzip2 bunzip2 bzcat bzless 压缩程度高 耗时长
- tar cf 创建归档 czf 用gzip压缩 cjf 用bzip2压缩
- tar tf 查看
- tar xf 解压
- find playground -name 'file-A' | tar cf - --files-from=-
   | gzip > playground.tgz
- zip 用于和windows系统交换文件
- alias backup='sudo rsync -av --delete /etc /home /usr/local /media/BigDisk/backup'

## 文本处理

- cat -A
- cat -ns
- sort -t ':' -nr -k 5

```bash
[me@linuxbox ~]$ sort -k 3.7nbr -k 3.1nbr -k 3.4nbr distros.txt
Fedora         10    11/25/2008
Ubuntu         8.10  10/30/2008
SUSE           11.0  06/19/2008
```

- uniq
- cut paste join
- aspell 拼写检查

## 格式化输出

- nl 输出带行数
- fold -w 12 -s 限制行宽

## 脚本

```block
if commands; then
     commands
[elif commands; then
     commands...]
[else
     commands]
fi

while commands; do commands; done

case word in
    [pattern [| pattern]...) commands ;;[&]]...
esac
a) 若单词为 “a”，则匹配
[[:alpha:]]) 若单词是一个字母字符，则匹配
???) 若单词只有3个字符，则匹配
*.txt) 若单词以 “.txt” 字符结尾，则匹配
*) 匹配任意单词。把这个模式做为 case 命令的最后一个模式，是一个很好的做法， 可以捕捉到任意一个与先前模式不匹配的数值；也就是说，捕捉到任何可能的无效值。

;;& 允许 case 语句继续执行下一条测试，而不是简单地终止运行。

for i in A B C D; do echo $i; done
for i in {A..D}; do echo $i; done
for i ; do echo $i; done  # i指参数
```

```block
测试文件表达式
-b file file 存在并且是一个块（设备）文件。
-c file file 存在并且是一个字符（设备）文件。
-d file file 存在并且是一个目录。
-e file file 存在。
-f file file 存在并且是一个普通文件。
-g file file 存在并且设置了组 ID。
-G file file 存在并且由有效组 ID 拥有。
-k file file 存在并且设置了它的“sticky bit”。
-L file file 存在并且是一个符号链接。
-O file file 存在并且由有效用户 ID 拥有。
-p file file 存在并且是一个命名管道。
-r file file 存在并且可读（有效用户有可读权限）。
-s file file 存在且其长度大于零。
-S file file 存在且是一个网络 socket。
-t fd fd 是一个定向到终端／从终端定向的文件描述符 。 这可以被用来决定是否重定向了标准输入／输出错误。
-u file file 存在并且设置了 setuid 位。
-w file file 存在并且可写（有效用户拥有可写权限）。
-x file file 存在并且可执行（有效用户有执行／搜索权限）。
```

```block
测试字符串表达式
string string is not null.
-n string The length of string is greater than zero.
-z string The length of string is zero.
string1 = string2
string1 == string2
string1 and string2 are equal. Single or double equal signs may be used, but the use of double equal signs is greatly preferred.
string1 != string2 string1 and string2 are not equal.
string1 > string2 sting1 sorts after string2.
string1 < string2 string1 sorts before string2.
```

```block
测试整数表达式
integer1 -eq integer2 integer1 等于 integer2。
integer1 -ne integer2 integer1 不等于 integer2。
integer1 -le integer2 integer1 小于或等于 integer2。
integer1 -lt integer2 integer1 小于 integer2。
integer1 -ge integer2 integer1 大于或等于 integer2。
integer1 -gt integer2 integer1 大于 integer2。
```

```block
[[ ]]表达式
[[string1 =~ regex]]正则表达式
[[ $FILE == foo.* ]] 文件路径展开
```

```block
(( ))表达式
```

```block
从键盘读取输入
read
-a array 把输入赋值到数组 array 中
-d delimiter 用字符串 delimiter 中的第一个字符指示输入结束，而不是一个换行符。
-e 使用 Readline 来处理输入。这使得与命令行相同的方式编辑输入。
-n num 读取 num 个输入字符，而不是整行。
-p prompt 为输入显示提示信息，使用字符串 prompt。
-r Raw mode. 不把反斜杠字符解释为转义字符。
-s Silent mode. 不会在屏幕上显示输入的字符。当输入密码和其它确认信息的时候，这会很有帮助。
-t seconds 超时. 几秒钟后终止输入。若输入超时，read 会返回一个非零退出状态。
-u fd 使用文件描述符 fd 中的输入，而不是标准输入。

IFS=":" read user pw uid gid name home shell <<< "$file_info"

read不能接受管道作为输入
```

```block
#!/bin/bash -x
export PS4='$LINENO + '】
set -x set +x
脚本调试
```

## 参数展开

- $a
- ${a}
- ${11}
- ${parameter:-word}
- ${parameter:=word} 空则赋值
- ${parameter:?word}
- ${parameter:+word}
- ${!prefix*} ${!prefix@}
- ${#parameter} 参数长度
- ${parameter:offset} ${parameter:offset:length} 截取
- ${parameter#pattern} ${parameter##pattern} 去除开头
- ${parameter%pattern} ${parameter%%pattern} 去除末尾
- ${parameter/pattern/string} ${parameter//pattern/string} ${parameter/#pattern/string} ${parameter/%pattern/string} 替换
- ${parameter,,}  把 parameter 的值全部展开成小写字母。
- ${parameter,} 仅仅把 parameter 的第一个字符展开成小写字母。
- ${parameter^^} 把 parameter 的值全部转换成大写字母。
- ${parameter^} 仅仅把 parameter 的第一个字符转换成大写字母（首字母大写）。

## 其他

```block
{ ls -l; echo "Listing of foo.txt"; cat foo.txt; } > output.txt
{ ls -l; echo "Listing of foo.txt"; cat foo.txt; } | lpr
```
