# 扩展一：Ubuntu日志清理/var/log/journal

![cover](Ubuntu的扩展学习.assets/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAU3RyYXdCYXJyeTE5OTc=,size_7,color_FFFFFF,t_70,g_se,x_16.png)

## Ubuntu日志清理/var/log/journal

Ubuntu虚拟机空间不足时，可以通过清除系统日志/var/log/journal来释放空间。

![](Ubuntu的扩展学习.assets/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAU3RyYXdCYXJyeTE5OTc=,size_20,color_FFFFFF,t_70,g_se,x_16.png)

查看/var/log中个文件大小

sudo du --max-depth=1 -h /var/log

/var/log/journal文件夹大小有2G

![](Ubuntu的扩展学习.assets/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAU3RyYXdCYXJyeTE5OTc=,size_7,color_FFFFFF,t_70,g_se,x_16.png)

cd /var/log/journal

![](Ubuntu的扩展学习.assets/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAU3RyYXdCYXJyeTE5OTc=,size_7,color_FFFFFF,t_70,g_se,x_16-171862750392331.png) 

直接删除，暂时解决

rm -rf /var/log/journal/88f08a5a995845578f49660b102c7a7d

再次查看

![](Ubuntu的扩展学习.assets/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAU3RyYXdCYXJyeTE5OTc=,size_7,color_FFFFFF,t_70,g_se,x_16-171862750392432.png)

**1）只保留近一周的日志**

journalctl --vacuum-time=1w

**2）只保留 500MB 的日志**

journalctl --vacuum-size=500M





# 扩展二：ipconfig

在Windows 10命令行中输入`ipconfig`命令可以显示当前网络适配器的配置信息。以下是`ipconfig`命令输出中各个参数的含义及其使用场景的生动形象解释：

1. **IPv4 地址（IPv4 Address）**：
   - **解释**：这是你电脑在网络中的“门牌号”，用于在本地网络中标识你的设备。
   - **场景**：在局域网中，例如在家里连接的Wi-Fi网络或公司内部网络中，其他设备可以通过这个地址与你的电脑通信。

2. **子网掩码（Subnet Mask）**：
   - **解释**：这是一个用来划分网络部分和主机部分的“面具”，帮助路由器判断数据包是发往本地网络还是外部网络。
   - **场景**：如果两个设备的IP地址和子网掩码相同，它们就在同一个子网中，可以直接通信。否则，需要通过路由器或其他网络设备来转发。

3. **默认网关（Default Gateway）**：
   - **解释**：这是你电脑访问外部网络的“出口”，通常是连接到外部互联网的路由器的IP地址。
   - **场景**：当你访问互联网时，你的请求会先发送到默认网关，由它负责把请求转发到互联网并将响应返回给你。

4. **DNS 服务器（DNS Servers）**：
   - **解释**：这是将域名转换为IP地址的“电话簿”服务，使你能够通过域名（如www.example.com）访问网站。
   - **场景**：当你在浏览器中输入一个网站的域名时，DNS服务器将这个域名转换为实际的IP地址，从而连接到对应的服务器。

5. **物理地址（Physical Address 或 MAC Address）**：
   - **解释**：这是网络适配器的唯一“身份证号”，用于局域网中的设备标识。
   - **场景**：在局域网中，路由器使用MAC地址来确定将数据包发送到哪个设备。这在网络管理和安全控制中非常重要，例如设置MAC地址过滤。

6. **链接本地IPv6地址（Link-local IPv6 Address）**：
   - **解释**：这是用于局部网络（如家庭网络或公司局域网）的IPv6地址，不用于互联网通信。
   - **场景**：在没有路由器的情况下，设备可以使用链接本地IPv6地址在同一网络中自动配置并通信。

7. **隧道适配器（Tunnel Adapter）**：
   - **解释**：这些适配器用于在IPv4和IPv6网络之间进行通信，是一种“桥梁”。
   - **场景**：如果你的网络使用IPv4地址，但你需要访问IPv6地址的资源，隧道适配器可以帮助进行这种转换和通信。

### 使用实例
假设你在命令行中输入`ipconfig`后看到如下输出：
```plaintext
Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::a00:27ff:fe4e:66a1%11
   IPv4 Address. . . . . . . . . . . : 192.168.1.2
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1

Wireless LAN adapter Wi-Fi:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::a123:b456:c789:d012%13
   IPv4 Address. . . . . . . . . . . : 192.168.1.4
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1

Ethernet adapter VirtualBox Host-Only Network:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::b00:c77:fe9a:bcde%14
   IPv4 Address. . . . . . . . . . . : 192.168.56.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :
```

### 解析
1. **Ethernet adapter Ethernet**:
   - **IPv4 Address**：192.168.1.2
     - 这是通过有线以太网连接的设备的IP地址。
   - **Subnet Mask**：255.255.255.0
     - 这是局域网的子网掩码。
   - **Default Gateway**：192.168.1.1
     - 这是路由器的IP地址，用于访问外部网络。

2. **Wireless LAN adapter Wi-Fi**:
   - **IPv4 Address**：192.168.1.4
     - 这是通过Wi-Fi连接的设备的IP地址。
   - **Subnet Mask**：255.255.255.0
     - 这是Wi-Fi网络的子网掩码。
   - **Default Gateway**：192.168.1.1
     - 这是Wi-Fi网络的默认网关。

3. **Ethernet adapter VirtualBox Host-Only Network**:
   - **IPv4 Address**：192.168.56.1
     - 这是VirtualBox虚拟机的虚拟网络接口的IP地址。
   - **Subnet Mask**：255.255.255.0
     - 这是虚拟网络的子网掩码。
   - **Default Gateway**：
     - 这个虚拟网络没有设置默认网关，因为它是一个仅限主机的网络，不需要访问外部网络。

通过`ipconfig`命令，你可以快速了解你的网络配置，解决连接问题，设置局域网，或者为网络调试提供帮助。这是网络管理和故障排除中的一个重要工具。



# 扩展三：配置双系统

自己电脑配置：

![image-20240711160426022](Ubuntu的扩展学习.assets/image-20240711160426022.png)





# 扩展四、Ubuntu常用命令

```
# Ctrl+Alt+T 打开新的终端
# Ctrl+shift+T 打开新的终端Tab
# Ctrl+shift+n 打开新的同目录的终端

clear # 清屏
clear --help # cmd --help:查看Linux命令的帮助，例如
sudo clear # 以管理员权限运行命令：sudo
history # 查看终端输入的所有历史命令

# 根目录：/，家目录：/home/zrad, ~
# cd ~ 回家，cd 打开文件夹
cd ~
cd Desktop
cd ..  # 返回上一级

pwd # 查看当前路径

# mkdir *** 创建文件夹
mkdir test_sh
cd /home/zard/test_sh
mkdir test test2
# 创建多级文件夹
mkdir -p test2/test3/test4

# 将文本写进tmp文件（覆盖）
echo "Ctrl+Alt+T 打开终端" > tmp
# 将文本写进tmp文件（追加）
echo "Ctrl+shift+T分开终端" >> tmp

cd test
# touch ****.*** 创建文件（如果存在只会更新创建时间）
touch test1.txt
mkdir test

ls  # ls 查看当前目录下所有文件及文件夹
ls -l # ls -l 查看当前目录下所有文件及文件夹并显示详细信息（字节为单位）
ls -a  # ls -a 查看当前目录下所有文件及文件夹(包括隐藏的)
ls -lh # ls -lh 查看当前目录下所有文件及文件夹并显示详细信息(单位kMGT)
# ll==ls -laf
ll
ls -lah
# ls ***:罗列路径下的所有文件及文件夹
ls /home/zard/test_sh

# tree：显示当前文件树结构 sudo apt-get install tree
tree

echo "rm **.**:移除文件"
echo "rm -r ***:移除文件夹"
echo "rm -f *** -r:移除文件夹及其下的所有文件"

cd /home/zard/test_sh/test/
touch test2.txt
echo "mv **.**/*** ***:移动文件夹/文件至***"
mv /home/zard/test_sh/test2 /home/zard/test_sh/test/test
mv /home/zard/test_sh/test/test2.txt /home/zard/test_sh/test/test

echo "cp **.**/*** ***:复制----------------"
cp /home/zard/test_sh/test2 /home/zard/test_sh/test/test -r
cp /home/zard/test_sh/test/test1.txt /home/zard/test_sh/test/test

# 压缩/解压缩文件
mkdir testcom
touch testcom testcom2
cd testcom && touch testcom testcom2
cd ..
tree
# c代表压缩，z代表使用gzip，v代表显示压缩日志，f代表指定压缩包名称，后面是要压缩的文件夹及文件
tar czvf all.tar.gz testcom testcom2 tmp
rm -f testcom testcom2 tmp -r
# x代表解压缩
tar xzvf all.tar.gz
# 解压缩到目录
mkdir all
tar xzvf all.tar.gz -C all
tree

# zip格式
# 安装压缩工具 sudo apt-get install zip uzip
zip -r all2 testcom testcom2 tmp
unzip all2
mkdir all3
unzip all2 -d all3

# LINUX查看进程
ps -elf
# -e：显示系统内的所有进程信息。
# -l：使用长（long）格式显示进程信息。
# -f：使用完整的（full）格式显示进程信息。
# 以全屏交互式的界面显示进程排名，及时跟踪包括CPU、内存等系统资源占用情况，默认情况下每三秒刷新一次，其作用基本类似于Windows系统中的任务管理器：
top
```



# 扩展五.实时显示当前的CPU，GPU，温度（工具--七）

一、添加indicator-sysmonitor的下载源
sudo add-apt-repository ppa:fossfreedom/indicator-sysmonitor -y
二、更新apt-get
sudo apt-get update
或者：

```
 sudo add-apt-repository ppa:fossfreedom/indicator-sysmonitor && sudo apt update
```

三、安装indicator-sysmonito

```
sudo apt-get install indicator-sysmonitor
```

四、启动

这时候通知栏默认会显示cpu和内存的实时数据

![在这里插入图片描述](https://img-blog.csdnimg.cn/401644fed6f34c7389cd2cca69473b23.png)


配置：点一下通知栏内容，按如下提示操作![在这里插入图片描述](https://img-blog.csdnimg.cn/bff36b7d70f54cfc8857fd3cec507ad5.png)


1. 开启开机自启动![在这里插入图片描述](https://img-blog.csdnimg.cn/c39f5354f19440999df05cc1a932dece.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAUmVzb3VyY2VmdWwh,size_16,color_FFFFFF,t_70,g_se,x_16)


2. 配置显示格式：CPU : {cpu} 网速 : {net}

![在这里插入图片描述](https://img-blog.csdnimg.cn/7ea8a292c71241b59a823e5091006914.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAUmVzb3VyY2VmdWwh,size_16,color_FFFFFF,t_70,g_se,x_16)

其他配置可以自由发挥~
网速 :   {net}  CPU {cpu}  {cputemp}   |  MEM {mem}  |  SWAP {swap}  |  Net Speed Compact {netcomp}  |  Total Net Speed {totalnet}
网速 :   {net}  | CPU : {cpu}  {cputemp}   |  MEM {mem}  |  SWAP {swap}  |  N SC {netcomp}  |  TNS {totalnet}



# 扩展六：双系统启动流程以及删除Ubuntu系统

双系统（如 Windows + Ubuntu）电脑的启动流程如下：

### **1. BIOS/UEFI 初始化**（一般不会有问题）

- 开机后，BIOS/UEFI 固件开始初始化硬件（CPU、内存、硬盘、显卡等）。
- 查找启动设备（通常是硬盘或 SSD）。
- 进入 Bootloader（引导程序）。

### **2. Bootloader（引导程序）加载**

- 你的电脑使用的是 **双系统（Windows + Ubuntu）**，一般会安装 **GRUB（GRand Unified Bootloader）** 作为引导程序。
- GRUB 读取配置文件（如 `/boot/grub/grub.cfg`），列出可用的操作系统选项。

### **3. 选择操作系统**

- 你可以在 GRUB 界面选择启动 **Ubuntu** 或 **Windows**。
- 如果不手动选择，GRUB 会在倒计时结束后默认启动预设的系统（可以在 `/etc/default/grub` 配置）。

### **4. 加载操作系统内核**

- 如果选择 Ubuntu：
  - GRUB 加载 Linux 内核（`vmlinuz`），同时加载 initrd（初始 RAM 磁盘）。
  - initrd 挂载根文件系统（`/`），然后启动 systemd，最终进入 Ubuntu 桌面环境。
- 如果选择 Windows：
  - GRUB 通过 `chainloader` 方式跳转到 Windows Boot Manager（`BOOTMGR`）。
  - Windows Boot Manager 读取 BCD（Boot Configuration Data）配置。
  - 加载 Windows 内核（`ntoskrnl.exe`），启动 Windows 系统。

### **总结**

1. **BIOS/UEFI** 初始化硬件，寻找启动设备。
2. **GRUB** 作为主引导程序，提供系统选择菜单。
3. 根据选择：
   - 进入 Linux 内核，启动 Ubuntu。
   - 进入 Windows Boot Manager，启动 Windows。

我的 **Lenovo Legion Y7000P** 使用的是 **UEFI 模式**，所以 GRUB 可能是 **EFI GRUB**，它会从 EFI 分区（`/boot/efi/`）加载。



## 问题一：Windows出现问题且要求在Windows中修改

```
则一般会涉及到这些指令
bootrec /fixmbr 
bootrec /fixboot
bootrec /scanos
bootrec /rebuildbcd 这是针对第几步
```

`bootrec` 命令主要用于修复 Windows 的 **MBR（主引导记录）** 和 **BCD（引导配置数据）**，通常用于修复 Windows 无法启动的问题。

在双系统启动流程中，它们针对的是 **第 4 步**（**加载操作系统内核**），具体来说，它们用于修复 **Windows Boot Manager** 的问题。

------

 **bootrec 命令的作用**

如果你的 **GRUB 破坏了 Windows 引导**，或者 **Windows 无法启动**，你可以在 **Windows 恢复模式** 或 **Windows 安装盘的命令提示符** 中运行这些命令。

| 命令                  | 作用                                    | 适用场景                                                    |
| --------------------- | --------------------------------------- | ----------------------------------------------------------- |
| `bootrec /fixmbr`     | 修复 MBR（主引导记录），不会影响分区表  | 适用于 MBR 损坏导致 Windows 无法启动                        |
| `bootrec /fixboot`    | 修复 Windows 的引导扇区                 | 适用于 Windows 引导扇区损坏（如 `BOOTMGR is missing` 错误） |
| `bootrec /scanos`     | 扫描 Windows 系统安装位置               | 检测是否有 Windows 版本未被引导管理器识别                   |
| `bootrec /rebuildbcd` | 重新构建 Windows 的 BCD（引导配置数据） | 适用于 BCD 记录丢失或损坏                                   |

------

 **在双系统中的应用**

1. **如果 GRUB 被 Windows 覆盖**（比如你重装了 Windows），需要 **重装 GRUB**。
2. **如果 Windows 无法引导**，可以用 `bootrec` 命令修复。

**典型修复 Windows 引导的步骤**（如果 Windows 启动失败）：

```bash
bootrec /fixmbr
bootrec /fixboot
bootrec /scanos
bootrec /rebuildbcd
```

如果 `bootrec /fixboot` 提示 **"Access is denied"**，可以先执行：

```bash
bcdboot C:\Windows /s C: /f ALL
```

如果你是想修复 **GRUB 引导 Ubuntu**，那 `bootrec` 命令是不适用的，需要使用 **Ubuntu LiveCD** 进入 `chroot` 修复 GRUB。

## 问题二：Ubuntu出现问题，要求在Ubuntu中处理并删除Ubuntu系统（针对Windows设置了管理员密码问题采用Ubuntu处理）

如果你仍然能进入 Ubuntu，并且想要 **在 Ubuntu 里删除 Ubuntu 并恢复 Windows 启动**，可以使用以下方法。

------

 **方法 1：使用 Ubuntu 删除 Ubuntu 分区并恢复 GRUB**

如果你想 **彻底删除 Ubuntu**，但又是在 **Ubuntu 里进行操作**，可以按照以下步骤：

 **1. 备份重要数据**

在删除 Ubuntu 之前，确保你已经备份了重要文件，因为这将永久删除 Ubuntu 及其数据。

 **2. 进入 Ubuntu，使用 fdisk/gparted 删除分区**

1. **打开终端**（`Ctrl + Alt + T`），运行：

   ```bash
   sudo fdisk -l
   ```

   找到你的 Ubuntu 分区（通常是 `/dev/sdaX` 或 `/dev/nvme0n1pX`，格式为 **ext4**）。

2. **使用 `fdisk` 或 `gparted` 删除 Ubuntu 分区**：

   ```bash
   sudo fdisk /dev/sdX  # 例如 /dev/sda 或 /dev/nvme0n1
   ```

   - 输入 `p` 列出分区。
   - 输入 `d` 删除 Ubuntu 相关分区（如 root `/` 和 swap）。
   - 输入 `w` 写入更改并退出。

   或者你可以使用 **GParted**（图形界面工具）：

   ```bash
   sudo apt install gparted
   sudo gparted
   ```

   - 右键 Ubuntu 分区 → **删除** → **应用更改**。

------

 **3. 修复 GRUB 并设为 Windows 默认**

现在 Ubuntu 分区已经删除了，但 GRUB 可能仍然存在。你需要修改 GRUB 以直接引导 Windows，或者完全移除 GRUB。

 **方案 1：修改 GRUB 让 Windows 成为默认系统**

如果你仍想保留 GRUB，可以修改 `/etc/default/grub` 让 Windows 启动项排在第一位：

```bash
sudo nano /etc/default/grub
```

找到：

```bash
GRUB_DEFAULT=0
```

改成：

```bash
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```

然后运行：

```bash
sudo update-grub
```

重启后，GRUB 会默认进入 Windows。

------

**方案 2：彻底删除 GRUB 并恢复 Windows 启动**（我的选择）

如果你想 **彻底移除 GRUB 并让 Windows 直接启动**，你可以用以下方式恢复 Windows 的引导：

1. **在 Ubuntu 里安装 `efibootmgr`（如果未安装）**：

   ```bash
   sudo apt install efibootmgr
   ```

2. **列出 UEFI 启动项**：

   ```bash
   sudo efibootmgr
   ```

   找到类似 `Boot000x* ubuntu` 的条目。

3. **删除 Ubuntu 引导项**：

   ```bash
   sudo efibootmgr -b 000x -B  # 这里的 "000x" 是上一步找到的 Ubuntu 引导项编号
   ```

4. **将 Windows 设为默认启动**：

   ```bash
   sudo efibootmgr -o 000y
   ```

   其中 `000y` 是 Windows Boot Manager 的编号（通常是 `Boot0000` 或 `Boot0001`）。

5. **（可选）删除 Ubuntu 的 EFI 目录**： 如果你想清理 Ubuntu 的引导文件，可以挂载 EFI 分区并删除 `ubuntu` 目录：

   ```bash
   sudo mount /dev/sdXY /mnt  # 例如 EFI 可能在 /dev/sda1
   sudo rm -rf /mnt/EFI/ubuntu
   sudo umount /mnt
   ```

6. **重启**，你的系统应该直接进入 Windows。

------

 **4. 进入 Windows 扩展分区（可选）**

如果你删除了 Ubuntu 分区，Windows 可能会显示未分配的磁盘空间。你可以：

- **进入 Windows** → `Win + R` → `diskmgmt.msc`
- 右键 C 盘 → **扩展卷** → **使用未分配空间**。

------

## **问题二总结**

| 方法                              | 适用场景                          |
| --------------------------------- | --------------------------------- |
| **修改 GRUB 默认启动项**          | 想保留 GRUB，但默认进入 Windows   |
| **删除 GRUB 并恢复 Windows 引导** | 完全移除 Ubuntu，Windows 直接启动 |
| **删除 Ubuntu 分区**              | 释放磁盘空间供 Windows 使用       |

这样，你就可以在 Ubuntu 里完成 Ubuntu 的删除，并让 Windows 恢复正常启动！