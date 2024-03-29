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
- man -k
- apropos – 显示一系列适合的命令
- info – 显示命令 info
- whatis – 显示一个命令的简洁描述
- alias – 创建命令别名
- help 查看shell命令列表
- alias foo='cd /usr; ls; cd -' 创建别名
- unaliase foo 删除别名
  
## 重定向

- \>
- \>\>  添加至文件末尾
- 2>&1  标准错误重定向
- &> 重定向标准输出标准错误
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
- echo $((expr)) 算数表达式
- echo {a,b,c}
- echo {1..5}
- echo {A{1,2},B{3,4}}
- ls -l $(which cp)
- ls -l \`which cp\`
- 双引号禁止分词展开 单引号禁止所有展开
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

## 键盘操作

| 按键          | 行动                                                                   |
| ------------- | ---------------------------------------------------------------------- |
| Ctrl-a        | 移动光标到行首。                                                       |
| Ctrl-e        | 移动光标到行尾。                                                       |
| opt-⬅️        | 光标前移一个字。                                                       |
| opt-➡️        | 光标后移一个字。                                                       |
| opt-鼠标左键  | 移动光标。                                                             |
| Ctrl-l        | 清空屏幕，移动光标到左上角。clear 命令完成同样的工作。                 |
| Ctrl-k        | 剪切从光标位置到行尾的文本。                                           |
| Ctrl-u        | 剪切从光标位置到行首的文本。                                           |
| Alt-d         | 剪切从光标位置到词尾的文本。                                           |
| Alt-Backspace | 剪切从光标位置到词头的文本。如果光标在一个单词的开头，剪切前一个单词。 |
| Ctrl-y        | 把剪切环中的文本粘贴到光标位置。                                       |

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
- kill 按pid
- killall 按程序名
- shutdown

## sehll环境

- printenv | less
- echo $PATH
- alias
- export
- source .bashrc

## Vim

- :q
- :q!
- u 撤销操作 U ctrl+r
- ^ 移动到当前行的第一个非空字符。
- $ 移动到当前行的末尾。
- w 移动到下一个单词或标点符号的开头。
- W 移动到下一个单词的开头，忽略标点符号。
- b 移动到上一个单词或标点符号的开头。
- B 移动到上一个单词的开头，忽略标点符号。
- 0 w W b B e E ^ $
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
- grep -nr 'text'

| 测试条件       | 描述                                                                                                                                                                                     |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -cmin n        | 匹配内容或属性最后修改时间正好在 n 分钟之前的文件或目录。 指定少于 n 分钟之前，使用 -n，指定多于 n 分钟之前，使用 +n。                                                                   |
| -cnewer file   | 匹配内容或属性最后修改时间晚于 file 的文件或目录。                                                                                                                                       |
| -ctime n       | 匹配内容和属性最后修改时间在 n*24小时之前的文件和目录。                                                                                                                                  |
| -empty         | 匹配空文件和目录。                                                                                                                                                                       |
| -group name    | 匹配属于一个组的文件或目录。组可以用组名或组 ID 来表示。                                                                                                                                 |
| -iname pattern | 就像-name 测试条件，但是不区分大小写。                                                                                                                                                   |
| -inum n        | 匹配 inode 号是 n的文件。这对于找到某个特殊 inode 的所有硬链接很有帮助。                                                                                                                 |
| -mmin n        | 匹配内容被修改于 n 分钟之前的文件或目录。                                                                                                                                                |
| -mtime n       | 匹配的文件或目录的内容被修改于 n*24小时之前。                                                                                                                                            |
| -name pattern  | 用指定的通配符模式匹配的文件和目录。                                                                                                                                                     |
| -newer file    | 匹配内容晚于指定的文件的文件和目录。这在编写执行备份的 shell 脚本的时候很有帮。 每次你制作一个备份，更新文件（比如说日志），然后使用 find 命令来判断哪些文件自从上一次更新之后被更改了。 |
| -nouser        | 匹配不属于一个有效用户的文件和目录。这可以用来查找 属于被删除的帐户的文件或监测攻击行为。                                                                                                |
| -nogroup       | 匹配不属于一个有效的组的文件和目录。                                                                                                                                                     |
| -perm mode     | 匹配权限已经设置为指定的 mode的文件或目录。mode 可以用 八进制或符号表示法。                                                                                                              |
| -samefile name | 类似于-inum 测试条件。匹配和文件 name 享有同样 inode 号的文件。                                                                                                                          |
| -size n        | 匹配大小为 n 的文件                                                                                                                                                                      |
| -type c        | 匹配文件类型是 c 的文件。                                                                                                                                                                |
| -user name     | 匹配属于某个用户的文件或目录。这个用户可以通过用户名或用户 ID 来表示。                                                                                                                   |

---

| 操作符 | 描述                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -and   | 如果操作符两边的测试条件都是真，则匹配。可以简写为 -a。 注意若没有使用操作符，则默认使用 -and。                                                                                                                                                                                                                                                                                                                      |
| -or    | 若操作符两边的任一个测试条件为真，则匹配。可以简写为 -o。                                                                                                                                                                                                                                                                                                                                                            |
| -not   | 若操作符后面的测试条件是假，则匹配。可以简写为一个感叹号（!）。                                                                                                                                                                                                                                                                                                                                                      |
| ()     | 把测试条件和操作符组合起来形成更大的表达式。这用来控制逻辑计算的优先级。 默认情况下，find 命令按照从左到右的顺序计算。经常有必要重写默认的求值顺序，以得到期望的结果。 即使没有必要，有时候包括组合起来的字符，对提高命令的可读性是很有帮助的。注意 因为圆括号字符对于 shell 来说有特殊含义，所以在命令行中使用它们的时候，它们必须 用引号引起来，才能作为实参传递给 find 命令。通常反斜杠字符被用来转义圆括号字符。 |

---

| 操作    | 描述                                                                      |
| ------- | ------------------------------------------------------------------------- |
| -delete | 删除当前匹配的文件。                                                      |
| -ls     | 对匹配的文件执行等同的 ls -dils 命令。并将结果发送到标准输出。            |
| -print  | 把匹配文件的全路径名输送到标准输出。如果没有指定其它操作，这是 默认操作。 |
| -quit   | 一旦找到一个匹配，退出。                                                  |
| -exec   | 执行自定义操作。                                                          |

## 压缩归档

- gzip gunzip 压缩 解压
- ls -l /etc | gzip > foo.txt.gz
- gunzip -c foo.txt.gz | less
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
- cut 抽取文本列，paste 合并文本列
- cut -f 3 distros.txt | cut -c 7-10
- aspell 拼写检查
- sed -n '2,3s/regexp/replacement/g'

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

## 特殊变量

- $0 - 脚本名
- $1 到 $9 - 脚本的参数。 $1 是第一个参数，依此类推。
- $@ - 所有参数
- $# - 参数个数
- $? - 前一个命令的返回值
- \$$ - 当前脚本的进程识别码
- !! - 完整的上一条命令，包括参数。常见应用：当你因为权限不足执行命令失败时，可以使用 sudo !!再尝试一次。
- $_ - 上一条命令的最后一个参数。如果你正在使用的是交互式 shell，你可以通过按下 Esc 之后键入 . 来获取这个值。
- $(cmd) - 执行命令 cmd 并返回其输出。这是一个命令替换的例子，它的作用和反引号是一样的。
- <(cmd) - 执行命令 cmd 并返回一个文件描述符，这个文件描述符指向一个临时文件，这个文件包含了命令 cmd 的输出。这个特性在 Bash 4.0 中被引入
- [[ ]与\[[ \]]差别](http://mywiki.wooledge.org/BashFAQ/031)
- 查看[]语法  man test

## 工具

- man tldr
- find fd locate
- [grep ack ag rg](https://beyondgrep.com/feature-comparison/)

## vim

- u U ctrl+r 撤销
- a A o O
- motion
  - 0 行首
  - ^ $
  - w W
  - b B
  - e E
  - G
  - gg
- operator
  - d 删除
  - c 删除+插入模式
  - y 复制
  - p P 黏贴
  - r 替换字符
  - x 删除字符
- 查询 / ?
- ctrl+o ctrl+i 前进 后退
- % 括号匹配
- ctrl+g 查询位置
- :r filename 插入文件
- :r !cmd 插入命令执行结果
- :w filename 写入文件
