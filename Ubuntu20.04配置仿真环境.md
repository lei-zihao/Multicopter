# Ubuntu20.04安装ROS 无人机 无人车 无人船仿真环境

https://dvu20vje1ss.feishu.cn/docx/SyxKd3xyPoACPzxORHpcoqdGnbd?referer=wx_mp_login_callback&wxmp_open_id=oIikk7VkA6MulFp9npSbKl4TTBBY&wxmp_open_id=oIikk7VkA6MulFp9npSbKl4TTBBY#share-V880dtWEsoqDz4xY1XUcWRXNnPe

ubuntu20.04自带python3(3.8)，建立python语句到python3的链接：

```
sudo ln -s /usr/bin/python3 /usr/bin/python
```

1. ## 先通过链接一键安装ROS-Noetic-desktop-full：[小鱼的一键安装系列](https://fishros.org.cn/forum/topic/20/小鱼的一键安装系列)

1. ## 再按照此过程安装无人机仿真环境：[仿真平台基础配置（对应PX4 1.13版） · 语雀](https://www.yuque.com/xtdrone/manual_cn/basic_config_13)

其中，安装Gazebo的过程参考这里：[Gazebo学习(一)Ubuntu20.04安装ROS+gazebo11+模型库导入(汇总跳转连接+个人安装记录)_gazebo模型库-CSDN博客](https://blog.csdn.net/Jenniehubby/article/details/134780066)，但不用执行这一步

![img](Ubuntu20.04配置仿真环境.assets/-173744973673730.assets)

这一步较慢，需要多尝试几次：

![img](Ubuntu20.04配置仿真环境.assets/-17374497366601.assets)

执行下面编译语句时会报错：

![img](Ubuntu20.04配置仿真环境.assets/-17374497366612.assets)

![img](Ubuntu20.04配置仿真环境.assets/-17374497366623.assets)

可以在这里找到解决办法：[下载PX4固件时网络太慢，经常出现克隆失败_px4克隆失败-CSDN博客](https://blog.csdn.net/qq_43212651/article/details/116193397)

![img](Ubuntu20.04配置仿真环境.assets/-17374497366624.assets)

以及其他错误：

![img](Ubuntu20.04配置仿真环境.assets/-17374497366635.assets)

可以用这个解决：

![img](Ubuntu20.04配置仿真环境.assets/-17374497366636.assets)

遇到这个错误：CMake Error: The following variables are used in this project, but they are set to NOTFOUND.

![img](Ubuntu20.04配置仿真环境.assets/-17374497366647.assets)

安装这个包：[PX4编译时容易出现的两个问题](https://blog.csdn.net/night___raid/article/details/106521521)

![img](Ubuntu20.04配置仿真环境.assets/-17374497366648.assets)

如果编译完之后，在mavros测试阶段遇到这个连接错误的问题，可以先跳过，后面修改完px4的组件再次编译就可以恢复正常连接了

![img](Ubuntu20.04配置仿真环境.assets/-17374497366649.assets)

最后编译成功

修改后，再次编译时遇到问题：[ROS-neotic:XTDrone配置的总结_xtdrone arming failed-CSDN博客](https://blog.csdn.net/qq_41536556/article/details/132543393)

![img](Ubuntu20.04配置仿真环境.assets/-173744973666510.assets)

启动launch时遇到问题：[XTDrone--执行roslaunch px4 indoor1.launch 遇到的问题_rlexception: [indoor1.launch\] is neither a launch -CSD](https://blog.csdn.net/z1872385/article/details/122664860)

![img](Ubuntu20.04配置仿真环境.assets/-173744973666511.assets)

1. #### 安装基于vrx的无人船与无人机协同环境

在catkin_ws编译时遇到错误：

![img](Ubuntu20.04配置仿真环境.assets/-173744973666512.assets)

通过给python建立符号链接解决：[解决:/usr/bin/env: ‘python’: No such file or directory_myenvs中找不到python-CSDN博客](https://blog.csdn.net/qq_41550190/article/details/119804102)

遇到找不到Launch文件的问题，参考这里：https://blog.csdn.net/weixin_47776213/article/details/139736604

![img](Ubuntu20.04配置仿真环境.assets/-173744973666613.assets)

添加无人机与第二艘无人船：

无人船

![img](Ubuntu20.04配置仿真环境.assets/-173744973666614.assets)

![img](Ubuntu20.04配置仿真环境.assets/-173744973666615.assets)

无人机

![img](Ubuntu20.04配置仿真环境.assets/-173744973666616.assets)

![img](Ubuntu20.04配置仿真环境.assets/-173744973666617.assets)

如何更换船体？如何控制无人机起飞？控制的代码接口在哪里？

1. #### 安装无人车环境

[配置与控制无人车 · 语雀](https://www.yuque.com/xtdrone/manual_cn/ugv_config) 按照这个链接，将XTDrone/sitl_config/ugv中已经事先下载好的的代码复制到ros编译空间中并编译，遇到报错：

![img](Ubuntu20.04配置仿真环境.assets/-173744973666718.assets)

![img](Ubuntu20.04配置仿真环境.assets/-173744973666719.assets)

这个问题通常是因为CMake在尝试使用`target_link_libraries`命令链接一个不存在的目标`protobuf::libprotobuf`。但经过查看，已经安装了protobuf，不知道错误原因，再次编译通过

编译又遇到错误

![img](Ubuntu20.04配置仿真环境.assets/-173744973666720.assets)

出现“C++: fatal error: Killed signal terminated program cc1plus”错误通常是由于系统资源不足，特别是内存不足导致的。不知道原因，再次编译时通过

1. #### 启动仿真环境ros launch sandisland.launch时报错，无人船无人机等模型下落

1. 这是因为**残留的 Gazebo 进程。**如果之前运行的 Gazebo 进程没有正确关闭，可能会导致新的实例无法启动。**解决方法**：运行以下命令强制关闭所有 Gazebo 相关进程：

```Bash
killall gzserver
killall gzclient
```

1. # Ubuntu20.04 yolo5安装、训练及测试

### a. 安装

yolo5 ros launch版本：

暂时无法在飞书文档外展示此内容

1. pip install -r requirements.txt，安装yolo要求的所有python功能包 
2. catkin_make编译
3. source devel/setup.bash使文件生效
4. roslaunch yolov5_ros yolov5.launch启动yolo识别程序
5. 在~/yolo_ws/src/yolov5_ros/launch/yolov5.launch中可以改变yolo5使用的权重、device和输入图像话题

![img](Ubuntu20.04配置仿真环境.assets/-173744973666721.assets)

### b. 训练

1. ##### 通过这个连接下载图片标注软件并标注

[超详细!手把手教你从零开始训练yolov5模型_yolov5模型训练-CSDN博客](https://blog.csdn.net/limingmin2020/article/details/129801242?utm_source=miniapp_weixin)

暂时无法在飞书文档外展示此内容

打开软件后，选择打开文件对图片进行处理，否则不知道为什么会报一些路径的错误：

TypeError: expected str, bytes or os.PathLike object, not NoneType

![img](Ubuntu20.04配置仿真环境.assets/-173744973666722.assets)

在~/yolo_ws/src/yolov5_ros/src/yolov5目录下新建一个文件夹存放自己的数据集，包括图片和标签

![img](Ubuntu20.04配置仿真环境.assets/-173744973666823.assets)

1. ##### 开始训练

暂时无法在飞书文档外展示此内容

暂时无法在飞书文档外展示此内容

在~/yolo_ws/src/yolov5_ros/src/yolov5目录下，执行：

python3 train.py --img 640 --batch 1 --epochs 200 --data usv_img/usv.yaml --cfg ./models/yolov5s.yaml --weights best.pt --device cpu

--batch 1 表示一次让CPU处理多少张图片，决定了显存占用大小，默认是16，过大会导致训练进程被killed，经过测试在本电脑上选1或者2才能正常运行

![img](Ubuntu20.04配置仿真环境.assets/-173744973666824.assets)

--data usv.yaml指明了训练集和验证集的路径，以及分类的类别数、检测的目标名称

![img](Ubuntu20.04配置仿真环境.assets/-173744973666925.assets)

 --cfg ./models/yolov5s.yaml指明了网络的结构，要修改类别数

![img](Ubuntu20.04配置仿真环境.assets/-173744973666926.assets)

 --weights best.pt 确定了网络的权重参数，但是不同系统中训练的权重一般不能直接在别的系统中使用，因在训练中会保存路径信息。

 训练结束后在runs/train/exp*下面查看训练的结果，并且可以获取.pt权重文件

![img](Ubuntu20.04配置仿真环境.assets/-173744973667027.assets)

1. ##### 常见报错

--batch 1 表示一次让CPU处理多少张图片，决定了显存占用大小，默认是16，过大会导致训练进程被killed，经过测试在本电脑上选1或者2才能正常运行

![img](Ubuntu20.04配置仿真环境.assets/-173744973667028.assets)

--weights best.pt 确定了网络的权重参数，但是不同系统中训练的权重一般不能直接在别的系统中使用，因在训练中会保存路径信息，如果直接使用会路径报错

在训练yolo5时，可能会报错：attributeerror: 'FreeTypeFont' object has no attribute 'getsize'，这是因为安装了新版本的Pillow删除了该`getsize `功能，降级到 Pillow 9.5 解决了该问题可以尝试以下方法进行解决：

```COBOL
pip install Pillow==9.5
```

### c. 测试

在~/yolo_ws/src/yolov5_ros/src/yolov5目录下，执行：

python3 detect.py --weights best.pt --source usv_img/train/images/ --conf 0.25

--weights best.pt 指定使用的权重文件路径

--source usv_img/train/images/ 表示需要检测的图片的路径，0代表摄像头输入

--conf 0.25 代表最小置信度

如果图片检测过程显示no detection，要不就是选择错了权重文件，要不就是训练的epochs还不够，需要继续训练，检测的结果会保存在runs/detect/exp*中

![img](Ubuntu20.04配置仿真环境.assets/-173744973667129.assets)