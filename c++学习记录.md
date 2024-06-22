# 知识点一：构造函数

## 带参数的构造函数（官方示例在一个文件中）

默认的构造函数没有任何参数，但如果需要，构造函数也可以带有参数。这样在创建对象时就会给对象赋初始值，如下面的例子所示：

```c++
#include <iostream>
 
using namespace std;
 
class Line
{
   public:
      void setLength( double len );
      double getLength( void );
      Line(double len);  // 这是构造函数
 
   private:
      double length;
};
 
// 成员函数定义，包括构造函数
Line::Line( double len)
{
    cout << "Object is being created, length = " << len << endl;
    length = len;
}
 
void Line::setLength( double len )
{
    length = len;
}
 
double Line::getLength( void )
{
    return length;
}
// 程序的主函数
int main( )
{
   Line line(10.0);
 
   // 获取默认设置的长度
   cout << "Length of line : " << line.getLength() <<endl;
   // 再次设置长度
   line.setLength(6.0); 
   cout << "Length of line : " << line.getLength() <<endl;
 
   return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```c++
Object is being created, length = 10
Length of line : 10
Length of line : 6
```

### 使用初始化列表来初始化字段（官方）

使用初始化列表来初始化字段：

```c++
Line::Line( double len): length(len)
{
    cout << "Object is being created, length = " << len << endl;
}
```

上面的语法等同于如下语法：

```c++
Line::Line( double len)
{
    length = len;
    cout << "Object is being created, length = " << len << endl;
}
```

假设有一个类 C，具有多个字段 X、Y、Z 等需要进行初始化，同理地，您可以使用上面的语法，只需要在不同的字段使用逗号进行分隔，如下所示：

```c++
C::C( double a, double b, double c): X(a), Y(b), Z(c)
{
  ....
}
```

#### 以高飞代码初始化构造函数的方法为例

```
PX4CtrlFSM::PX4CtrlFSM(Parameter_t &param_, LinearControl &controller_) : param(param_), controller(controller_)
{
	state = MANUAL_CTRL;
	hover_pose.setZero();
}
```



## 自我总结构造函数的写法

在.h文件里定义类class声明类中的函数（但不定义）

在.cpp文件中定义成员函数（可以有回调函数，判断函数），包括构造函数（用于在创建实例时初始化类）

![image-20240418115553034](C++%E5%AD%A6%E4%B9%A0%E8%AE%B0%E5%BD%95/image-20240418115553034.png)





# 知识点二：param参数服务器

rosparam load(先准备 yaml 文件)  从外部文件加载参数

rosparam  command

```xml
<param name="robot_description" command="$(find xacro)/xacro $(find demo01_urdf_helloworld)/urdf/xacro/my_base.urdf.xacro" />
```

- `name="robot_description"`：这是参数的名称。在这个例子中，参数名是 `robot_description`，通常用于存储机器人的URDF（Unified Robot Description Format）描述。

- `command="$(find xacro)/xacro $(find demo01_urdf_helloworld)/urdf/xacro/my_base.urdf.xacro"`：这是一个指令，告诉ROS如何生成这个参数的值。具体来说，这里的指令是调用 `xacro`（XML宏）工具来处理一个Xacro文件，并生成URDF描述。

详细解释 `command` 的内容：

1. `$(find xacro)/xacro`：
   - `$(find xacro)`：这是ROS的一个查找命令，用来找到 `xacro` 包的路径。
   - `/xacro`：这是 `xacro` 包中的 `xacro` 可执行文件。结合前面的查找命令，这部分指定了要运行的程序。

2. `$(find demo01_urdf_helloworld)/urdf/xacro/my_base.urdf.xacro`：
   - `$(find demo01_urdf_helloworld)`：这是另一个ROS的查找命令，用来找到 `demo01_urdf_helloworld` 包的路径。
   - `/urdf/xacro/my_base.urdf.xacro`：这是在 `demo01_urdf_helloworld` 包中指定的Xacro文件的路径。结合前面的查找命令，这部分指定了要处理的文件。

综合起来，这个指令的意思是：

1. 找到 `xacro` 包，并运行其中的 `xacro` 可执行文件。
2. 找到 `demo01_urdf_helloworld` 包，并处理其中的 `urdf/xacro/my_base.urdf.xacro` 文件。
3. `xacro` 工具会将这个Xacro文件转换成URDF文件，并将结果作为 `robot_description` 参数的值。

### 使用这个 `<param>` 标签的典型场景

通常，这个参数会在启动文件（launch file）中使用，以便在启动时加载机器人的URDF描述。例如：

```xml
<launch>
  <!-- Define the robot description parameter -->
  <param name="robot_description" command="$(find xacro)/xacro $(find demo01_urdf_helloworld)/urdf/xacro/my_base.urdf.xacro" />

  <!-- Launch other nodes that need the robot description -->
  <node name="robot_state_publisher" pkg="robot_state_publisher" type="robot_state_publisher" />
</launch>
```

在这个启动文件中，首先定义了 `robot_description` 参数，接着启动 `robot_state_publisher` 节点，这个节点会使用 `robot_description` 参数来获取机器人的URDF描述。

希望这能帮助你理解这个 `<param>` 标签的作用和用法。如果有更多问题或需要进一步解释，请随时问我！



#### 参数服务器获取参数

```
/*
    参数服务器操作之查询_C++实现:
    在 roscpp 中提供了两套 API 实现参数操作
    ros::NodeHandle

        param(键,默认值) 
            存在，返回对应结果，否则返回默认值

        getParam(键,存储结果的变量)
            存在,返回 true,且将值赋值给参数2
            若果键不存在，那么返回值为 false，且不为参数2赋值

        getParamCached键,存储结果的变量)--提高变量获取效率
            存在,返回 true,且将值赋值给参数2
            若果键不存在，那么返回值为 false，且不为参数2赋值

        getParamNames(std::vector<std::string>)
            获取所有的键,并存储在参数 vector 中 

        hasParam(键)
            是否包含某个键，存在返回 true，否则返回 false

        searchParam(参数1，参数2)
            搜索键，参数1是被搜索的键，参数2存储搜索结果的变量

    ros::param ----- 与 NodeHandle 类似





*/

#include "ros/ros.h"

int main(int argc, char *argv[])
{
    setlocale(LC_ALL,"");
    ros::init(argc,argv,"get_param");

    //NodeHandle--------------------------------------------------------
    /*
    ros::NodeHandle nh;
    // param 函数
    int res1 = nh.param("nh_int",100); // 键存在
    int res2 = nh.param("nh_int2",100); // 键不存在
    ROS_INFO("param获取结果:%d,%d",res1,res2);

    // getParam 函数
    int nh_int_value;
    double nh_double_value;
    bool nh_bool_value;
    std::string nh_string_value;
    std::vector<std::string> stus;
    std::map<std::string, std::string> friends;

    nh.getParam("nh_int",nh_int_value);
    nh.getParam("nh_double",nh_double_value);
    nh.getParam("nh_bool",nh_bool_value);
    nh.getParam("nh_string",nh_string_value);
    nh.getParam("nh_vector",stus);
    nh.getParam("nh_map",friends);

    ROS_INFO("getParam获取的结果:%d,%.2f,%s,%d",
            nh_int_value,
            nh_double_value,
            nh_string_value.c_str(),
            nh_bool_value
            );
    for (auto &&stu : stus)
    {
        ROS_INFO("stus 元素:%s",stu.c_str());        
    }

    for (auto &&f : friends)
    {
        ROS_INFO("map 元素:%s = %s",f.first.c_str(), f.second.c_str());
    }

    // getParamCached()
    nh.getParamCached("nh_int",nh_int_value);
    ROS_INFO("通过缓存获取数据:%d",nh_int_value);

    //getParamNames()
    std::vector<std::string> param_names1;
    nh.getParamNames(param_names1);
    for (auto &&name : param_names1)
    {
        ROS_INFO("名称解析name = %s",name.c_str());        
    }
    ROS_INFO("----------------------------");

    ROS_INFO("存在 nh_int 吗? %d",nh.hasParam("nh_int"));
    ROS_INFO("存在 nh_intttt 吗? %d",nh.hasParam("nh_intttt"));

    std::string key;
    nh.searchParam("nh_int",key);
    ROS_INFO("搜索键:%s",key.c_str());
    */
    //param--------------------------------------------------------
    ROS_INFO("++++++++++++++++++++++++++++++++++++++++");
    int res3 = ros::param::param("param_int",20); //存在
    int res4 = ros::param::param("param_int2",20); // 不存在返回默认
    ROS_INFO("param获取结果:%d,%d",res3,res4);

    // getParam 函数
    int param_int_value;
    double param_double_value;
    bool param_bool_value;
    std::string param_string_value;
    std::vector<std::string> param_stus;
    std::map<std::string, std::string> param_friends;

    ros::param::get("param_int",param_int_value);
    ros::param::get("param_double",param_double_value);
    ros::param::get("param_bool",param_bool_value);
    ros::param::get("param_string",param_string_value);
    ros::param::get("param_vector",param_stus);
    ros::param::get("param_map",param_friends);

    ROS_INFO("getParam获取的结果:%d,%.2f,%s,%d",
            param_int_value,
            param_double_value,
            param_string_value.c_str(),
            param_bool_value
            );
    for (auto &&stu : param_stus)
    {
        ROS_INFO("stus 元素:%s",stu.c_str());        
    }

    for (auto &&f : param_friends)
    {
        ROS_INFO("map 元素:%s = %s",f.first.c_str(), f.second.c_str());
    }

    // getParamCached()
    ros::param::getCached("param_int",param_int_value);
    ROS_INFO("通过缓存获取数据:%d",param_int_value);

    //getParamNames()
    std::vector<std::string> param_names2;
    ros::param::getParamNames(param_names2);
    for (auto &&name : param_names2)
    {
        ROS_INFO("名称解析name = %s",name.c_str());        
    }
    ROS_INFO("----------------------------");

    ROS_INFO("存在 param_int 吗? %d",ros::param::has("param_int"));
    ROS_INFO("存在 param_intttt 吗? %d",ros::param::has("param_intttt"));

    std::string key;
    ros::param::search("param_int",key);
    ROS_INFO("搜索键:%s",key.c_str());

    return 0;
}
```



# 知识点三：vector使用

## 好处：向量（`vector`）是一个动态数组，可以根据需要增加其大小。

```
geometry_msgs::Pose wp;
std::vector<geometry_msgs::Pose> waypoints;

// 定义第一个图片靶的位置
wp.position.x = 0; //假设图片1位置
wp.position.y = 0;
wp.position.z = 1;
waypoints.push_back(wp);

// 清空wp变量，重新使用
wp = geometry_msgs::Pose();
wp.position.x = 1; //假设图片2位置
wp.position.y = 0;
wp.position.z = 1;
waypoints.push_back(wp);

// 定义其他图片靶的位置
wp = geometry_msgs::Pose(); 
wp.position.x = 2; //假设图片3位置
wp.position.y = 0;
wp.position.z = 1;
waypoints.push_back(wp);

wp = geometry_msgs::Pose(); 
wp.position.x = 3; //假设图片4位置
wp.position.y = 0;
wp.position.z = 1;
waypoints.push_back(wp);
```

`push_back()` 是 C++ STL（Standard Template Library，标准模板库）中 `std::vector` 类的成员函数，用于向向量（`vector`）的末尾添加一个元素。

### 用法：
```cpp
vector_name.push_back(value);
```

### 参数：
- `vector_name` 是要添加元素的向量的名称。
- `value` 是要添加到向量中的元素的值。

### 功能：
- 将指定的元素添加到向量的末尾，扩展向量的大小，并将新元素放置在新的末尾位置。

### 示例：
```cpp
std::vector<int> my_vector;
my_vector.push_back(10); // 向 my_vector 向量的末尾添加值为 10 的元素
```

### 注意事项：
- `push_back()` 操作会动态增长向量（vector）的大小，因此在添加大量元素时要考虑内存使用。
- 向量（`vector`）是一个动态数组，可以根据需要增加其大小。

### 更多信息：
- `push_back()` 只能在向量末尾添加元素，不能在中间或头部插入。
- 当插入元素时，向量会自动调整大小以容纳新元素。
- 您可以将任何类型的元素添加到向量中，包括自定义类型和结构。

希望这些信息能帮助您更好地理解`push_back()` 函数的用法和语法。



