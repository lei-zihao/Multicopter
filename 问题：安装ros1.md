<<<<<<< Updated upstream
# 问题1：安装ros1

## 自动安装ros：wget http://fishros.com/install -O fishros && . fishros。但是ros1安装不了？
![image-20231210171930505](C:\markdown\Typora\图片\image-20231210171930505.png)  

[![image-20231210171930505.png](https://i.postimg.cc/y6fs4vK8/image-20231210171930505.png](https://postimg.cc/5jFZ85jh)[![image-20231210171930505.png](https://i.postimg.cc/y6fs4vK8/image-20231210171930505.png](https://postimg.cc/5jFZ85jh)

## 解决方法：

### 安装18.4版本的ubuntu，因为22.4不支持ros1

可以此种方法安装镜像源

https://img-blog.csdnimg.cn/20201002105940856.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTkxMjI5MQ==,size_16,color_FFFFFF,t_70#pic_center

https://img-blog.csdnimg.cn/20201002105943284.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTkxMjI5MQ==,size_16,color_FFFFFF,t_70#pic_center

https://img-blog.csdnimg.cn/20201002105945958.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTkxMjI5MQ==,size_16,color_FFFFFF,t_70#pic_center





# 问题2：无法定位软件包+无法解析域名

## 问题描述：

### 1、无法定位软件包  

[![image-20231210175956862.png](https://i.postimg.cc/0jcDfZs9/image-20231210175956862.png)](https://postimg.cc/H88rWwnN)

### 2、无法解析域名

[![QQ-20231210233828.png](https://i.postimg.cc/sxxmhV1q/QQ-20231210233828.png)
[](https://postimg.cc/vxR5Rwrt)

## 

## 原因：

### 软件源的问题，要更新软件源

## 解决方法：
### 1、更新镜像源

```
sudo apt-get update
sudo apt-get upgrade
```
### 2、若还是不行，就换镜像源：

 在软件和更新里——下载自——其他——选服务器（清华，阿里）

鱼香ros的一键安装

```
wget http://fishros.com/install -O fishros && . fishros
```



# 问题3：无法跑鱼香ros的launch文件

[![image-20231212152739130.png](https://i.postimg.cc/WpnGTpJx/image-20231212152739130.png)](https://postimg.cc/pymhBHCB)

![image-20231212152739130](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20231212152739130.png)

## 问题描述：

### ERROR:cannot launch node of type

## 原因：

### 没有配置好环境（只是把learning_launch功能包文件复制到my_ws工作空间中，还要把其他功能包复制过来）

## 解决方法：

### 1、先复制功能包

[![image-20231212152953763.png](https://i.postimg.cc/pL7Q40nT/image-20231212152953763.png)](https://postimg.cc/0zYJJ0nR)

![image-20231212152953763](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20231212152953763.png)

### 2、编译工作空间

[![image-20231212153122817.png](https://i.postimg.cc/Hkf5BVf8/image-20231212153122817.png)](https://postimg.cc/pmJpdXVP)

![image-20231212153122817](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20231212153122817.png)

### 3、配置环境+运行launch文件

[![image-20231212153404987.png](https://i.postimg.cc/TYNn5k09/image-20231212153404987.png)](https://postimg.cc/JGJs959D)

![image-20231212153404987](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20231212153404987.png)



# 问题4：

=======
# 问题1：安装ros1

## 自动安装ros：wget http://fishros.com/install -O fishros && . fishros。但是ros1安装不了？
![image-20231210171930505](C:\markdown\Typora\图片\image-20231210171930505.png)  

[![image-20231210171930505.png](https://i.postimg.cc/y6fs4vK8/image-20231210171930505.png](https://postimg.cc/5jFZ85jh)[![image-20231210171930505.png](https://i.postimg.cc/y6fs4vK8/image-20231210171930505.png](https://postimg.cc/5jFZ85jh)

## 解决方法：

### 安装18.4版本的ubuntu，因为22.4不支持ros1

可以此种方法安装镜像源

https://img-blog.csdnimg.cn/20201002105940856.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTkxMjI5MQ==,size_16,color_FFFFFF,t_70#pic_center

https://img-blog.csdnimg.cn/20201002105943284.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTkxMjI5MQ==,size_16,color_FFFFFF,t_70#pic_center

https://img-blog.csdnimg.cn/20201002105945958.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTkxMjI5MQ==,size_16,color_FFFFFF,t_70#pic_center





# 问题2：无法定位软件包+无法解析域名

## 问题描述：

### 1、无法定位软件包  

[![image-20231210175956862.png](https://i.postimg.cc/0jcDfZs9/image-20231210175956862.png)](https://postimg.cc/H88rWwnN)

### 2、无法解析域名

[![QQ-20231210233828.png](https://i.postimg.cc/sxxmhV1q/QQ-20231210233828.png)
[](https://postimg.cc/vxR5Rwrt)

## 















## 原因：

### 软件源的问题，要更新软件源

## 解决方法：
### 1、更新镜像源

```
sudo apt-get updaate
sudo apt-get upgrade
```
### 2、若还是不行，就换镜像源：

 在软件和更新里——下载自——其他——选服务器（清华，阿里）



# 问题3：无法跑鱼香ros的launch文件

[![image-20231212152739130.png](https://i.postimg.cc/WpnGTpJx/image-20231212152739130.png)](https://postimg.cc/pymhBHCB)

![image-20231212152739130](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20231212152739130.png)

## 问题描述：

### ERROR:cannot launch node of type

## 原因：

### 没有配置好环境（只是把learning_launch功能包文件复制到my_ws工作空间中，还要把其他功能包复制过来）

## 解决方法：

### 1、先复制功能包

[![image-20231212152953763.png](https://i.postimg.cc/pL7Q40nT/image-20231212152953763.png)](https://postimg.cc/0zYJJ0nR)

![image-20231212152953763](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20231212152953763.png)

### 2、编译工作空间

[![image-20231212153122817.png](https://i.postimg.cc/Hkf5BVf8/image-20231212153122817.png)](https://postimg.cc/pmJpdXVP)

![image-20231212153122817](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20231212153122817.png)

### 3、配置环境+运行launch文件

[![image-20231212153404987.png](https://i.postimg.cc/TYNn5k09/image-20231212153404987.png)](https://postimg.cc/JGJs959D)

![image-20231212153404987](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20231212153404987.png)



# 问题4：无法安装PX4源代码

## 问题描述：无法克隆

```
无法克隆 'https://github.com/PX4/PX4-FlightGear-Bridge.git' 到子模组路径 '/home/jeremy/PX4-Autopilot/Tools/flightgear_bridge'
克隆 'Tools/flightgear_bridge' 失败。按计划重试
```

## 解决办法：

### 1、可以先将PX4文件克隆下来，不去克隆子项目，运行下面指令

```
git clone https://github.com.cnpmjs.org/PX4/PX4-Autopilot.git
```

### 2、然后切换到PX4文件夹，继续克隆子项目,执行下面指令

```
cd PX4-Autopilot
git submodule update --init --recursive
```

### 3、如果还是出现失败也没关系，继续执行

```
git submodule update --recursive`
```

### 直到不出现失败提示为止。（这时是在继续克隆你之前没成功的子项目，注意：此时没有init)



# 问题4：bash文件运行

## 问题描述：mirrors.aliyun.com 无法解析

![image-20231220204413959](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20231220204413959.png)

## 解决方法：

### 一：已知可行：

#### 1、运行

```
sudo gedit /etc/resolv.conf 
```

#### 2、修改文件参数（更改里面的nameserver）

```
nameserver 8.8.8.8 
nameserver 8.8.4.4
nameserver 223.5.5.5
nameserver 223.6.6.6
```

### 二:待定：

#### 更换软件源



# 问题五：bash文件运行过程

## 问题描述：retrying......Could not find a version that satisfies the requirement

## ![image-20231220211301889](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20231220211301889.png)

## 解决方法：

### 循环操作直至依赖全部安装好

![image-20231220214857983](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20231220214857983.png)

## 问题分析

### 1检查pip的版本（升级版本）

```
python -m pip install --upgrade pip
```

### 2更换一个pip源或换软件源

#### 1、这时考虑换一个pip源

```
pip install pymysql -i https://pypi.tuna.tsinghua.edu.cn/simple/
```

#### 2、换软件源

### 3用镜像安装库（考虑是网速的原因，这时采用国内的镜像源来加速）

```
pip install 包名-i http://pypi.douban.com/simple/ --trusted-host pypi.douban.com
```

```text
阿里源 http://mirrors.aliyun.com/pypi/simple/

中国科技大学 https://pypi.mirrors.ustc.edu.cn/simple/ 

清华大学 https://pypi.tuna.tsinghua.edu.cn/simple/
```

直接运行下面的代码

```
bash ./PX4-Autopilot/Tools/setup/ubuntu.sh
```

是将安装相对完整的PX4固件环境需要下载的依赖包多，因为网络原因造成的报错更多**。此外，不管运行哪一个命令，其实大概率都会【遇到一堆红色的报错】，解决方法其实也很简单，即 【**确定导致报错的依赖包名，网上检索安装这个依赖包的方法】**。我们只需要将导致报错的依赖包都安装好了，运行.sh文件时就能会跳过他们。

## PS:如果安装好sympy库后，仍然不行。则按照以下方法把文件里的sympy>=1.10.1改为sympy

![image-20231222195839544](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20231222195839544.png)



# 问题六：PX4配置（太难了（哭脸））

## 问题描述：AttributeError: module 'em' has no attribute 'RAW_OPT'

![image-20240109134241110](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20240109134241110.png)

### 可能是因为使用旧的解决方案卸载em并安装empy。这还不够，因为从11月30日开始的最新版本的empy(4.0)似乎引起了AttributeError的新问题:` module `对象没有属性` RAW_OPT `，所以我安装了一个旧版本的empy `AttributeError: 'module' object has no attribute 'RAW_OPT'`（版本太新）

## 解决方案：

### 卸载新版本，安装一个旧版本的

```
pip3 uninatall empy
pip3 install empy==3.3.2
```

### 若仍然失败则更新软件源并重新编译（我的是这种）

```
sudo apt-get update
sudo apt-get upgrade
sudo make clean
```



# 问题八：roslaunch文件时，文件的仿真环境出现Resource not found: px4

## 问题描述：运行launch文件时Resource not found: px4



![image-20240312224250371](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20240312224250371.png)

## 解决方案：按照px4官方文档

分析：这意味着 PX4 SITL 未包含在路径中。要解决此问题，请在 `.bashrc` 文件末尾添加以下行：

```sh
source ~/PX4-Autopilot/Tools/simulation/gazebo/setup_gazebo.bash ~/PX4-Autopilot ~/PX4-Autopilot/build/px4_sitl_default
export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:~/PX4-Autopilot
export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:~/PX4-Autopilot/Tools/simulation/gazebo-classic/sitl_gazebo-classic
export GAZEBO_PLUGIN_PATH=$GAZEBO_PLUGIN_PATH:/usr/lib/x86_64-linux-gnu/gazebo-9/plugins
```

现在在终端中，转到主目录并运行以下命令以将上述更改应用于当前终端：

```sh
source .bashrc
```





# 问题九：opencv安装过程出现问题

### 问题描述：

### modules/java_bindings_generator/CMakeFiles/gen_opencv_java_source.dir/build.make:357: recipe for target 'CMakeFiles/dephelper/gen_opencv_java_source' failed

make[2]: *** [CMakeFiles/dephelper/gen_opencv_java_source] Error 1
CMakeFiles/Makefile2:1527: recipe for target 'modules/java_bindings_generator/CMakeFiles/gen_opencv_java_source.dir/all' failed
make[1]: *** [modules/java_bindings_generator/CMakeFiles/gen_opencv_java_source.dir/all] Error 2
Makefile:162: recipe for target 'all' failed
make: *** [all] Error 2

![image-20240320200204304](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20240320200204304.png)

## 解决方法：将下载改为Download。因为不支持中文



# 问题10：1、无法launch节点；2、无法发现

## 问题描述：ERROR: cannot launch node of type [rviz/rviz]: rviz

![image-20240324153738326](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20240324153738326.png)

## 解决方法：下载rviz

```
sudo apt-get install ros-melodic-rviz
```

## 同理：如下问题都是这样

1、https://img-blog.csdnimg.cn/20200310100359556.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjU5MTUyOQ==,size_16,color_FFFFFF,t_70

![在这里插入图片描述](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjU5MTUyOQ==,size_16,color_FFFFFF,t_70.png)

```
sudo apt-get install ros-melodic-robot-state-publisher
```

2、https://img-blog.csdnimg.cn/20200310104146178.png

![在这里插入图片描述](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/20200310104146178.png)

解决方法：

```
sudo apt-get install ros-melodic-joint-state-publisher-gui
```



# 问题11：安装opencv时

## 问题描述：

Traceback (most recent call last):  File "/home/ros1/下载/opencv-3.4.1/modules/java/generator/../generator/gen_java.py", line 1093, in <module>    copy_java_files(java_files_dir, target_path)  File "/home/ros1/下载/opencv-3.4.1/modules/java/generator/../generator/gen_java.py", line 1032, in copy_java_files    src = checkFileRemap(java_file)  File "/home/ros1/下载/opencv-3.4.1/modules/java/generator/../generator/gen_java.py", line 25, in checkFileRemap    assert path[-3:] != '.in', path AssertionError: /home/ros1/下载/opencv-3.4.1/modules/java/generator/src/java/org/opencv/osgi/OpenCVNativeLoader.java.in modules/java_bindings_generator/CMakeFiles/gen_opencv_java_source.dir/build.make:357: recipe for target 'CMakeFiles/dephelper/gen_opencv_java_source' failed make[2]: *** [CMakeFiles/dephelper/gen_opencv_java_source] Error 1 CMakeFiles/Makefile2:1652: recipe for target 'modules/java_bindings_generator/CMakeFiles/gen_opencv_java_source.dir/all' failed make[1]: *** [modules/java_bindings_generator/CMakeFiles/gen_opencv_java_source.dir/all] Error 2 Makefile:162: recipe for target 'all' failed make: *** [all] Error 2

## 原因分析：因为文件夹的名字为中文下载

## 解决方法：将文件夹的名字改为英文“Download”





# 问题12：无法launch一个文件

## 问题描述：RLException: [indoor1.launch] is neither a launch file in package [px4] nor is [px4] a launch file name
The traceback for the exception was written to the log file

![image-20240326223813698](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20240326223813698.png)

## 解决方法：删除重名文件

首先locate这个文件，看重复的文件在什么地方



# 问题13：工作空间编译不了

## 问题描述：![image-20240328144942795](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20240328144942795-1711608596265-1.png)

### 改完工作空间下的功能包的名字，然后编译不了了

## 解决方法：

### 1.删除 `build` 和 `devel` 文件夹，以确保在新的配置下重新构建。

### 2**修改 `CMakeLists.txt` 和 `package.xml`**：

- 确保你的 `CMakeLists.txt` 文件中的项目名称与你的功能包名称一致。
- 在 `CMakeLists.txt` 中搜索并替换旧的功能包名称，确保所有引用都已更新为新的名称。
- 在 `package.xml` 文件中更新功能包名称。

### 3**重新构建功能包**：

- 在你的工作空间中运行 `catkin_make` 或 `catkin build` 以重新构建功能包。
- 如果使用的是 `catkin_tools`，则运行 `catkin clean` 以清理旧的构建文件，然后再次运行 `catkin build`。





# 问题14：无法启动仿真launch文件

## 问题描述：![image-20240328155544384](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20240328155544384.png)

## 问题分析：

因为跑仿真时代码的话题变为 

```
发布者订阅者为
/iris_0/mavros/state
/iris_0/mavros/local_position/pose
客户端服务端为
iris_0/mavros/cmd/arming
iris_0/mavros/set_mode
```

可能是launch文件写错了，所以检查一下节点能不能启动（rosrun my_control_lzh pose_control_sim.cpp）

![image-20240329002547530](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20240329002547530.png)

## 问题解决：

将话题名字改为仿真的话题

检查launch文件，添加CMakelist文件

## 推广：

#### 若为别人的代码则有可能是没下载功能包

https://img-blog.csdnimg.cn/20210717080225949.png

![在这里插入图片描述](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/20210717080225949.png)

```
sudo apt-get install ros-melodic（ros版本名）-包名
```

#### 1.先加权限

```
sudo chmod +x 
```

#### 2.再加上环境变量

```
source ~/.bashrc
```

## 其他原因：

CMakelist文件的依赖项没调好：

1.忘在find_package中加入roscpp了

2.添加add_excutive( 可执行文件名字  文件路径)

3.没加入add_libraries(可执行文件名字 )







# 问题十五：编译问题

## 问题描述：在工作空间无法编译c++文件

![image-20240402162651696](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20240402162651696.png)

## 我的已有操作：

1、CMakelist文件添加find_package()中添加geometry_msgs依赖项

2、CMakelist文件添加可执行文件和库

add_executable(pose_control_sim src/pose_control_sim.cpp)
target_link_libraries(pose_control_sim
  ${catkin_LIBRARIES}
)

3、CMakelist文件添加catkin_package中的依赖项geometry_msgs

![image-20240402162457020](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20240402162457020.png)

因为

![image-20240402162553709](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20240402162553709.png)

## 问题分析：程序编写错误，不能够在main函数外赋值。可以在main函数外定义全局变量，但得在main函数内赋值

![image-20240402175118252](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20240402175118252.png)

## 解决方法：

将赋值放到函数内部

![image-20240402163154092](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/image-20240402163154092.png)



# 问题十六：首飞无人机时的问题记录

## 一.QGC里一直显示Not ready

### 原因分析：

### 1.通过查看日志信息知道：在飞行途中遥控器的模式切换突然没了。推测为遥控器接收机有问题。遥控器信号不稳

### 2.GPS信号不好，接线松了。

​			拔电重启

​			GPS的安全开关没打开也会导致无法解锁，有的是集成再GPS上，有的是单独的一个小按钮，慢闪就是没打开的状态，长按一下变成双闪，就是打开状态们就可以解锁了。

### 3.拔CD内存卡时，一定要注意先断电，再拔内存卡，然后上电。不然GPS无信号。无法进入定点模式（要用GPS信号）（自稳模式不用GPS，可用于室内飞行，一般穿越机为这样的模式）。

### 解决方案：换一个5pin的接线，重新连接。

## 二.起飞时仅拨动推力杆，无人机会左右飘。每次重新校准传感器时都会换个方向飘。

### 原因分析：

#### 1.QGC校准电调时没校准好

#### 2.电调安装位置并未按照PX4官网要求1324.而为1234.导致飞行时底层飞控分配的推力不符合预期。

## 三.炸机

### 原因分析：

#### 1.电池电量过低。最后垂直下落

#### 2.按键设置不合理。用模式切换时，手的姿势不对，误触了arm按键。导致无人机掉落。

![IMG_2906(20240417-124955)](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/IMG_2906(20240417-124955).JPG)![IMG_2904](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/IMG_2904.JPG)

![IMG_2925(20240417-174048)](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/IMG_2925(20240417-174048).JPG)

![IMG_2905](%E9%97%AE%E9%A2%98%EF%BC%9A%E5%AE%89%E8%A3%85ros1.assets/IMG_2905.JPG)
