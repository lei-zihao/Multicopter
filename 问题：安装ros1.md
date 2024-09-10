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





# 问题十七：虚拟机无WiFi

## 文章目录

- - [方法一：网络连接状态排查](https://blog.csdn.net/dong__ge/article/details/123581117#_14)
  - [方法二：主机网络服务查询](https://blog.csdn.net/dong__ge/article/details/123581117#_40)
  - [其他解决方法](https://blog.csdn.net/dong__ge/article/details/123581117#_54)

早上刚到公司，打开电脑，远程连接虚拟机，突然发现 `SSH`连接失败！

What，什么情况，打开[虚拟机](https://so.csdn.net/so/search?q=%E8%99%9A%E6%8B%9F%E6%9C%BA&spm=1001.2101.3001.7020)，网络连接的按钮都没了？还报了一堆异常！

![image-20220318091445473](问题：安装ros1.assets/90279ad13424d3c429e5af5f083dbbe2-17138428649837.png)

内心一阵恐慌，这种虚拟机突然崩溃的时候，虽然不经常遇到，一旦碰上，着实烦人。

**基本上，这种情况大多都会遇到，同样导致这样问题可能有很多，在这里记录一下两种解决方案，同时并分享一些其他相同问题的解决方法！**

### 方法一：网络连接状态排查

出现该问题，第一步进行网络状态排查，通常也是最有效的方法之一。

进入 `Ctrl+Alt+T`打开终端，输入以下命令，查看网络状态信息。

```bash
sudo vim /var/lib/NetworkManager/NetworkManager.state
```

可以看到，网络状态信息 `NetworkingEnabled=false`，

![image-20220318091818467](问题：安装ros1.assets/bdc9a1a89c40e332ff6b08591c03d755-17138428649849.png)

不知道怎么就被搞成了 `false`，要:q

想修改成 `true`，需要以下步骤：

- **关闭网络服务**：`sudo service network-manager stop`
- **设置网络状态**：`sudo vim /var/lib/NetworkManager/NetworkManager.state`，设置为 `true`
- **打开网络服务**：`sudo service network-manager start`

此时，就看到了网络连接成功的标识。

![image-20220318092109152](问题：安装ros1.assets/e118045e5b97ad82d5e23f3e092ced5c.png)

### 方法二：主机网络服务查询

还有另外一个原因，一般是自己的主机把服务给关掉了，或者是因为**电脑管家把这些软件给升级了**，然后把**虚拟机的网路服务给停止**了。

右击 `我的电脑`，然后找到 `管理`\->`服务`，**确保下面虚拟机的网络服务是否打开**，然后虚拟机就有网了。

![img](问题：安装ros1.assets/5dd7cf14405c3126d080e1d1b4f839c4.png)

> 如果你的还没有解决，可以参考以下文章。

### 其他解决方法

[【VMware】虚拟机中Ubuntu无法连接网络的有效解决办法](https://blog.csdn.net/u013554213/article/details/79408084)

[VMware 虚拟机里连不上网的五种解决方案](https://blog.csdn.net/qq_36408196/article/details/103390303)

[VMware 虚拟机无法连接网络解决办法](https://blog.csdn.net/m0_37259197/article/details/78221016)

### 解决方法三：  

可能原因是VMware NET Service服务没开

win + R，输入：services.[msc](https://so.csdn.net/so/search?q=msc&spm=1001.2101.3001.7020) ，启动VMware NAT Servise服务

![在这里插入图片描述](问题：安装ros1.assets/def4e7cfda80406b910ee9b8f7546a7e.png)

找到“VMware NAT Service”，点击左边的“启动”。

![在这里插入图片描述](https://img-blog.csdnimg.cn/950954e6737c49efb711ff204cd7284e.png)



# 问题十八：舵机调试

### 1.代码控制不了（未解决）

### 问题描述：有信号输出了，但是是一上电就开始转动（按照正常情况他应该是不动的）

### 原因分析：推测可能是之前代码给他初始化，而后面的代码要用spinones才能调用一次

### 解决思路：试试代码控制量初始化为1，能不能反向转动。

### 2.遥控器控制（必须arm）（已解决）

### 问题描述：用遥控器可以控制IO PWM OUT端口（并不是FMU PWM OUT）。要在arm模式下。自己在QGC中映射一个通道![](问题：安装ros1.assets/image-20240504150821762.png![image-20240504153258806](问题：安装ros1.assets/image-20240504153258806.png)

![image-20240504125952764](问题：安装ros1.assets/image-20240504125952764.png)



# 问题十九：用vins来定点(位置模式）飞行

## 问题描述：无法切入offboard模式，无法进入位置模式

### 进入位置模式

1.提供位姿代码
先让/mavros/local_position/pose的值和/mavros/vision_pose/pose的值基本一样

要自己写一个代码来转化数据即如果用视觉的话要将视觉估计的位姿传给mavros节点。即让飞控可以订阅到/mavros/local_position/pose（有数据）。

解决方法：用vins或者t265来把定位信息传给飞控。订阅视觉的imu数据/vins_estimator/odometry或 并转化为posestamped类型。然后通过/mavros/vision_pose/pose发布pose。

![image-20240515205653481](问题：安装ros1.assets/image-20240515205653481.png)

![img](问题：安装ros1.assets/O[XPZCR{M2XD3V%6U2F`CW.png)

2.需要的功能包

要想用让飞控接收到/mavros/vision_pose/pose发布的pose。还要下载按照功能包

```
sudo apt-get install ros-noetic-mavros-extras
```

这样mavros就看可以接收到/mavros/vision_pose/pose发布的话题了。

### 进入offboard模式（命令和频率）

1.还要发布命令信息才能进入offboard模式

即一般都是要发布其目标点位置命令。但是想要从offboard切换land模式时：1先退出offboard模式，然后land模式。2加一个判断标识变量bool型。当赋值为true时，不发布命令指令（退出offboard模式）。

```c++
int offboard_flag = 0; // 防止切land降落之后又去解锁切offboard
在循环里
if (!offboard_flag) {
        local_pos_pub.publish(pose);
    }
```

2.保证发布目标位姿的频率不低于2hz

即最好不用ros::duritio（10.0）.sleep()。通过添加一个bool类型的hovering变量来控制悬停。

```c++
if ((abs(position[0]) < 0.2 && abs(position[1]) < 0.2 && abs(position[2] - HEIGHT) < 0.2))
{
    if (!hovering)
    {
        ROS_INFO("Hovering at (%f, %f, %f)", pose.pose.position.x, pose.pose.position.y, pose.pose.position.z);
        hovering = true;
        hover_start_time = ros::Time::now();
    }
    else if (ros::Time::now() - hover_start_time > ros::Duration(30.0))
    {
        ROS_INFO("Hover complete. Moving to next position.");
        hovering = false;
        pose.pose.position.x = SIDE;
        pose.pose.position.y = 0;
        pose.pose.position.z = HEIGHT;
        last_request = ros::Time::now();
    }
}
```



### 代码案例:

确保无人机在起飞到 `(0, 0, HEIGHT)` 位置时悬停30秒，之后不再悬停，而是直接移动到 `(SIDE, 0, HEIGHT)`，再移动回到 `(0, 0, HEIGHT)`，最后降落。

```c++
#include <ros/ros.h>
#include <geometry_msgs/PoseStamped.h>
#include <mavros_msgs/CommandBool.h>
#include <mavros_msgs/SetMode.h>
#include <mavros_msgs/State.h>

mavros_msgs::State current_state;
double position[3] = {0, 0, 0};

void state_cb(const mavros_msgs::State::ConstPtr &msg) {
    current_state = *msg;
}

void pos_cb(const geometry_msgs::PoseStamped::ConstPtr &msg) {
    position[0] = msg->pose.position.x;
    position[1] = msg->pose.position.y;
    position[2] = msg->pose.position.z;
}

int main(int argc, char **argv) {
    ros::init(argc, argv, "offb_node");
    ros::NodeHandle nh;
    ros::NodeHandle nh1("~");
    float HEIGHT;
    float SIDE;
    bool AUTO_ARM_OFFBOARD;
    nh1.param<float>("height", HEIGHT, 0.65);
    nh1.param<float>("side", SIDE, 1.5);
    nh1.param<bool>("auto_arm_offboard", AUTO_ARM_OFFBOARD, false);

    ros::Subscriber state_sub = nh.subscribe<mavros_msgs::State>("mavros/state", 10, state_cb);
    ros::Subscriber position_sub = nh.subscribe<geometry_msgs::PoseStamped>("/mavros/local_position/pose", 10, pos_cb);
    ros::Publisher local_pos_pub = nh.advertise<geometry_msgs::PoseStamped>("mavros/setpoint_position/local", 10);
    ros::ServiceClient arming_client = nh.serviceClient<mavros_msgs::CommandBool>("mavros/cmd/arming");
    ros::ServiceClient set_mode_client = nh.serviceClient<mavros_msgs::SetMode>("mavros/set_mode");

    // the setpoint publishing rate MUST be faster than 2Hz
    ros::Rate rate(20.0);

    // wait for FCU connection
    while (ros::ok() && !current_state.connected) {
        ros::spinOnce();
        rate.sleep();
    }

    geometry_msgs::PoseStamped pose;
    pose.pose.position.x = 0;
    pose.pose.position.y = 0;
    pose.pose.position.z = HEIGHT;

    // send a few setpoints before starting
    for (int i = 100; ros::ok() && i > 0; --i) {
        local_pos_pub.publish(pose);
        ros::spinOnce();
        rate.sleep();
    }

    mavros_msgs::SetMode offb_set_mode;
    offb_set_mode.request.custom_mode = "OFFBOARD";

    mavros_msgs::SetMode land_set_mode;
    land_set_mode.request.custom_mode = "AUTO.LAND";

    mavros_msgs::CommandBool arm_cmd;
    arm_cmd.request.value = true;

    int offboard_flag = 0; // 防止切land降落之后又去解锁切offboard
    bool hovering = false;
    bool moved_to_next_position = false;
    bool moved_back_to_start = false;
    ros::Time hover_start_time;

    ros::Time last_request = ros::Time::now();

    while (ros::ok()) {
        if (AUTO_ARM_OFFBOARD) {
            if (current_state.mode != "OFFBOARD" &&
                (ros::Time::now() - last_request > ros::Duration(5.0)) && (offboard_flag == 0)) {
                if (set_mode_client.call(offb_set_mode) &&
                    offb_set_mode.response.mode_sent) {
                    ROS_INFO("Offboard enabled");
                }
                last_request = ros::Time::now();
            } else {
                if (!current_state.armed &&
                    (ros::Time::now() - last_request > ros::Duration(5.0)) && (offboard_flag == 0)) {
                    if (arming_client.call(arm_cmd) &&
                        arm_cmd.response.success) {
                        ROS_INFO("Vehicle armed");
                    }
                    last_request = ros::Time::now(); // 可以通过这个方式保持当前指点持续几秒钟。
                }
            }
        }

        // Hover for 30 seconds after reaching the initial position
        if ((abs(position[0]) < 0.2 && abs(position[1]) < 0.2 && abs(position[2] - HEIGHT) < 0.2) && !hovering && !moved_to_next_position) {
            ROS_INFO("Hovering at (%f, %f, %f)", pose.pose.position.x, pose.pose.position.y, pose.pose.position.z);
            hovering = true;
            hover_start_time = ros::Time::now();
        }

        // Check if hover time is over
        if (hovering && (ros::Time::now() - hover_start_time > ros::Duration(30.0))) {
            ROS_INFO("Hover complete. Moving to next position.");
            hovering = false;
            moved_to_next_position = true;
            pose.pose.position.x = SIDE;
            pose.pose.position.y = 0;
            pose.pose.position.z = HEIGHT;
            last_request = ros::Time::now();
        }

        // Move to the next position
        if (moved_to_next_position && (abs(position[0] - SIDE) < 0.2 && abs(position[1]) < 0.2 && abs(position[2] - HEIGHT) < 0.2)) {
            ROS_INFO("Reached next position. Moving back to start.");
            moved_to_next_position = false;
            moved_back_to_start = true;
            pose.pose.position.x = 0;
            pose.pose.position.y = 0;
            pose.pose.position.z = HEIGHT;
            last_request = ros::Time::now();
        }

        // Move back to the start position
        if (moved_back_to_start && (abs(position[0]) < 0.2 && abs(position[1]) < 0.2 && abs(position[2] - HEIGHT) < 0.2)) {
            ROS_INFO("Back to start position. Initiating landing.");
            moved_back_to_start = false;
            if (set_mode_client.call(land_set_mode) && land_set_mode.response.mode_sent) {
                ROS_INFO("Landing enabled");
                offboard_flag = 1;
            }
        }

        // Publish the position setpoint if not in landing mode
        if (!offboard_flag) {
            local_pos_pub.publish(pose);
        }

        ros::spinOnce();
        rate.sleep();
    }

    return 0;
}
```





# 问题二十：ros功能包所用opencv版本与ros默认opencv版本不一致情况解决方法_ros查看opencv版本

> ## Excerpt
> 下面camke命令中，CMAKE_INSTALL_PREFIX指定了安装路径，OPENCV_EXTRA_MODULES_PATH指定了opencv_contrib的路径，注意确保opencv_contrib和opencv处于同一个文件夹内，下面OPENCV_EXTRA_MODULES_PATH指定的相对路径才有效。将opencv编译生成的build文件路径加入到cv_bridge功能包的CMakeLists.txt里，命令如下，像上面自己编译安装的opecv3.3.1的build文件夹路径就是。_ros查看opencv版本

---
## ros功能包所用[opencv](https://so.csdn.net/so/search?q=opencv&spm=1001.2101.3001.7020)版本与ros默认opencv版本不一致情况解决方法

这种情况包含比如：  
在ubuntu20.04 ros noetic opencv4的环境下部署opencv3的功能包  
在ubuntu20.04 ros foxy opencv4的环境下部署opencv3.4.1的功能包（比如部署[ros2](https://so.csdn.net/so/search?q=ros2&spm=1001.2101.3001.7020)的vins-fusion-gpu时）  
在ubuntu18.04 ros melodic opencv3.3.1的环境下部署opencv3.4.1的功能包（比如部署vins-fusion-gpu时）

解决的关键是使得功能包所调用的cv\_bridge功能包是寻找链接的我们想指定的opencv版本，由于ROS功能包一般都是默认用的装ROS时自动二进制安装的cv\_bridge功能包，导致默认情况下，ROS功能包就都是使用的同一个版本的opencv，也就是这个二进制安装的cv\_bridge功能包所原本找到并链接的opencv，如果我们有功能包需要使用特定版本的opencv，没法使用ros现在默认链接的opencv，此时功能包编译运行便会出现问题，比如opencv4的环境下想用opencv3的功能包，或者opencv3.3.1的环境下想用只能适配于opencv3.4.1的vinsfusiongpu，解决办法就是自己源码编译安装一个cv\_bridge（如果是ROS2注意源码编译安装ROS2版本的cv\_bridge），使得此cv\_bridge使用我们指定版本的opencv，同时使我们的功能包使用我们源码编译安装的这个cv\_bridge，就可以实现功能包找到并编译链接的我们指定版本的opencv了。

这里以在ubuntu20.04 opencv4的环境下部署原本依赖opencv3.3.1的功能包为例

首先源码编译安装opencv3.3.1和opencv\_contrib3.3.1，这里假设功能包也需要opencv\_contrib。  
新建一个文件夹opencv331来专门存放opencv3.3.1和opencv\_contrib3.3.1

```bash
mkdir opencv331

cd opencv331
```

然后运行下面命令下载opencv3.3.1和opencv\_contrib3.3.1

```cobol
git clone -b 3.3.1 https://github.com/opencv/opencv.git

git clone -b 3.3.1 https://github.com/opencv/opencv_contrib
```

接着编译安装  
下面camke命令中，CMAKE\_INSTALL\_PREFIX指定了安装路径，OPENCV\_EXTRA\_MODULES\_PATH指定了opencv\_contrib的路径，注意确保opencv\_contrib和opencv处于同一个文件夹内，下面OPENCV\_EXTRA\_MODULES\_PATH指定的相对路径才有效。

```cobol
cd opencv

mkdir build

cd build

cmake -D CMAKE_BUILD_TYPE=Release -D WITH_CUDA=OFF -D CMAKE_INSTALL_PREFIX=/usr/local -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules ..

make -j8

sudo make install
```

此时[ubuntu](https://so.csdn.net/so/search?q=ubuntu&spm=1001.2101.3001.7020)环境里面可以找到opencv4也可以找到opencv3

查找opencv3版本命令可以用

```lua
pkg-config --modversion opencv
```

查找opencv4版本命令可以用

```lua
pkg-config --modversion opencv4
```

此时单纯地把功能包的cmakelists里面的find\_package(OpenCV REQUIRED)改为find\_package(OpenCV 3.3.1 REQUIRED)是不够的，这样虽然可以找到opencv3.3.1，但是编译链接时会依旧链接的opencv4的库文件，因为ubuntu20.04上ros noetic二进制安装的cv\_bridge默认链接的是opencv4，这样编译一般会出现譬如undefined reference to cv::mat::mat()一类带有undefined的报错，出现这种undefined的报错一般是因为找到了头文件，但是链接库的时候没有链接库或者没有找到库导致的，因为头文件一般只有函数的声明，库文件才带有函数的定义实现。

![输入图片说明](问题：安装ros1.assets/4a1f1f4b1fa64558131d3cae0c9bc795.jpeg)

可以cmakelists里面加上这些打印，会发现虽然找到的是opencv3.3.1，但是链接的库还是opencv4的

```erlang
message(STATUS "OpenCV library status:")

message(STATUS " version: ${OpenCV_VERSION}")

message(STATUS " libraries: ${OpenCV_LIBS}")

message(STATUS " include path: ${OpenCV_INCLUDE_DIRS}")

message(STATUS " catkin libraries: ${catkin_LIBRARIES}")
```

![输入图片说明](问题：安装ros1.assets/c06934e97d6d514e8f0918762d62bf02.jpeg)

此时需要自己再另外编码编译安装一个cv\_bridge，之前系统二进制安装的cv\_bridge不用卸载，只需要保证自己的功能包找到的cv\_bridge功能包是源码编译安装的cv\_bridge功能包即可。实现这个的操作就是自己功能包的cmakelists里面加上`set(cv_bridge_DIR "your-path/cv_bridge_ws/devel/share/cv_bridge/cmake")` 。

按照下面操作源码编译部署一个cv\_bridge，使得这个cv\_bridge是调用的opencv3.3.1，同时自己这个功能包是找到的这个源码编译的cv\_bridge，而不是系统二进制安装的cv\_bridge就可以了。

ros1下源码编译安装cv\_bridge

```bash
mkdir -p cv_bridge_ws/src

cd cv_bridge_ws/src

git clone https://gitee.com/maxibooksiyi/cv_bridge

cd ..
```

将opencv编译生成的build文件路径加入到cv\_bridge功能包的CMakeLists.txt里，命令如下，像上面自己编译安装的opecv3.3.1的build文件夹路径就是`~/opencv331/opencv/build`

```csharp
set(OpenCV_DIR "your-path/opencv-x.x.x/build")
```

编译

```undefined
catkin_make
```

如果是ros2，则源码编译安装cv\_bridge功能包的步骤是

```cobol
mkdir cv_bridge_ros2_ws/src

cd cv_bridge_ros2_ws

cd src

git clone https://github.com/ros-perception/vision_opencv.git -b foxy
```

把cv\_bridge功能包里的cmakelists（/cv\_bridge\_ros2\_ws/src/vision\_opencv/cv\_bridge/CMakeLists.txt）里这里的OpenCV 4改为OpenCV 3  


![输入图片说明](问题：安装ros1.assets/3ddd5cc359cdeeaf04c7ed9153e21d01.png)

![输入图片说明](问题：安装ros1.assets/62a4d139074ae94cc37e6952950f9f19.png)


改完后保存编译

```erlang
cd ..

colcon build
```

源码编译部署完cv\_bridge功能包之后，最后将依赖使用指定opencv版本的功能包里的**CMakeLists.txt**文件按照下面命令添加opencv路径以及cv\_bridge路径，位置放在OpenCV和cv\_bridge的find\_package之前即可，这样再编译这个功能包就会链接的是所指定版本的opencv，而不是原来ros默认链接的opencv了。

```csharp
set(OpenCV_DIR "your-path/opencv-x.x.x/build")

set(cv_bridge_DIR "your-path/cv_bridge_ws/devel/share/cv_bridge/cmake")
```

## 代码全部：OpenCv4.6.0和cv\_bridge安装（gpu）

#### 1、opencv安装

移动至指定目录

```
cd ~/IPAC-drone/doc/
sudo mv ./opencv-4.6.0/ /usr/local/
sudo mv ./opencv_contirb-4.6.0/ /usr/local/
cd /usr/local/opencv-4.6.0/
```

确定安装路径，我的是CMAKE\_INSTALL\_PREFIX=/usr/local

开始编译

```
sudo mkdir build &amp;&amp; cd build
sudo cmake -D CMAKE_BUILD_TYPE=RELEASE \
        -D CMAKE_INSTALL_PREFIX=/usr/local \
        -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-4.6.0/modules \
        -D WITH_CUDA=ON \
        -D CUDA_ARCH_BIN=8.7 \
        -D CUDA_ARCH_PTX="" \
        -D ENABLE_FAST_MATH=ON \
        -D CUDA_FAST_MATH=ON \
        -D WITH_CUBLAS=ON \
        -D WITH_LIBV4L=ON \
        -D WITH_GSTREAMER=ON \
        -D WITH_GSTREAMER_0_10=OFF \
        -D WITH_QT=ON \
        -D WITH_OPENGL=ON \
        -D CUDA_NVCC_FLAGS="--expt-relaxed-constexpr" \
        -D WITH_TBB=ON \
        -D CUDA_SDK_ROOT_DIR=/usr/local/cuda-11.4/ \
        ..
sudo make
sudo make install
```

#### 2、cv\_bridge配置

创建cv\_bridge专属的工作空间

```
mkdir cv_bridge_460/src
cd ~/cv_bridge_460/src
```

将cv\_bridge移动到专属工作空间

```
cp ~/IPAC-drone/doc/cv_bridge ~/cv_bridge_460/src
```

编译

```
cd ~/cv_bridge_460/
catkin_make
```



# 问题二十一：从零开始的机械臂yolov5抓取gazebo仿真（环境搭建篇中）_melodic yolo(GPU)

### [yolov5](https://so.csdn.net/so/search?q=yolov5&spm=1001.2101.3001.7020)运行环境搭建

本篇主要讲如何搭建yolov5运行环境，以及一些需要注意避坑的重要知识点。anaconda与[显卡驱动](https://so.csdn.net/so/search?q=%E6%98%BE%E5%8D%A1%E9%A9%B1%E5%8A%A8&spm=1001.2101.3001.7020)先装后装是没有什么影响的，关键在于，不能将显卡驱动以及cuda装在虚拟环境中。这里介绍一下博主的电脑环境为i7九代+ubuntu18.04+ros-melodic+gtx1660ti显卡，渣渣神舟笔记本。当然各位配置是越高越好哈，渣本训练个模型快要报废了。



首先查看自己python的环境

```cpp
python3
```

ubuntu18.04默认安装的python3环境是：python 3.6.9.在yolov5的分支中查看对应版本要求的python3开发环境。  
目前，默认的yolov5版本是v6.1,而要求的python环境：python>=3.7.0。  
这里，我们选择yolov5 6.0版本，其python环境：python >=3.6.0 ，PyTorch >=1.7

#### 显卡驱动以及cuda安装

在博主之前发的文章中有提到显卡驱动的安装方法：[gazebo版本升级以及环境太暗的解决方法](https://blog.csdn.net/qq_48427527/article/details/124459006?spm=1001.2014.3001.5502)，然而这样的方法其实也有一些问题，那就是使用

```
sudo ubuntu-drivers autoinstall 
```

自动下载命令下载的显卡驱动，是适配你显卡的最佳驱动，并不一定能够下载到你需要的驱动，最好的方式还是得手动安装。

##### 避坑提醒！！！

一开始博主的显卡驱动为470对应安装的cuda版本为11.4，然而在使用gpu版pytorch基于yolov5训练模型时发现loss曲线呈一条直线，且无法训练模型，为解决该问题又跳了许多坑，网上也没有很好的解决方案，无奈博主只能重新安装显卡驱动以及cuda，卸载原先的cuda真的是一门技术活，给博主留下了难忘的回忆，希望各位能够及时避坑。

##### 安装cuda10.2版本

为什么安装cuda10.2版本呢，因为该版本比较稳定且支持pytorch1.8，由显卡驱动与cuda版本对应表[显卡驱动与cuda版本对应表](https://docs.nvidia.com/cuda/cuda-toolkit-release-notes/index.html)中我们可以发现cuda10.2版本对应的显卡驱动为440且该驱动支持博主的gtx1660ti显卡。![请添加图片描述](问题：安装ros1.assets/1500c53fa94b4c09bb7d7985f9d46a42.png)  
接下去就是在官网下载对应的驱动以及cuda了，打开官网[cuda各版本下载库](https://developer.nvidia.cn/cuda-toolkit-archive)，选择并点击cuda10.2版本

![请添加图片描述](问题：安装ros1.assets/8f2f620880cf40e993ee21f731e36802.png)  
进入安装链接，依次选择你自己电脑对应的环境，博主的选择如下  
![请添加图片描述](问题：安装ros1.assets/7f6fdaecea254c88a6bd780de3f3c730.png)  
接着就出现了如下安装命令，依照如下命令安装即可。

```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-ubuntu1804.pin
sudo mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/10.2/Prod/local_installers/cuda-repo-ubuntu1804-10-2-local-10.2.89-440.33.01_1.0-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu1804-10-2-local-10.2.89-440.33.01_1.0-1_amd64.deb
sudo apt-key add /var/cuda-repo-10-2-local-10.2.89-440.33.01/7fa2af80.pub
sudo apt-get update
sudo apt-get -y install cuda
```

安装完成后，打开终端，输入`nvcc -V`

出现如下显示，则说明cuda10.2安装完毕。

![请添加图片描述](问题：安装ros1.assets/145a1a5c823f4eab899b4c3d02aee793.png)  
接着输入`nvidia-smi`，你会发现对应的显卡驱动也装好了。

![请添加图片描述](问题：安装ros1.assets/bf39a273b8754450a0c4b63f58901f8f.png)  
安装完成后，还需将如下代码写进.bashrc文件中，并`source .bashrc`文件

```
export PATH=/usr/local/cuda-10.2/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-10.2/lib64\
${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```

![请添加图片描述](问题：安装ros1.assets/7c96c2e3a1504228ab6c7528aafba2e3.png)

#### anaconda3环境配置

Anaconda 是一个用于科学计算的 Python 发行版,支持 Linux, Mac, Windows, 包含了众多流行的科学  
计算、数据分析的 Python 包。安装anaconda是因为要将pytorch安装至conda环境中，因为ros-melodic默认使用的是python2.7，虽然可以将默认使用python改为3.6版本，但是这样一来，会对ros的正常使用造成影响，且conda可自由配置python环境，因此将pytorch安装在conda环境中是最为合理的方案。

其实anaconda安装配置这一块网上的教程不少，这块各位可以酌情参考。

##### 安装anaconda（anaconda安装也可以直接使用wget命令，在Terminal中进行下载，执行bash命令进行安装：
wget https://repo.anaconda.com/archive/Anaconda3-2022.05-Linux-aarch64.sh
bash Anaconda3-2022.05-Linux-aarch64.sh
之后一路Enter+yes，直到安装完成
重新打开Terminal，发现命令行最前面有了(base)，如果没有的话，执行source activate命令，回车即可）

1.  先去官方地址下载好对应的安装包（还有可去清华镜像站下载，具体可看参考文献部分）  
    下载地址:[https://www.anaconda.com/download/#linux](https://www.anaconda.com/download/#linux)
2.  然后安装anaconda

```
bash ~/Downloads/Anaconda3-2021.05-Linux-x86_64.sh
```

anaconda会自动将环境变量添加到PATH里面,如果后面你发现输入conda提示没有该命令,那么  
你需要执行命令 source ~/.bashrc 更新环境变量,就可以正常使用了。  
如果发现这样还是没用,那么需要添加环境变量。  
编辑~/.bashrc 文件,在最后面加上

```
export PATH=/home/bai/anaconda3/bin:$PATH
```

注意:路径应改为自己机器上的路径  
保存退出后执行: `source ~/.bashrc`  
再次输入 `conda list` 测试看看,应该没有问题。

##### 添加anaconda国内镜像配置(见问题二十四，添加软件源)

清华TUNA提供了 Anaconda 仓库的镜像,运行以下三个命令:（最简单的）

```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels
https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
```

##### 创建conda[虚拟环境](https://so.csdn.net/so/search?q=%E8%99%9A%E6%8B%9F%E7%8E%AF%E5%A2%83&spm=1001.2101.3001.7020)

这里我创建了一个python3.8的虚拟环境，用于安装pytorch1.8以及适配yolov5-6.1版本

```
创建虚拟环境
conda create -n 虚拟环境的名字 python=3.8(python版本自己决定)
创建完后激活环境
conda activate 之前设定的虚拟环境的名字
关闭环境
conda deactivate 之前设定的虚拟环境的名字
```

下面是一些用于conda环境的命令

```
激活虚拟环境
conda activate 虚拟环境的名字
退出激活环境
conda deactivate
删除环境
conda renove -n 虚拟环境的名字 --all
查看当前所有的虚拟环境
conda env list
查看虚拟环境中下载的包
conda list
```

#### pytorch1.8安装

进入pytorch官网查看安装对应自身cuda的pytorch版本，pytorch官网[https://pytorch.org/get-started/previous-versions/](https://pytorch.org/get-started/previous-versions/)，找到cuda10.2对应的pytorch1.8版本  
![请添加图片描述](问题：安装ros1.assets/aa4f2f63630d44c9b996faebc2cf4d99.png)  
打开终端，激活conda环境

```
conda activate 虚拟环境的名字
输入pytorch1,8.0安装命令
conda install pytorch==1.8.0 torchvision==0.9.0 torchaudio==0.8.0 cudatoolkit=10.2 -c pytorch
安装完成后运行
python
import torch
print(torch.cuda.is_available())
若打印出True则说明安装成功
```

![请添加图片描述](问题：安装ros1.assets/2036ec5398584625a81e721e6efc6de7.png)

#### 运行yolov5

博主的yolov5用的是6.1版本的，如果各位下载其它版本可能会导致博主的权重无法适配的情况，因此各位使用yolov5的版本尽量与博主保持一致。  
首先进入github，找到yolov5-6.1分支，[https://github.com/ultralytics/yolov5/tree/v6.1](https://github.com/ultralytics/yolov5/tree/v6.1)可以看到6.1版本的运行条件是：Clone repo and install requirements.txt in a Python>=3.7.0 environment, including PyTorch>=1.7.那目前的环境是正好符合的。

##### 下载yolov5-6.1项目

```
git clone https://github.com/ultralytics/yolov5.git
```

或者也可以直接下载该分支的zip代码包

##### 安装所需库

```
cd yolov5
pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
注意:simple 不能少, 是 https 而不是 http，这里添加源用于提高下载速度
```

这些依赖项可以手动安装`pip3 install numpy==1.18.5`  
也可以`pip install -r requirements.txt`但是吧有的博主说整体安装出现报错，还真有，具体我也不太懂，我先手动安装的，最后又执行了pip install -r requirements.txt这个代码，发现是有错误，我也没管。也就这样了。大家还是手动把。



##### 下载预训练权重文件

下载yolov5s.pt,yolov5m.pt,yolov5l.pt,yolov5x.pt权重文件,并放置在weights文件夹下，  
[https://github.com/ultralytics/yolov5/releases/tag/v6.1](https://github.com/ultralytics/yolov5/releases/tag/v6.1)  
进入上述网页找到assets栏下载权重。  
![请添加图片描述](https://img-blog.csdnimg.cn/49b83dfee5e34256be99ebd945bad177.png)

##### 安装测试

打开终端

```
cd yolov5
conda activate 虚拟环境的名字
python detect.py --source ./data/images/ --weights weights/yolov5s.pt
```

跑完测试会告知你测试结果保存的路径，这里路径为runs/detect/exp10  
![请添加图片描述](https://img-blog.csdnimg.cn/d0b3d8c863564464a6488f191d572cdf.png)  
依据此路径查找到测试结果，如下图所示：  
![请添加图片描述](问题：安装ros1.assets/b23b606f33ea48b990301bb61d037add.jpeg)  
至此yolov5安装以及环境配置完毕。

#### 补充

在新建的conda环境中，需要补充安装rospkg，要不然在运行yolov5\_ros功能包的时候会报错。no model name rospkg.

```
pip install rospkg
```

#### 参考资料

1.  [Ubuntu18.04安装Anaconda(最新最全亲测图文并茂)](https://blog.csdn.net/KIK9973/article/details/118772450?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522167722683316782429799602%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=167722683316782429799602&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-3-118772450-null-null.142%5Ev73%5Econtrol,201%5Ev4%5Eadd_ask,239%5Ev2%5Einsert_chatgpt&utm_term=anaconda%E5%AE%89%E8%A3%85%E6%95%99%E7%A8%8Bubuntu18.04&spm=1018.2226.3001.4187)
2.  [yolov5-6.1，使用github镜像](https://kgithub.com/ultralytics/yolov5/tree/v6.1)
3.  [yolov5权重，使用github镜像](https://kgithub.com/ultralytics/yolov5/releases/tag/v6.1)
4.  [gazebo版本升级以及环境太暗的解决方法](https://blog.csdn.net/qq_48427527/article/details/124459006?spm=1001.2014.3001.5502)



### 以上都安装好了，接下来就是到你的YOLOV5下运行你的那个文件啦，我的是，python3 detect.py就好了，对了不要忘了这个3，要不他报错，因为默认是python2(可能我装了ROS的事把)，大家的是默认python3就好，反正我这个地方也弄了我半天，具体在另一个帖子有报错的例子。



# 问题二十三：jetson安装软件

jeston是arm架构，不是X86.所以安装软件包不一样

1，小猫安装

2，anconda安装

![image-20240621135944422](问题：安装ros1.assets/image-20240621135944422.png)



# 问题二十四：conda创建不了环境

# Conda网络报错Collecting package metadata (current_repodata.json): failed_channels: - defaults - conda-forge platform: linux-CSDN博客

使用python部署独立环境小伙伴因为网速慢没少吃苦。下面的异常你一定见过，或者似曾相识

```powershell
CondaHTTPError: HTTP 000 CONNECTION FAILED for url <https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/linux-64/qt-5.12.5-hd8c4c69_1.tar.bz2> Elapsed: - An HTTP error occurred when trying to retrieve this URL. HTTP errors are often intermittent, and a simple retry will get you on your way. Collecting package metadata (current_repodata.json): failed
```

```powershell
CondaHTTPError: HTTP 000 CONNECTION FAILED for url <https://conda.anaconda.org/conda-forge/linux-64/current_repodata.json> Elapsed: - An HTTP error occurred when trying to retrieve this URL. HTTP errors are often intermittent, and a simple retry will get you on your way. 'https://conda.anaconda.org/conda-forge/linux-6
```

解决方法

[Anaconda](https://so.csdn.net/so/search?q=Anaconda&spm=1001.2101.3001.7020)下载速度很慢，笔者换了Miniconda速度稍微好一些。但是一些资源minconda还是下载不到。经过最终寻找，笔者在清华大学镜像网站上找到设置中国镜像源的版本如下：  
#1、备份本地配置

```powershell
cp ~/.condarc ~/.condarc.bak vim ~/.condarc
```

#2、删除原来的内容，填入以下

```powershell
channels: - defaults show_channel_urls: true channel_alias: https://mirrors.tuna.tsinghua.edu.cn/anaconda default_channels: - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/pro - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2 custom_channels: conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
```

#3、清除缓存

```powershell
conda clean -i
```





# 问题二十四：启动不了仿真环境

## 问题描述：ROS:ModuleNotFoundError: No module named ‘rospkg‘_modulenotfounderror: no module named 'rospkg-CSDN博客



一般是安装了[anaconda](https://so.csdn.net/so/search?q=anaconda&spm=1001.2101.3001.7020) 导致的；

## 方法一：

不关闭[conda](https://so.csdn.net/so/search?q=conda&spm=1001.2101.3001.7020)，那么就需要安装所需的rospkg包及其他依赖：

```powershell
pip install catkin-tools rospkg pyyaml empy numpy
```

## 方法二：

首先，关闭anaconda：

```powershell
conda deactivate
```

这句话的意思就是不再使用conda的相关库以及python，用系统的python来操作；  ![image-20240622145821651](问题：安装ros1.assets/image-20240622145821651.png)
然后，再安装依赖;（已安装，不用了)

```powershell
sudo apt-get install pip
```

```powershell
pip install catkin-tools rospkg pyyaml empy numpy
```

这里可能还有一个问题：ROS使用的是python2的版本，很可能会自动寻找/usr/bin/python，这个版本是python2的版本，而你在系统下使用的pip很可能是python3的工具，这时候还是会出现 No [module](https://so.csdn.net/so/search?q=module&spm=1001.2101.3001.7020) named ‘rospkg’。

所以我们需要将 `/usr/bin/python`替换成python3的；

```powershell
sudo rm /usr/bin/python 
sudo ln -s /usr/bin/python3 /usr/bin/python
```

这时候输入python -V；输出的就是版本3 的信息；

这样问题就解决了。

另外：  
如果要需要使用conda：

```powershell
conda activate base (后面接你要激活的虚拟环境)
```





# 问题二十四：Linux下载QGC报错

### 问题描述：![image-20240622191115425](问题：安装ros1.assets/image-20240622191115425.png)

## 解决方案：下载较低版本（稳定版）

![image-20240622191230524](问题：安装ros1.assets/image-20240622191230524.png)



# 问题二十五：ubuntu18.04 USB_cam安装使用

1.安装：
---

# ubuntu利用usb_cam打开摄像头_ubuntu打开摄像头命令-CSDN博客

> ## Excerpt
> 文章浏览阅读6.4k次，点赞5次，收藏34次。一.安装摄像头驱动usb_cam想要标定多个相机，首先得把相机打开吧，usb_cam是针对usb摄像头的ros驱动包，简单来说就是得有这个功能包，才能在ros中把摄像头打开。首先打开终端，输入：sudo apt-get install ros-melodic-usb-cam这里melodic应该根据自己Ubuntu系统进行灵活变换，例如我使用的Ubuntu18.04，那么我对应的就是melodic版本。驱动安装完成之后，会自带一个launch文件，我们打开launch文件就可以打开摄_ubuntu打开摄像头命令

---
## 一.安装摄像头驱动usb\_cam

想要[标定](https://so.csdn.net/so/search?q=%E6%A0%87%E5%AE%9A&spm=1001.2101.3001.7020)多个相机，首先得把相机打开吧，usb\_cam是针对usb摄像头的ros驱动包，简单来说就是得有这个功能包，才能在ros中把摄像头打开。

首先打开终端，输入：

```csharp
sudo apt-get install ros-melodic-usb-cam
```

这里melodic应该根据自己[Ubuntu系统](https://so.csdn.net/so/search?q=Ubuntu%E7%B3%BB%E7%BB%9F&spm=1001.2101.3001.7020)进行灵活变换，例如我使用的Ubuntu18.04，那么我对应的就是melodic版本。

驱动安装完成之后，会自带一个launch文件，我们打开launch文件就可以打开摄像头。

```undefined
roslaunch usb_cam usb_cam-test.launch
```

此时，保证相机已经开机，并通过usb接口连接至电脑，则会出现以下画面，并成功打开摄像头。

![c9b07b1b67cf41a6be6988892d6f5c05.png](问题：安装ros1.assets/c9b07b1b67cf41a6be6988892d6f5c05.png)

## 二.报错： 如果报错如下select timeout

![5ad28192a60d4f718a46d325997d264a.png](问题：安装ros1.assets/5ad28192a60d4f718a46d325997d264a.png)

说明usb兼容性选择错了，需要关闭虚拟机进行更改，点击编辑虚拟机，打开usb控制器，将usb兼容性改为usb3.1，点击确定，重新打开虚拟机，再次运行即可打开摄像头。

![845dd2cf372f4aa686470df64e8acb2e.png](问题：安装ros1.assets/845dd2cf372f4aa686470df64e8acb2e.png)

### 三.报错： ERROR: cannot launch node of type [image_view/image_view]: image_viewROS path [0]=/opt/ros/noetic/s-CSDN博客

运行笔记本自带摄像头时报错。

运行命令：

```undefined
roslaunch usb_cam usb_cam-test.launch
```

报错代码：

```cobol
ERROR: cannot launch node of type [image_view/image_view]: image_view

ROS path [0]=/opt/ros/noetic/share/ros

ROS path [1]=/home/zxf/catkin_ws/src

ROS path [2]=/opt/ros/noetic/share
```

解决方法：

```sql
sudo apt-get install ros-melodic-image-view
```



# 问题二十六：训练YOLOV5

### \-整理yolov5模型

```
为了完成训练工作，我们需要将训练的图片按照指定的格式进行整理，
详细参照yolov5官方指南：
https://github.com/ultralytics/yolov5/wiki/Train-Custom-Data
```

我们首先需要建立如下的文件夹：  
![在这里插入图片描述](问题：安装ros1.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NzAxNzkx,size_16,color_FFFFFF,t_70.png)  
所有文件放在yolo\_A文件夹下，子文件夹images用来存放样本图片，labels文件夹用来存储标注信息。A.yaml文件用来存放一些目录信息和标志物分类。

我这次测试的检测哆啦A梦的头像，我采集了50张哆啦A梦的样本，放到images文件夹下：  
![在这里插入图片描述](问题：安装ros1.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NzAxNzkx,size_16,color_FFFFFF,t_70-17210756834811.png)  
接下来我们就要进行图片的标注工作了，图片标注我们用到了一个名为labelimg的工具：https://github.com/tzutalin/labelImg  



```
sudo apt-get install pyqt5-dev-tools
sudo pip3 install lxml
git clone https://github.com/tzutalin/labelImg.git
cd labelImg
make all
python3 labelImg.py  #打开labelImg
```

即可进入我们的界面中来。进入之后，首先我们先把一些选项勾上，便于我们标记。然后，最重要的是把标记模式改为yolo。  
![在这里插入图片描述](问题：安装ros1.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NzAxNzkx,size_16,color_FFFFFF,t_70-17210756834822.png)  
之后我们点击Open dir选择我们图片所在的images文件夹，选择之后会弹窗让你选择labels所在的文件夹。当然如果选错了，也可以点change save dir进行修改。

然后软件右上角我们打开这个选项，当我们标记图片后，就会自动帮我们归类到A了  
![在这里插入图片描述](问题：安装ros1.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NzAxNzkx,size_16,color_FFFFFF,t_70-17210756834823.png)

现在我们就可以开始进行标记了，常用的快捷键，用主要wad三个键

```markup
Ctrl + u Load all of the images from a directory 
Ctrl + r Change the default annotation target dir 
Ctrl + s Save Ctrl + d Copy the current label and rect box 
Ctrl + Shift + d Delete the current image Space Flag the current image as verified w Create a rect box d Next image a Previous image del Delete the selected rect box 
Ctrl++ Zoom in Ctrl-- Zoom out ↑→↓← | Keyboard arrows to move selected rect box
```

通过鼠标拖拽框选即可标注：  
![在这里插入图片描述](问题：安装ros1.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NzAxNzkx,size_16,color_FFFFFF,t_70-17210756834824.png)

所有图片标注好之后，我们再来看我们的labels文件夹，可以看到很多txt文件。每个文件都对应着我们标记的类别和框的位置：  
![在这里插入图片描述](问题：安装ros1.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NzAxNzkx,size_16,color_FFFFFF,t_70-17210756834825.png)  
最后还要做的是建立yaml文件，文件的位置也不要放错：  
![在这里插入图片描述](问题：安装ros1.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NzAxNzkx,size_16,color_FFFFFF,t_70-17210756834826.png)  
文件里面内容如下，其中train和val都是我们images的目录，labels的目录不用写进去，会自动识别。nc代表识别物体的种类数目，names代表种类名称，如果多个物体种类识别的话，可以自行增加。

```markup
# train and val data as 1) directory: path/images/, 2) file: path/images.txt, or 3) list: [path1/images/, path2/images/] train: ../yolo_A/images/ val: ../yolo_A/images/ # number of classes nc: 1 # class names names: ['A meng']
```

到目前，我们的训练的材料就已经准备好了。

### \-yolov5模型训练（租服务器训练）（看哔哩哔哩视频）

```python
git clone https://github.com/ultralytics/yolov5 # clone repo %cd yolov5 
pip install -qr requirements.txt # install dependencies
```

上传数据集压缩包并解压

```python
unrar x ../yolo_A ../
```

然后一下代码可以测试能否正常工作，顺带会下载yolov5s.pt文件，这个文件后面训练的时候会用到

```python
python detect.py --weights yolov5s.pt --img 640 --conf 0.25 --source data/images/ Image(filename='runs/detect/exp/zidane.jpg', width=600)
```

如果一切正常会显示如下图  
![在这里插入图片描述](问题：安装ros1.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NzAxNzkx,size_16,color_FFFFFF,t_70-17210756834837.png)  
接下来就要开始训练模型了：

```python
python train.py --img 640 --batch 50 --epochs 100 --data ../yolo_A/A.yaml --weights yolov5s.pt --nosave --cache
```

训练完成后，我们可以看到训练结果保存的位置：  
![在这里插入图片描述](问题：安装ros1.assets/20210223190940761.png)  
在对应exp文件下可以看到用训练集做预测的结果：

```python
Image(filename='runs/train/exp2/test_batch0_pred.jpg', width=800) # test batch 0 predictions
```

现在我们用训练出来的结果找一张网图做测试（文件名和导出预测文件地址不一定相同，但是相似，大家自行寻找）

```python
python detect.py --weights /content/yolov5/runs/train/exp2/weights/best.pt --img 640 --conf 0.25 --source ../test2.jpg Image(filename='runs/detect/exp4/test2.jpg', width=600)
```

![在这里插入图片描述](问题：安装ros1.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NzAxNzkx,size_16,color_FFFFFF,t_70-17210756834838.png)









# 问题二十七：配置仿真环境运行.launch文件显示not found

## 问题描述：Error info:
/opt/ros/noetic/lib/robot_localization/navsat_transform_node: error while loading shared libraries: libGeographic.so.19: cannot open shared object file: No such file or directory
log4cxx: Could not read configuration file [/home/zz/??????/cpp_project/LIO_SAM_ws/src/LIO-SAM/launch/include/rosconsole/rosconsole_error.conf].
process[lio_sam_rviz-9]: started with pid [53535]
[navsat-8] process has died [pid 53530, exit code 127, cmd /opt/ros/noetic/lib/robot_localization/navsat_transform_node imu/data:=imu_correct gps/fix:=gps/fix odometry/filtered:=odometry/navsat __name:=navsat __log:=/home/zz/.ros/log/a1ca73aa-332c-11ec-ba59-178e13b8db7e/navsat-8.log].
log file: /home/zz/.ros/log/a1ca73aa-332c-11ec-ba59-178e13b8db7e/navsat-8*.log



"符号连接的层数过多" 错误通常表示符号链接存在循环，导致系统在尝试访问文件时陷入无限循环。以下是解决这个问题的步骤：

### 1. 删除所有相关符号链接

首先，找到并删除与 `libGeographic.so` 相关的所有符号链接，以避免循环：

```bash
sudo find /usr/lib/x86_64-linux-gnu -name 'libGeographic.so*' -exec rm -f {} +
```

### 2. 确保正确的库文件存在

确保实际的库文件存在而不是符号链接。你之前提到的库文件路径是 `/usr/lib/x86_64-linux-gnu/libGeographic.so.19`，所以检查这个文件是否存在并且不是一个符号链接：

```bash
ls -l /usr/lib/x86_64-linux-gnu/libGeographic.so.19
```

### 3. 重新创建正确的符号链接

根据实际的库文件，重新创建正确的符号链接：

```bash
sudo ln -s /usr/lib/x86_64-linux-gnu/libGeographic.so.19 /usr/lib/x86_64-linux-gnu/libGeographic.so
```

### 4. 更新共享库缓存

更新共享库缓存：

```bash
sudo ldconfig
```

### 5. 设置 `LD_LIBRARY_PATH` 环境变量

确认并设置 `LD_LIBRARY_PATH` 环境变量：

```bash
export LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH
```

### 6. 验证配置

尝试运行 `GeoConvert` 命令来验证配置是否生效：

```bash
GeoConvert --version
```

### 检查并重置

如果问题仍然存在，检查系统中是否存在其他 `libGeographic.so` 相关的符号链接并删除：

```bash
sudo find /usr -name 'libGeographic.so*' -exec rm -f {} +
```

然后，重新安装 `libgeographic-dev` 包：

```bash
sudo apt-get update
sudo apt-get install --reinstall libgeographic-dev
```

### 总结

通过这些步骤，你应该能够解决 `libGeographic.so.19` 库文件找不到的问题。如果问题仍然存在，请提供详细的 `ls -l /usr/lib/x86_64-linux-gnu/libGeographic.so*` 输出以便进一步诊断。



重新安装后sz@sz:~$ locate libGeographic.so.19 

/usr/lib/x86_64-linux-gnu/libGeographic.so.19 

sz@sz:~$ ls -l /usr/lib/x86_64-linux-gnu/libGeographic.so.19 

ls: 无法访问 '/usr/lib/x86_64-linux-gnu/libGeographic.so.19': 没有那个文件或目录 

sz@sz:~$ GeoConvert --version 

GeoConvert: error while loading shared libraries: libGeographic.so.19: cannot open shared object file: No such file or directory



既然 `locate` 命令显示 `/usr/lib/x86_64-linux-gnu/libGeographic.so.19` 存在，但 `ls` 命令显示没有这个文件，这可能是文件系统或数据库的问题。我们可以按照以下步骤来解决这个问题。

### 1. 更新文件数据库

首先，确保文件数据库是最新的：
```bash
sudo updatedb
```

### 2. 重新查找文件

再次使用 `locate` 命令查找文件：
```bash
locate libGeographic.so.19
```

### 3. 确认实际文件位置

检查是否有其他位置的 `libGeographic.so.19` 文件。如果有，使用以下命令确认实际文件位置：
```bash
find /usr -name 'libGeographic.so*'
```

sz@sz:~$ find /usr -name 'libGeographic.so*' 

/usr/lib/x86_64-linux-gnu/libGeographic.so



从输出中可以看到，`/usr/lib/x86_64-linux-gnu/` 目录下仅存在 `libGeographic.so`，但没有 `libGeographic.so.19`。这可能意味着 `libGeographic.so.19` 确实未正确安装或符号链接有问题。

### 1. 检查 `libgeographic` 包的内容

首先，检查 `libgeographic` 包的内容，确保它确实包含所需的库文件：
```bash
dpkg -L libgeographic-dev
```

通过这些步骤，你应该能够解决 `GeoConvert` 程序无法找到 `libGeographic.so.19` 库文件的问题。如果问题仍然存在，请提供 `dpkg -L libgeographic-dev` 的输出信息以便进一步诊断。



sz@sz:~$ dpkg -L libgeographic-dev
/.
/usr
/usr/include
/usr/include/GeographicLib
/usr/include/GeographicLib/Accumulator.hpp
/usr/include/GeographicLib/AlbersEqualArea.hpp
/usr/include/GeographicLib/AzimuthalEquidistant.hpp
/usr/include/GeographicLib/CassiniSoldner.hpp
/usr/include/GeographicLib/CircularEngine.hpp
/usr/include/GeographicLib/Config.h
/usr/include/GeographicLib/Constants.hpp
/usr/include/GeographicLib/DMS.hpp
/usr/include/GeographicLib/Ellipsoid.hpp
/usr/include/GeographicLib/EllipticFunction.hpp
/usr/include/GeographicLib/GARS.hpp
/usr/include/GeographicLib/GeoCoords.hpp
/usr/include/GeographicLib/Geocentric.hpp
/usr/include/GeographicLib/Geodesic.hpp
/usr/include/GeographicLib/GeodesicExact.hpp
/usr/include/GeographicLib/GeodesicLine.hpp
/usr/include/GeographicLib/GeodesicLineExact.hpp
/usr/include/GeographicLib/Geohash.hpp
/usr/include/GeographicLib/Geoid.hpp
/usr/include/GeographicLib/Georef.hpp
/usr/include/GeographicLib/Gnomonic.hpp
/usr/include/GeographicLib/GravityCircle.hpp
/usr/include/GeographicLib/GravityModel.hpp
/usr/include/GeographicLib/LambertConformalConic.hpp
/usr/include/GeographicLib/LocalCartesian.hpp
/usr/include/GeographicLib/MGRS.hpp
/usr/include/GeographicLib/MagneticCircle.hpp
/usr/include/GeographicLib/MagneticModel.hpp
/usr/include/GeographicLib/Math.hpp
/usr/include/GeographicLib/NearestNeighbor.hpp
/usr/include/GeographicLib/NormalGravity.hpp
/usr/include/GeographicLib/OSGB.hpp
/usr/include/GeographicLib/PolarStereographic.hpp
/usr/include/GeographicLib/PolygonArea.hpp
/usr/include/GeographicLib/Rhumb.hpp
/usr/include/GeographicLib/SphericalEngine.hpp
/usr/include/GeographicLib/SphericalHarmonic.hpp
/usr/include/GeographicLib/SphericalHarmonic1.hpp
/usr/include/GeographicLib/SphericalHarmonic2.hpp
/usr/include/GeographicLib/TransverseMercator.hpp
/usr/include/GeographicLib/TransverseMercatorExact.hpp
/usr/include/GeographicLib/UTMUPS.hpp
/usr/include/GeographicLib/Utility.hpp
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/libGeographic.a
/usr/lib/x86_64-linux-gnu/pkgconfig
/usr/lib/x86_64-linux-gnu/pkgconfig/geographiclib.pc
/usr/share
/usr/share/cmake
/usr/share/cmake/geographiclib
/usr/share/cmake/geographiclib/FindGeographicLib.cmake
/usr/share/doc
/usr/share/doc/libgeographic-dev
/usr/share/doc/libgeographic-dev/copyright
/usr/share/doc/libgeographic-dev/examples
/usr/share/doc/libgeographic-dev/examples/GeoidToGTX.cpp
/usr/share/doc/libgeographic-dev/examples/JacobiConformal.cpp
/usr/share/doc/libgeographic-dev/examples/JacobiConformal.hpp.gz
/usr/share/doc/libgeographic-dev/examples/example-Accumulator.cpp
/usr/share/doc/libgeographic-dev/examples/example-AlbersEqualArea.cpp
/usr/share/doc/libgeographic-dev/examples/example-AzimuthalEquidistant.cpp
/usr/share/doc/libgeographic-dev/examples/example-CassiniSoldner.cpp
/usr/share/doc/libgeographic-dev/examples/example-CircularEngine.cpp
/usr/share/doc/libgeographic-dev/examples/example-Constants.cpp
/usr/share/doc/libgeographic-dev/examples/example-DMS.cpp
/usr/share/doc/libgeographic-dev/examples/example-Ellipsoid.cpp
/usr/share/doc/libgeographic-dev/examples/example-EllipticFunction.cpp
/usr/share/doc/libgeographic-dev/examples/example-GARS.cpp
/usr/share/doc/libgeographic-dev/examples/example-GeoCoords.cpp
/usr/share/doc/libgeographic-dev/examples/example-Geocentric.cpp
/usr/share/doc/libgeographic-dev/examples/example-Geodesic-small.cpp
/usr/share/doc/libgeographic-dev/examples/example-Geodesic.cpp
/usr/share/doc/libgeographic-dev/examples/example-GeodesicExact.cpp
/usr/share/doc/libgeographic-dev/examples/example-GeodesicLine.cpp
/usr/share/doc/libgeographic-dev/examples/example-GeodesicLineExact.cpp
/usr/share/doc/libgeographic-dev/examples/example-GeographicErr.cpp
/usr/share/doc/libgeographic-dev/examples/example-Geohash.cpp
/usr/share/doc/libgeographic-dev/examples/example-Geoid.cpp
/usr/share/doc/libgeographic-dev/examples/example-Georef.cpp
/usr/share/doc/libgeographic-dev/examples/example-Gnomonic.cpp
/usr/share/doc/libgeographic-dev/examples/example-GravityCircle.cpp
/usr/share/doc/libgeographic-dev/examples/example-GravityModel.cpp
/usr/share/doc/libgeographic-dev/examples/example-LambertConformalConic.cpp
/usr/share/doc/libgeographic-dev/examples/example-LocalCartesian.cpp
/usr/share/doc/libgeographic-dev/examples/example-MGRS.cpp
/usr/share/doc/libgeographic-dev/examples/example-MagneticCircle.cpp
/usr/share/doc/libgeographic-dev/examples/example-MagneticModel.cpp
/usr/share/doc/libgeographic-dev/examples/example-Math.cpp
/usr/share/doc/libgeographic-dev/examples/example-NearestNeighbor.cpp.gz
/usr/share/doc/libgeographic-dev/examples/example-NormalGravity.cpp
/usr/share/doc/libgeographic-dev/examples/example-OSGB.cpp
/usr/share/doc/libgeographic-dev/examples/example-PolarStereographic.cpp
/usr/share/doc/libgeographic-dev/examples/example-PolygonArea.cpp
/usr/share/doc/libgeographic-dev/examples/example-Rhumb.cpp
/usr/share/doc/libgeographic-dev/examples/example-RhumbLine.cpp
/usr/share/doc/libgeographic-dev/examples/example-SphericalEngine.cpp
/usr/share/doc/libgeographic-dev/examples/example-SphericalHarmonic.cpp
/usr/share/doc/libgeographic-dev/examples/example-SphericalHarmonic1.cpp
/usr/share/doc/libgeographic-dev/examples/example-SphericalHarmonic2.cpp
/usr/share/doc/libgeographic-dev/examples/example-TransverseMercator.cpp
/usr/share/doc/libgeographic-dev/examples/example-TransverseMercatorExact.cpp
/usr/share/doc/libgeographic-dev/examples/example-UTMUPS.cpp
/usr/share/doc/libgeographic-dev/examples/example-Utility.cpp
/usr/share/doc/libgeographic-dev/examples/make-egmcof.cpp
/usr/lib/x86_64-linux-gnu/libGeographic.so
/usr/share/doc/libgeographic-dev/changelog.Debian.gz

-----

从 `dpkg -L libgeographic-dev` 的输出中，我们可以看到 `/usr/lib/x86_64-linux-gnu/libGeographic.so` 是实际存在的库文件，但没有 `libGeographic.so.19`。

### 解决步骤：

1. **确认实际库文件是否存在：**
   - `/usr/lib/x86_64-linux-gnu/libGeographic.so` 是存在的库文件。
   - 确保这个文件没有问题：
     ```bash
     ls -l /usr/lib/x86_64-linux-gnu/libGeographic.so
     ```

这些步骤应该可以解决 `GeoConvert` 程序无法找到 `libGeographic.so.19` 库文件的问题。如果问题仍然存在，请提供 `ls -l /usr/lib/x86_64-linux-gnu/libGeographic.so` 的输出信息以便进一步诊断。

--------

sz@sz:~$ ls -l /usr/lib/x86_64-linux-gnu/libGeographic.so

rwxrwxrwx 1 root root 23 3月  24  2020 /usr/lib/x86_64-linux-gnu/libGeographic.so -> libGeographic.so.19.0.1

--------

从输出中可以看到 `/usr/lib/x86_64-linux-gnu/libGeographic.so` 实际上是一个符号链接，指向 `libGeographic.so.19.0.1`。这意味着 `libGeographic.so.19.0.1` 文件应该存在于 `/usr/lib/x86_64-linux-gnu/` 目录下，但没有单独的 `libGeographic.so.19` 符号链接。

### 解决步骤

1. **检查 `libGeographic.so.19.0.1` 文件是否存在**

   确认实际库文件 `libGeographic.so.19.0.1` 是否存在：
   ```bash
   ls -l /usr/lib/x86_64-linux-gnu/libGeographic.so.19.0.1
   ```


通过这些步骤，你应该能够解决 `GeoConvert` 程序无法找到 `libGeographic.so.19` 库文件的问题。如果问题仍然存在，请提供 `ls -l /usr/lib/x86_64-linux-gnu/libGeographic.so.19.0.1` 的输出信息以便进一步诊断。

-----

sz@sz:~$ ls -l /usr/lib/x86_64-linux-gnu/libGeographic.so.19.0.1 ls: 无法访问 '/usr/lib/x86_64-linux-gnu/libGeographic.so.19.0.1': 没有那个文件或目录

-----

从输出信息可以确认，虽然有符号链接指向 `libGeographic.so.19.0.1`，但实际的文件不存在。这就是 `GeoConvert` 无法找到 `libGeographic.so.19` 的原因。

1. **重新安装 `libgeographic` 库**
   ```bash
   sudo apt-get update
   sudo apt-get install --reinstall libgeographic19 libgeographic-dev
   ```

2. **检查安装结果**
   ```bash
   ls -l /usr/lib/x86_64-linux-gnu/libGeographic.so*
   ```


通过这些步骤，你应该能够解决 `GeoConvert` 程序无法找到 `libGeographic.so.19` 库文件的问题。如果问题仍然存在，请提供 `ls -l /usr/lib/x86_64-linux-gnu/libGeographic.so*` 的输出信息以便进一步诊断。

----

sz@sz:~$ ls -l /usr/lib/x86_64-linux-gnu/libGeographic.so*

 lrwxrwxrwx 1 root root     23 3月  24  2020 /usr/lib/x86_64-linux-gnu/libGeographic.so -> libGeographic.so.19.0.1 lrwxrwxrwx 1 root root     23 3月  24  2020 /usr/lib/x86_64-linux-gnu/libGeographic.so.19 -> libGeographic.so.19.0.1 -rw-r--r-- 1 root root 705096 3月  24  2020 /usr/lib/x86_64-linux-gnu/libGeographic.so.19.0.1

----

从输出中可以看到，`libGeographic.so.19.0.1` 文件确实存在，并且符号链接 `libGeographic.so` 和 `libGeographic.so.19` 都正确指向该文件。

### 更新共享库缓存
确保系统更新了共享库缓存：
```bash
sudo ldconfig
```

### 验证配置
再次尝试运行 `GeoConvert` 命令来验证配置是否生效：
```bash
GeoConvert --version
```

结束

----

### 如果仍然报错

如果仍然报错，请检查以下几点：

1. **确保库路径被系统识别**
   - 确认 `/usr/lib/x86_64-linux-gnu` 路径在系统的库路径中。编辑 `/etc/ld.so.conf` 文件（如果不存在，可以创建），确保其中包含这一行：
     ```
     /usr/lib/x86_64-linux-gnu
     ```
   - 运行 `ldconfig` 更新库缓存：
     ```bash
     sudo ldconfig
     ```

2. **检查库文件的权限**
   - 确认库文件的权限是否正确：
     ```bash
     sudo chmod 755 /usr/lib/x86_64-linux-gnu/libGeographic.so.19.0.1
     ```

### 验证 LD_LIBRARY_PATH

你也可以临时设置 `LD_LIBRARY_PATH` 变量以确保库路径被识别：
```bash
export LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH
GeoConvert --version
```

### 示例步骤

1. **更新共享库缓存**
   ```bash
   sudo ldconfig
   ```

2. **验证配置**
   ```bash
   GeoConvert --version
   ```

3. **确保库路径被系统识别**
   - 编辑 `/etc/ld.so.conf` 文件，确保包含：
     ```
     /usr/lib/x86_64-linux-gnu
     ```
   - 更新库缓存：
     ```bash
     sudo ldconfig
     ```

4. **检查库文件的权限**
   ```bash
   sudo chmod 755 /usr/lib/x86_64-linux-gnu/libGeographic.so.19.0.1
   ```

5. **临时设置 `LD_LIBRARY_PATH` 变量**
   ```bash
   export LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH
   GeoConvert --version
   ```

通过这些步骤，你应该能够解决 `GeoConvert` 程序无法找到 `libGeographic.so.19` 库文件的问题。如果问题仍然存在，请提供 `GeoConvert --version` 的输出信息以便进一步诊断。



# 问题二十八

**使用 conda 安装 `gdal`**： 使用 conda 来管理环境和依赖关系，避免与系统库冲突。首先创建一个新的 conda 环境，然后在该环境中安装 `gdal`。

```
conda install -c conda-forge gdal
```



# 问题二十九：在安装conda之前可以运行XTDrone的键盘控制无人机代码，安装conda后运行无人机键盘控制代码无反应，退出conda环境后运行又可以了

## 问题描述：在conda环境中运行无人机键盘控制代码无反应

![image-20240827130142191](/home/sz/.config/Typora/typora-user-images/image-20240827130142191.png)

#### 问题分析：python环境不一样。在conda和本地环境运行communication无影响，但是在conda运行keyboard有影响，本地环境运行keyboard无影响。所以用本地环境的python来运行keyboard代码

#### 解决方法一：

先查找到本地环境中python的位置

```
conda deactivate
which python
```

然后使用本地环境的python来运行代码

```
/usr/bin/python multirotor_keyboard_control.py iris 1 vel
```

#### ![image-20240827130349919](/home/sz/.config/Typora/typora-user-images/image-20240827130349919.png)

## 解决方法二：取消conda的默认启动

**打开终端。** **输入命令：**

```
conda config --set auto_activate_base false
```

 这将把auto_activate_base参数设置为false，从而取消conda的默认启动

