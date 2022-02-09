#

## simple commands

- df 查看磁盘剩余
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
