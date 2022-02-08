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
