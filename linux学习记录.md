## 命令行快捷键

命令行中的ctrl组合键
Ctrl+c 结束正在运行的程序

Ctrl+d 结束输入或退出shell

Ctrl+s 暂停屏幕输出【锁住终端】

Ctrl+q 恢复屏幕输出【解锁终端】

Ctrl+l 清屏，【是字母L的小写】等同于Clear

当前光标到行首：ctrl+a

当前光标到行尾：ctrl+e

删除当前光标到行首：ctrl+u

删除当前光标到行尾：ctrl+k

Ctrl+y 在光标处粘贴剪切的内容

Ctrl+r 查找历史命令【输入关键字，就能调出以前执行过的命令】

Ctrl+t 调换光标所在处与其之前字符位置，并把光标移到下个字符

Ctrl+x+u 撤销操作

**Ctrl+左右方向键 #跳转单词**

# 大纲![image-20240722193620967](linux学习记录.assets/image-20240722193620967.png)

![image-20240722193705448](linux学习记录.assets/image-20240722193705448.png)

# 三种网络模式

![image-20240722200057453](linux学习记录.assets/image-20240722200057453.png)

3.主机模式：独 立系统

# 目录结构

 ![image-20240722200830726](linux学习记录.assets/image-20240722200830726.png)

![image-20240722201146401](linux学习记录.assets/image-20240722201146401.png)

![image-20240722201200954](linux学习记录.assets/image-20240722201200954.png)

 ![image-20240722201420306](linux学习记录.assets/image-20240722201420306.png)

# 关机重启

![image-20240722203146670](linux学习记录.assets/image-20240722203146670.png)

# 用户管理

## 添加用户

```
useradd (-d) 用户名
```

## 更改密码（不输入默认为root密码）

```
passwd 用户名
```

## 删除用户

```
userdel 用户名 （保留家目录）
userdel -r 用户名 （全删掉）
```

## 切换用户

```
su - 用户名
```

## 返回原来用户

```
logout
```

## 用户组

添加组（groupadd）

```
useradd -g 用户组 用户名
```

改变组

```
usermod -g 用户组 用户名
```

![image-20240722212451395](linux学习记录.assets/image-20240722212451395.png)

## 用户和相关文件

![image-20240722212607521](linux学习记录.assets/image-20240722212607521.png)

# 运行级别

![image-20240722214549826](linux学习记录.assets/image-20240722214549826.png)

# 时间日期

![image-20240722215045730](linux学习记录.assets/image-20240722215045730.png)

# 查找文件find

```
find path -option [ -print ] [ -exec -ok command ] {} \;
```

## 参数

```
常用参数说明 :
-perm xxx：权限为 xxx的文件或目录
-user： 按照文件属主来查找文件。
-size n : n单位,b:512位元组的区块,c:字元数,k:kilo bytes,w:二个位元组
-mount, -xdev : 只检查和指定目录在同一个文件系统下的文件，避免列出其它文件系统中的文件
-amin n : 在过去 n 分钟内被读取过
-anewer file : 比文件 file 更晚被读取过的文件
-atime n : 在过去n天内被读取过的文件
-cmin n : 在过去 n 分钟内被修改过
-cnewer file :比文件 file 更新的文件
-ctime n : 在过去n天内被修改过的文件
-empty : 空的文件
-gid n or -group name : gid 是 n 或是 group 名称是 name
-ipath p, -path p : 路径名称符合 p 的文件，ipath 会忽略大小写
-name name, -iname name : 文件名称符合 name 的文件。iname 会忽略大小写
-type 查找某一类型的文件：
    b - 块设备文件
    d - 目录
    c - 字符设备文件
    p - 管道文件
    l - 符号链接文件
    f - 普通文件
-exec 命令名{} \ (注意：“}”和“\”之间有空格)
```

## 例子

```
显示当前目录中大于20字节并以.c结尾的文件名
find . -name "*.c" -size +20c 

将目前目录其其下子目录中所有一般文件列出
find . -type f

将目前目录及其子目录下所有最近 20 天内更新过的文件列出
find . -ctime -20

查找/var/log目录中更改时间在7日以前的普通文件，并在删除之前询问它们：
find /var/log -type f -mtime +7 -ok rm {} \;

查找前目录中文件属主具有读、写权限，并且文件所属组的用户和其他用户具有读权限的文件：
find . -type f -perm 644 -exec ls -l {} \;

查找系统中所有文件长度为0的普通文件，并列出它们的完整路径：
find / -type f -size 0 -exec ls -l {} \;

从根目录查找类型为符号链接的文件，并将其删除：
find / -type l -exec rm -rf {} \

从当前目录查找用户tom的所有文件并显示在屏幕上
find . -user tom

在当前目录中查找所有文件以.doc结尾，且更改时间在3天以上的文件，找到后删除，并且给出删除提示
find . -name *.doc  -mtime +3 -ok rm {} \;

在当前目录下查找所有链接文件，并且以长格式显示文件的基本信息
find . -type l -exec ls -l {} \;

在当前目录下查找文件名有一个小写字母、一个大写字母、两个数字组成，且扩展名为.doc的文件
find . -name '[a-z][A-Z][0-9][0-9].doc'
```

# 查找文件locate

运行之前冼运行一下，来建立locate数据库。然后查找文件比如hello.tet。（若无updatedb这可能搜索不到文件）

```
updatedb
locate hello.tet
```



# 查找历史记录history

显示n个

```
history -n 
```

执行第n个

```
！n
```

显示行号

```
num
```

**查找匹配的（CTRL R）**

```
输入  然后 enter执行
```

**.!+字符串 代表搜索历史命令最近一个以xxxx字符开头的命令**

```
[root@localhost ~]# cd /etc/sysconfig/network-scripts/
[root@localhost ~]# !cd
cd /etc/sysconfig/network-scripts/
```



# 文件编辑器vi

## 普通模式

前进/后退一页

```
CTRL f/b
```

前进/后退半页

```
CTRL u/d
```

删除（注意，删除时会将文本内容进行缓存，然后通过粘贴，实现剪切功能。）

```
x	删除光标处的一个字符
dd	删除光标处的所在行
ndd	删除从光标所在行开始的n行(包含光标行)，1dd等于dd
dw	删除从光标位置开始的一个单词
d$	删除从光标处到该行行尾的字符
d^	删除光标处到该行行首的字符
dG	删除光标行到行尾的所有行
dnG	删除从光标行到第n行(包含第n行)
```

复制

```
yy
```

粘贴

| 按键 |                          按键功能                          |
| ---- | :--------------------------------------------------------: |
| p    | 将复制的内容粘贴到光标所在行的下一行(小写，地位低，居下方) |
| P    | 将复制的内容粘贴到光标所在行的上一行(大写，地位高，居上方) |

替换

| 按键 | 按键功能                     |
| ---- | ---------------------------- |
| r    | 替换光标处的一个字符         |
| R    | 从光标处开始往后连续替换     |
| cc   | 替换光标所在行               |
| c$   | 替换光标处到该行行尾         |
| c^   | 替换光标处到该行行首         |
| cG   | 替换从光标行到行尾           |
| cnG  | 替换从光标行到第n行(包含n行) |

撤销

```
u
```

光标移动左下上右

```
hjkl
```

行首行尾

```
gg	文件首行的行首
GG	文件尾行的行首
```

查找(/加字符串)

```
/
```

字符串替换

```
:%s/old_string/new_string	全局替换
: s /old_string/new_string	替换光标所在行
: n, $s /old_string/new_string	替换第 n行开始到最后一行中的第一个old_string
: n,$s /old_string/new_string/g	替换第n行开始到最后一行的所有old_string
```

##  可视模式

v	每次选择一个字符
V	每次选择一行
gv	重选上一次的高亮区
选中后，按下d	删除所选中部分
选中后，按下D	删除所选中部分所在的行
选中后，按下v	复制选中的部分
选中后，按下V	复制所选中部分的所在行
选中后，按下c或C	删除所选中部分(选中部分所在行)，并切换到输入模式
选中后，按下J	将选中部分合并为一行
选中后，按下r	将选中的部分的每个字符替换为新字符



# PS：如何将 Vim 剪贴板里面的东西粘贴到 Vim 之外的地方

### 问题描述

在笔记本电脑上使用linux系统，经常打开并编辑一些文本文件，我比较喜欢用vim。但有时候遇到要从文件中拷贝几个数据到文件外(比如excel, 或者google spreadsheets)的时候，我就遇到麻烦了。在vim里面用**y**拷贝的东西，没法粘贴到文件外。因此我每次需要拷贝数据的时候，都是换gedit来操作。直到今天，我由于需要从三个文件中拷贝一共十八个数据，忍不了了。

### 解决方法

还好，已经有大佬帮我解决了这个\[问题\](如何将 Vim 剪贴板里面的东西粘贴到 Vim 之外的地方？ - cnlzxin的回答 - 知乎  
[https://www.zhihu.com/question/19863631/answer/182346296)。](https://www.zhihu.com/question/19863631/answer/182346296)%E3%80%82)

-   检查vim是否支持clipboard功能:
    
    <table><tbody><tr><td><pre><span>1</span><br></pre></td><td><pre><span>vim --version | grep clipboard</span><br></pre></td></tr></tbody></table>
    
-   如果有 **+clipboard** 则跳过这一步; 如果显示的是 **\-clipboard** 说明不支持(很遗憾，我的就是 **\-clipboard**), 需要
    
    ```
    sudo apt install vim-gtk
    ```

安装好vim -gtk之后就可以了。复制内容到vim外了。不过在vim内复制内容时，需要制定将内容复制到 **clipboard**，通过 **“+** 来指定特定寄存器。

### 例子

当我想复制一个数据到spreadsheets时，使用**v**选中该数据内容，然后 **“+y**，切换到spreadsheets，**ctrl + v** 即可。想把剪切板的内容复制到另一个vim文件时，使用`"+p`即可。



## 压缩与解压文件

## 1.zip和unzip

压缩

将home下的文件压缩成hello.zip

```
zip -r hello.zip  /home/
```

解压缩

将hello.zip解压缩到指定目录/opt/temp

```
unzip /home/hello.zip -d /opt/temp
```

## 2.tar

```
tar [选项] 文件名.tar.gz 源文件
-c --create ：创建新的归档文件，即打包，打包的意思就是说把一堆文件打包成一个文件
-x --extract ：解压文件
-v --verbose ：可视化，显示详细的tar处理的文件信息的过程
-f --file ：要操作的文件名
-z --gzip, --gunzip, --ungzip ：通过 gzip 来进行归档压缩,如 tar -czvf etc.tar.gz /etc/,解压使用tar -zxvf test.tar.gz
-j --bzip2 ：通过 bzip2 来归档压缩文件，如 tar -jcvf test.tar.bz2 /etc/,解压使用tar -jxvf test.tar.bz2
-J :使用xz压缩工具压缩成.xz文件,如 tar -Jcvf test.tar.xz /etc/,解压使用tar -Jxvf test.tar.xz
-t --list ：表示查看文件，查看文件中的文件内容
-C --directory=DIR ：解压文件至指定的目录，如果是解压到当前目录，可以不加-C
```

压缩

```
#将dir1文件夹压缩成dir1.tar.gz
tar -zcvf dir1.tar.gz dir1/
#将dir1文件夹下所有的内容压缩成dir1.tar.gz
tar -zcvf dir1.tar.gz dir1/*
```


解压缩

```
#将dir1.tar.gz解压到dir1_copy目录下（前提是要自己创建dir1_copy目录。若当前目录中存在目录dir1，会替换覆盖目录中的同名文件）
tar -zxvf dir1.tar.gz -C dir1_copy/
```

# 文件所有者

改变文件所有者（改为tom所有者）

```
chown tom hello.tet
```

改变文件所属组

```
groupadd fruit
touch orange.tet(root创建为root组)
chgrp fruit orange.tet
```



# 在终端替换字符串

如果你是在命令行中直接替换字符串 `melody` 为 `noetic`，可以使用以下方法：

### 1. 使用 `echo` 和 `sed`
如果你有一个字符串，并希望在终端输出中将 `melody` 替换为 `noetic`，可以这样做：

```bash
echo "melody" | sed 's/melody/noetic/g'
```

这会输出替换后的字符串。

![image-20240827133848277](/home/sz/.config/Typora/typora-user-images/image-20240827133848277.png)

### 2. 使用参数替换（适用于变量）
如果字符串存储在一个变量中，你可以直接在 Bash 中使用参数替换：

```bash
my_string="melody"
new_string="${my_string/melody/noetic}"
echo $new_string
```

这会将 `my_string` 中的 `melody` 替换为 `noetic` 并存储在 `new_string` 中。

### 3. 历史命令替换
如果你想在历史命令中替换 `melody` 为 `noetic`，你可以使用历史替换功能：

```bash
!!:s/melody/noetic/
```

- `!!` 表示上一个命令。
- `:s/melody/noetic/` 表示将上一个命令中的 `melody` 替换为 `noetic`。

这个命令将执行替换后的新命令。



# Ubuntu软件操作的相关指令

```
sudo apt-cache show package 获取包的相关信息（如说明，大小，版本等）
sudo apt-get install package --reinstall 重新安装包
sudo apt-get remove package 删除安装包
sudo apt-get source package 下载该安装包的源码

```











