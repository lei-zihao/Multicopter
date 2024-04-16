mavlink stream -d /dev/ttyACM0 -s HIGHRES_IMU -r 200



<<<<<<< Updated upstream

# 知识点1：查找ros发行版本
```
echo $ROS_DISTRO
```
```
melodic
```
或用
```
printenv | grep ROS
```
查看更详细的信息
[image-20231210171930505.png](https://postimg.cc/5jFZ85jh)








# 知识点2：操作



## 基本规律

### 1、node、topic、server

话题：发送指令动作（半双工/单向）

服务：生成，删除小海龟（双工/双向）

参数：背景颜色

```
rosnode list
rosetopic pub [话题eg：cmd_vel] （tab） [信息类型，tab可自动补全] （tab) [调参]
rosserver call [服务eg：/call  /spawn] （tab看是否有参数）
rosparam set
```



### 2、bag文件

*下面所有的命令中，前面都有一个`time`，这样做可以同时输出执行每个命令花费的时间，而且有时这些命令需要很长时间，因此使用`time`命令了解给定命令所需的时间是有必要的。如果您不想使用它，可以放心删除下面任何命令中的`time`。*

#### 1、记录（创建）

##### 1、全部

```
rosbag record -a
```

##### 2、部分

```
rosbag record -O subset /turtle1/cmd_vel /turtle1/pose
```

上述命令中的-O参数告诉rosbag record将数据记录到名为subset.bag的文件中，而后面的topic参数告诉rosbag record只能订阅这两个指定的话题。然后通过键盘控制乌龟随意移动几秒钟，最后按Ctrl+C退出rosbag record命令。

#### 2、查找

```
rosbag info <your bagfile>
```



#### 3、使用运行

1、-r 2   （速率）

```
time rosbag play -r 2 <your bagfile> 
```

2、（使用`--immediate`选项），**只**会发布我们感兴趣的话题。

```
time rosbag play --immediate demo.bag --topics /topic1 /topic2 /topic3 /topicN
```







# 知识点3：launch文件

## parameter和arg

![image-20231212112004664](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20231212112004664.png)

[![image-20231212112004664.png](https://i.postimg.cc/XYZdfwD0/image-20231212112004664.png)](https://postimg.cc/fVNVZ0NH)

## 注释

### 1、单行注释

```
      <!--      

      注释内容（无其他注释符）

      -->

```

###    2、多行注释

```
 <![CDATA[                
注释内容（包含其他注释符）     
     ]]>
```

## 举例：

![image-20240312131329555](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/image-20240312131329555.png)





# 知识点4：msg和srv的创建、配置、使用

## 1、创建文件夹msg/srv（在功能包下）

![image-20231213002650797](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20231213002650797.png)

## 2、在文件夹里添加消息或服务文档（一种结构体）

![image-20231213003105159](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20231213003105159.png)

![image-20231213003002417](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20231213003002417.png)

## 3、修改package.xml里的依赖（为了使信息和服务可随便变为c或python文件格式）**（难）**

package.xml自带依赖？？？，用于给cmake.list添加依赖？？？

![image-20231213003601983](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20231213003601983.png)

## 4、添加依赖进cmake.list文件里

### 1、添加依赖message_generation（对msg和srv都成立）到find_package（）函数

![](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20231213004038538.png)

### 2、修改服务字段？？？

### ![image-20231213005620733](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20231213005620733.png)

=======





# 知识点五：创建和启动ros功能包

# 一、创建ros功能包

## 1、创建工作空间并初始化(src下)

```
mkdir -p ~/my_ws/src
cd ~/my_ws/src
catkin_init_workspace
```

## 2、创建功能包(src下)

### 在 `~/my_ws/src 中` 目录创建一个新包，名为 `offboard_py` (在这种情况下) 依赖 `rospy` ：

```
catkin_create_pkg    offboard_py   rospy roscpp
```

## 3、编译（在工作空间my_ws下）

```
cd ~/my_ws/
catkin_make
```

## 4、配置环境

```
source ~/my_ws/devel/setup.bash
```

# 二、编写python文件

## 1、在功能包里创建scripts文件夹储存文件

```
roscd offboard_py
mkdir scripts
cd scripts
```

## 2、创建python文件并使其有可执行权限

```
touch offb_node.py
chmod +x offb_node.py
```

# 三、用launch文件运行功能包

## 1、创建launch文件（在功能包下）

```
cd ~/my_ws/src/offboard_py/src
roscd offboard_py
mkdir launch
cd launch
touch start_offb.launch
```

launch文件eg：

```xml
<launch>
    <arg name="world_path" default="$(find simulation)/worlds/empty.world" />
    <arg name="gui" default="true"/>
    <arg name="ns" default="/"/>
    <arg name="model" default="iris_irlock_camera"/>
    <arg name="fcu_url" default="udp://:14540@localhost:14557"/>
    <arg name="gcs_url" default="" />   <!-- GCS link is provided by SITL -->
    <arg name="tgt_system" default="1" />
    <arg name="tgt_component" default="1" />
    <arg name="vehicle" default="iris"/>

    <param name="use_sim_time" value="true" />


    <!-- Launch PX4 SITL -->
    <include file="$(find px4)/launch/px4.launch">
        <arg name="vehicle" value="$(arg vehicle)"/>
    </include>

    <!-- Launch MavROS -->
    <include file="$(find mavros)/launch/px4.launch">   
         <!-- Need to change the config file to get the tf topic and get local position in terms of local origin -->
         <arg name="fcu_url" value="$(arg fcu_url)" />
    </include>

    <!-- Launch Gazebo -->
    <include file="$(find gazebo_ros)/launch/empty_world.launch">
        <arg name="gui" value="$(arg gui)"/>
        <arg name="world_name" value="$(arg world_path)" />
    </include>

    <!-- Spawn vehicle model -->
    <node name="spawn_model" pkg="gazebo_ros" type="spawn_model" output="screen"
          args="-sdf -database $(arg model) -model $(arg vehicle)">
    </node>

    <node name="ros_study_offnode" pkg="px4_simu" type="px4_simu_node" output="screen">
    </node>

</launch>

```



## 2、启动launch文件

```
roslaunched offboard_py start_offb.launch
```

>>>>>>> Stashed changes



# 知识点六：VMware+Ubuntu18.04 磁盘扩容

## 1、首先，需要将虚拟机关机。

## 2、进入到虚拟机的设置界面，如下图:

![在这里插入图片描述](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpbnV4X2VtYmVkZGVk,size_16,color_FFFFFF,t_70.png)

## 3、进入磁盘扩展界面，如下，修改扩展后的磁盘容量为:41G，保存。

![在这里插入图片描述](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpbnV4X2VtYmVkZGVk,size_16,color_FFFFFF,t_70-17044583026872.png)

![在这里插入图片描述](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpbnV4X2VtYmVkZGVk,size_16,color_FFFFFF,t_70-17044583081204.png)

# Gparted合并磁盘空间

## 1、Ubuntu默认情况下是没有安装Gparted工具的，需要自行安装。安装命令如下：

```
sudo apt-get install gparted
```

## 2、gparted需要root权限，执行如下命令进入gparted的配置界面:

```
sudo gparted
```

## 3、首先，看一下，扩容前的磁盘使用情况:

![在这里插入图片描述](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/20190125092417735.png)

## 4、gparted列出了当前系统的磁盘的所有分区情况，可以看到刚才我们刚刚扩展的分区，显示未使用的状态，如图:

## 5、我们所要做的就是将这部分磁盘空间合并到第一个分区中，我们编辑一下第一个分区，右键，选择更改大小，如图:

## 6、调整磁盘大小到最大，如图:![在这里插入图片描述](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpbnV4X2VtYmVkZGVk,size_16,color_FFFFFF,t_70-17044584820727.png)

## 7、点击，上方的确认执行按钮，执行磁盘扩容操作，如图:![在这里插入图片描述](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpbnV4X2VtYmVkZGVk,size_16,color_FFFFFF,t_70-17044584895549.png)

## 8、稍等片刻，扩容成功，如图:![在这里插入图片描述](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpbnV4X2VtYmVkZGVk,size_16,color_FFFFFF,t_70-170445849560411.png)

## 9、再次查看系统系统分区信息，如图:![在这里插入图片描述](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/20190125092618438.png)

# 总结

## 通过上面的步骤，大家看到了我们使用vmware和gparted可以轻松的完成Ubuntu分区的磁盘空间扩容操作，原来磁盘扩容可以这么简单。









# 知识点七：使用特定配置和初始化文件调用 make 的完整语法为：

```
make [VENDOR_][MODEL][_VARIANT] [VIEWER_MODEL_DEBUGGER_WORLD]、
```

比如

```
make px4_sitl_default gazebo
```

## **VENDOR_MODEL_VARIANT：（又称 `CONFIGURATION_TARGET` ）****

```
make list_config_targets（获取所有可用 CONFIGURATION_TARGET 选项的列表：）
```

### 1、**VENDOR**供应商：**板子的制造商： `px4` 、、、 `airmind` `atlflight` 、 `auav` `beaglebone` `intel` `nxp` `aerotenna` 等。Pixhawk 系列主板的供应商名称是 `px4` 。**

### 2、**MODEL**：板模型“model”：、、 `fmu-v3` 、、 `fmu-v4` `fmu-v5` `navio2` `fmu-v2` 、 `sitl` 等。

### **3、VARIANT**：**表示特定配置：例如 `bootloader` ， `cyphal` 其中包含配置中不存在的 `default` 组件。最常见的是 `default` ，可以省略。**

## **VIEWER_MODEL_DEBUGGER_WORLD：**

### 1、查看器：这是要启动和连接的模拟器（“查看器”）： `gz` 、、 `gazebo` `jmavsim` `none` 、

## 比如

```
cd PX4-Firmware
make px4_fmu-v5_default
```

构建目标 `px4_fmu-v4` 的第一部分表示固件的目标飞行控制器硬件。在本例 `_default` 中，后缀表示固件配置，例如支持或省略特定功能。



# 知识点八：无人机架构

![image-20240128221241900](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/image-20240128221241900.png)



# 知识点九：启动mavros

## 1、找到mavros的启动文件

```
roscd mavros
cd launch/
sudo gedit px4.launch
```

![image-20240310203424392](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/image-20240310203424392.png)

## 2、选择哪个串口进行mavros通信（telem1、2、3）

![image-20240310203846649](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/image-20240310203846649.png)

## 3、找到所选串口的波特率和端口名称

### 1、串口波特率：

![image-20240310204543892](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/image-20240310204543892.png)

### 2、端口名称：

```
/dev
ls
```

### 3、修改launch文件（sudo gedit px4.launch）

```
	（比如）<arg name="fcu_url" default="/dev/ttyUSB0:115200" />
```

## 4.加权限

```
sudo chmod 777 /dev/ttyUSB0
```

## 5、启动mavros

```
roslaunch mavros px4.launch 
```



# 知识点10：发布者，订阅者，服务端，客户端的python编写

## 1、发布者（无回调函数，但有队列长度）

```python
   1 #!/usr/bin/env python
   2 # license removed for brevity
   3 import rospy
   4 from std_msgs.msg import String
   5 
   6 def talker():
   7     pub = rospy.Publisher('chatter', String, queue_size=10)
   8     rospy.init_node('talker', anonymous=True)
   9     rate = rospy.Rate(10) # 10hz

  10     while not rospy.is_shutdown():
  11         hello_str = "hello world %s" % rospy.get_time()
  12         rospy.loginfo(hello_str)
  13         pub.publish(hello_str)
  14         rate.sleep()
  15 
  16 if __name__ == '__main__':
  17     try:
  18         talker()
  19     except rospy.ROSInterruptException:
  20         pass
```

## 2、订阅者(有回调函数，等待发布者发布，调用用spin（)）

```python
 def state_cb(msg):
    global current_state
    current_state = msg

 state_sub = rospy.Subscriber("mavros/state", States, callback = state_cb)
```

```python
   1 #!/usr/bin/env python
   2 import rospy
   3 from std_msgs.msg import String
   4 
   5 def callback(data):
   6     rospy.loginfo(rospy.get_caller_id() + "I heard %s", data.data)
   7     
   8 def listener():
   9 
  10     # In ROS, nodes are uniquely named. If two nodes with the same
  11     # name are launched, the previous one is kicked off. The
  12     # anonymous=True flag means that rospy will choose a unique
  13     # name for our 'listener' node so that multiple listeners can
  14     # run simultaneously.
  15     rospy.init_node('listener', anonymous=True)
  16 
  17     rospy.Subscriber("chatter", String, callback)
  18 
  19     # spin() simply keeps python from exiting until this node is stopped
  20     rospy.spin()
  21 
  22 if __name__ == '__main__':
  23     listener()
```

## 3、服务端

```python
   1 #!/usr/bin/env python
   2 
   3 from __future__ import print_function
   4 
   5 from beginner_tutorials.srv import AddTwoInts,AddTwoIntsResponse
   6 import rospy
   7 
   8 def handle_add_two_ints(req):
   9     print("Returning [%s + %s = %s]"%(req.a, req.b, (req.a + req.b)))
  10     return AddTwoIntsResponse(req.a + req.b)
  11 
  12 def add_two_ints_server():
  13     rospy.init_node('add_two_ints_server')
  14     s = rospy.Service('add_two_ints', AddTwoInts, handle_add_two_ints)
  15     print("Ready to add two ints.")
  16     rospy.spin()
  17 
  18 if __name__ == "__main__":
  19     add_two_ints_server()
```

## 4、客户端

```python
   1 #!/usr/bin/env python
   2 
   3 from __future__ import print_function
   4 
   5 import sys
   6 import rospy
   7 from beginner_tutorials.srv import *
   8 
   9 def add_two_ints_client(x, y):
  10     rospy.wait_for_service('add_two_ints')
  11     try:
  12         add_two_ints = rospy.ServiceProxy('add_two_ints', AddTwoInts)
  13         resp1 = add_two_ints(x, y)
  14         return resp1.sum
  15     except rospy.ServiceException as e:
  16         print("Service call failed: %s"%e)
  17 
  18 def usage():
  19     return "%s [x y]"%sys.argv[0]
  20 
  21 if __name__ == "__main__":
  22     if len(sys.argv) == 3:
  23         x = int(sys.argv[1])
  24         y = int(sys.argv[2])
  25     else:
  26         print(usage())
  27         sys.exit(1)
  28     print("Requesting %s+%s"%(x, y))
  29     print("%s + %s = %s"%(x, y, add_two_ints_client(x, y)))
```

## 5、总结

```
   7     pub = rospy.Publisher('chatter', String, queue_size=10)
  17     rospy.Subscriber("chatter", String, callback)
  14     s = rospy.Service('add_two_ints', AddTwoInts, handle_add_two_ints)
  12     add_two_ints = rospy.ServiceProxy('add_two_ints', AddTwoInts)

```





# 知识点十：vim的使用

### 打开 Vim 编辑器：

1. 在终端中输入以下命令以编辑一个新文件：
   ```bash
   vim filename
   ```
   其中 `filename` 是你想要编辑的文件名。

2. 如果文件不存在，Vim 将会创建一个新文件，并将其命名为 `filename`；如果文件已经存在，Vim 将会打开该文件以供编辑。

### Vim 的工作模式：

1. **普通模式（Normal mode）**：用于移动光标、复制、粘贴、删除等操作。在这个模式下，按下的键会被解释为命令。

2. **插入模式（Insert mode）**：用于输入文本。按下 `i` 键进入插入模式。

3. **命令行模式（Command-line mode）**：用于保存文件、退出编辑器、搜索等操作。按下 `:` 键进入命令行模式。

### 常用命令：

1. **保存文件并退出**：
   - 在普通模式下，输入 `:wq` 并按下回车键。

2. **退出不保存**：
   - 在普通模式下，输入 `:q!` 并按下回车键。

3. **在插入模式和普通模式之间切换**：
   - 按下 `Esc` 键。

4. **撤销上一步操作**：
   - 在普通模式下，按下 `u` 键。

5. **复制、粘贴**：
   - 在普通模式下，按下 `v` 进入可视模式，选择文本，然后按下 `y` 复制（或者 `d` 剪切）。移动光标到目标位置，按下 `p` 粘贴。

6. **移动光标**：
   - 使用 `h`（左）、`j`（下）、`k`（上）、`l`（右）键进行光标的移动。

7. **搜索文本**：
   - 在普通模式下，按下 `/` 键，输入要搜索的文本，然后按下回车键。

以上是 Vim 编辑器的一些基本使用方法。Vim 具有许多功能和命令，学习曲线较陡，但一旦掌握，它可以成为你的强大工具。可以通过阅读 Vim 的文档或在线教程来更深入地了解它的功能和用法。



# 知识点十一：给文件夹赋予权限

比如给realsense2_camera赋予权限

```
sudo chmod -R 777 ~/realsense2_camera/
```



# 知识点十二：没有interRealSenseD435i SDK2和RealSense-ROS就无法打开摄像机，没有camera的话题，rviz中看不到图像。下载完后还要调整rc_camera.launch文件的参数，不然看不到深度图



# 知识点十三：vins的使用（仿真和实际）

    1.启动rviz
    roslaunch vins vins_rviz.launch
    
    2.启动vins里程计（实际）
    rosrun vins vins_node ~/my_ws/src/VINSFusion/config/vi_car/vi_car.yaml 
    2.启动vins里程计（仿真）
    rosrun vins vins_node ~/my_ws/src/VINS-Fusion-gpu/config/euroc/euroc_stereo_imu_config.yaml
    
    3.视觉循环闭合（可选）
    (optional) rosrun loop_fusion loop_fusion_node ~/catkin_ws/src/VINS-Fusion/config/vi_car/vi_car.yaml 
    
    4.播放 bag 文件
    rosbag play YOUR_DATASET_FOLDER/car.bag



# 知识点十四：控制时间

方法一：cwkj

!(../../Users/86153/AppData/Roaming/Typora/typora-user-images/image-20240330161319033.png)![image-20240330161319190](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/image-20240330161319190.png)

方法二：树康师兄

![image-20240330161614752](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/image-20240330161614752.png)



方法三：官网

![image-20240330163326628](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/image-20240330163326628.png)







# 无人机代码的使用

## 基本通信:启动mavros

舒康师兄的后两个代码是使用了雷达和激光雷达

```
roslaunch mavros px4.launch
```

## 脚本通信：

```
rosrun init_control multi....py
```

## 运行视觉定位节点

```
roslaunch VINS ipac_drone_
```



## 监听视觉定位信息

rostopic echo /mavros/local_position/pose

**初始化视觉定位**

**此步骤相当关键！！！没有此步骤定位飘的概率将大大增****加**缓慢拿起飞机，缓慢左右移动一下（1、2m即可）再缓慢返回原处此过程期间不要让*t265*视野被遮挡或者有移动的物体或者有强光**持续观察定位信息的xyz**几秒钟，如果一直保持（0,0,0）则说明初始化成功

两位小数之后的值不用在意

## **选择节点进行起飞**

```
rosrun my_control_lzh pose_control_sim
```

起飞前需解锁GPS，打开遥控器的紧急开关



## **视觉识别节点**

打开相机并且检测二维码，识别结果到会输出到屏幕上

```
roslaunch example vision.launch
```

![image-20240326204912243](%E7%9F%A5%E8%AF%86%E7%82%B91%EF%BC%9A%E6%9F%A5%E6%89%BEros%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC.assets/image-20240326204912243.png)

## 命令规则：起飞高度 坐标数量 x坐标 y坐标

1.起飞&降落（悬停10秒 高度1.2米）

rosrun my_control_lzh pose_control_sim 1.2 1 \
0 0

2.定位(起飞位置分别设为 (0,0) (1,1) )

rosrun my_control_lzh pose_control_sim 1.2 1 \
0 0

rosrun my_control_lzh pose_control_sim \
1.2 1\
1 1

3.无人机控制测试 挂重物向前飞行1.5米

rosrun my_control_lzh pose_control_sim \
1.2 2 \
0 1.5 \
0 0



# 知识点十五：高飞代码的理解

## 1.ctrl订阅的编写

```c++
#第一种：三个参数
ros::Subscriber state_sub =
    nh.subscribe<mavros_msgs::State>("/mavros/state",
				10,                                    				   boost::bind(&State_Data_t::feed, &fsm.state_data, _1));

#第二种：五个参数
ros::Subscriber odom_sub =
    nh.subscribe<nav_msgs::Odometry>("odom",
                 100,                                         		   boost::bind(&Odom_Data_t::feed, &fsm.odom_data, _1),                           						 ros::VoidConstPtr(),                      			   ros::TransportHints().tcpNoDelay());
```

添加订阅话题eg：/mavros/local_position/pose

1`

```c++
原版：
ros::Subscriber pose_sub = nh.subscribe<geometry_msgs::PoseStamped>
        ( "/iris_0/mavros/local_position/pose", 
        10, 
        get_pose);
改：
ros::Subscriber pose_sub = nh.subscribe<geometry_msgs::PoseStamped>
        ( "/iris_0/mavros/local_position/pose", 
        10, 
        boost::bind(&Pose_Data_t::feed, &fsm.Pose_data, _1));   
```

2`（以下以"/mavros/state"为例）创建构造函数State_Data_t。在input.h中83行

```c++
class State_Data_t
{
public:
  mavros_msgs::State current_state;
  mavros_msgs::State state_before_offboard;

  State_Data_t();
  void feed(mavros_msgs::StateConstPtr pMsg);
};
```

3·在input.cpp中添加回调函数定义

```c++
State_Data_t::State_Data_t()
{
}

void State_Data_t::feed(mavros_msgs::StateConstPtr pMsg)
{
    current_state = *pMsg;
}
```

2.remap的理解：

remap在node之外的作用域是他之后的所有节点，在node中的作用域是当前节点，此外要注意想要remap的话题是这个节点要接收的还是要发布的。
如果是要remap一个该节点发布的source_topic到target_topic,应该是<remap from="/source_topic" to="/target_topic" />
如果是要remap一个该节点想要接收的的target_topic，而实际被另外一个节点发布的话题是source_topic,应该是<remap from="/target_topic" to="/source_topic" />

#### 1、remap要发布的话题

节点中通过ros::Publisher发布了base/joint_states，head/joint_states，torso/joint_states，想要把发布出来的话题重映射到joint_states上，可以这么写：

```xml
<?xml version="1.0"?>
<launch>

    <group ns="dhrobot">
        <remap from="base/joint_states" to="joint_states" />
        <remap from="head/joint_states" to="joint_states" />
        <remap from="torso/joint_states" to="joint_states" /> 
        <node name="robot_driver" pkg="dhrobot_driver" type="robot_driver" />
    </group>

</launch>
```

rostopic list一下可以看到话题：

> /dhrobot//joint_states

#### ２、remap要接收的话题

节点中通过Ros::Subscriber**想要**接收/image话题，但是实际摄像头发布的话题是/kinect2/hd/image_color，所以需要这样处理：

```xml
<?xml version="1.0"?>
<launch>
   <node name="robot_visual" pkg="dhrobot_demo" type="robot_visual" >
	<remap from="/image" to="/kinect2/hd/image_color" />  
  </node>  
</launch>
```

### 自己的理解：（核心）

```
<remap from="目前的话题名" to="我想要的话题名" />
```

#### 这么理解更方便，无论发布和订阅都适用。节点A发布话题/a，节点B订阅话题/b，现在想通过话题/c联系到一起。对于A，本来该发布/a，现在想发布/c，所以

```
<remap from="/a" to="c" />
```

#### 对于B，本来是应该订阅/b，想要改为订阅/c（实际有的）， 

```
<remap from="/b" to="c" />
```

#### A已经有/a，想变成/c，B已经有/b，想变成/c（实际有的）。



#### 在高飞的run_ctrl.launch代码里就是:（核心）

```
<remap from="~cmd" to="/position_cmd" />
```

/position_cmd（**我想要订阅的话题名，即实际话题名**）话题可以rostopic查看到（由ego发出）。而在代码px4ctrl_node.cpp内部自己定义话题为**~cmd（目前的话题名，自己写的**）。故要重映射。



## 2.高飞代码起飞并避障：

```
sh shfiles/rspx4.sh
roslaunch px4ctrl run_ctrl.launch
roslaunch ego_planner single_run_in_exp.launch
```



代码内容：

1.rspx4.sh（未设置rivz可视化界面）

```
sudo chmod 777 /dev/ttyACM0 & sleep 2;
roslaunch realsense2_camera rs_camera.launch & sleep 10;
roslaunch mavros px4.launch & sleep 10;
roslaunch vins ipac_drone_330.launch
wait;
```

ipac_drone_330.launch（用于启动vins）

```
<launch>
  <node name="vins_estimator" pkg="vins" type="vins_node" output="screen" args="$(find vins)/../config/ipac_drone_330.yaml" />

  <node name="loop_fusion" pkg="loop_fusion" type="loop_fusion_node" output="screen" args="$(find vins)/../config/ipac_drone_330.yaml" />

</launch>
```



2.run_ctrl.launch

```
<launch>

	<node pkg="px4ctrl" type="px4ctrl_node" name="px4ctrl" output="screen">
        	<!-- <remap from="~odom" to="/vicon_imu_ekf_odom" /> -->
			
			<remap from="~odom" to="/vins_fusion/imu_propagate" />

		<remap from="~cmd" to="/position_cmd" />

        <rosparam command="load" file="$(find px4ctrl)/config/ctrl_param_fpv.yaml" />
	</node>
 
</launch>
```



- 自动起飞：
  - `sh shfiles/rspx4.sh`
  - `rostopic echo /vins_fusion/imu_propagate`
  - 拿起飞机进行缓慢的小范围晃动，放回原地后确认没有太大误差
  - 遥控器5通道拨到内侧（进入悬停模式），六通道拨到下侧（防止进入阶段3——控制命令模式），油门打到中位
  - `roslaunch px4ctrl run_ctrl.launch`
  - `sh shfiles/takeoff.sh`，如果飞机螺旋桨开始旋转，但无法起飞，说明`hover_percent`参数过小；如果飞机有明显飞过1米高，再下降的样子，说明`hover_percent`参数过大
  - 遥控器此时可以以类似大疆飞机的操作逻辑对无人机进行位置控制
  - 降落时把油门打到最低，等无人机降到地上后，把5通道拨到中间（进入手动模式），左手杆打到左下角上锁
- Ego-Planner实验
  - 自动起飞
  - `roslaunch ego_planner single_run_in_exp.launch`
  - `sh shfiles/record.sh`
  - 进入远程桌面 `roslaunch ego_planner rviz.launch`
  - 按下G键加鼠标左键点选目标点使无人机飞行


$$

$$

