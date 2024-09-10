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

### vector定义

```
vector<int> a;           //无参数 - 构造一个空的vector,
vector<int> a(10);       //定义了10个整型元素的向量（尖括号中为元素类型名，它可以是任何合法的数据类型），但没有给出初值，其值是不确定的。
vector<int> a(10,1);     //定义了10个整型元素的向量,且给出每个元素的初值为1
vector<int> a(b);        //用b向量来创建a向量，整体复制性赋值， 拷贝构造
vector<int> v3=a ;       //移动构造
vector<int> a(b.begin(),b.begin+3);   //定义了a值为b中第0个到第2个（共3个）元素
int b[7]={1,2,3,4,5,9,8};
vector<int> a(b,b+6);    //从数组中获得初值，b[0]~b[5]
```

### 基本操作

```
    （1）a.assign(b.begin(), b.begin()+3); //b为向量，将b的0~2个元素构成的向量赋给a
    （2）a.assign(4,2);        //是a只含4个元素，且每个元素为2
    （3）a.back();             //返回a的最后一个元素
    （4）a.front();            //返回a的第一个元素
    （5）a[i];                 //返回a的第i个元素，当且仅当a[i]存在2013-12-07
    （6）a.clear();            //清空a中的元素
    （7）a.empty();            //判断a是否为空，空则返回ture,不空则返回false
    （8）a.pop_back();         //删除a向量的最后一个元素
    （9）a.erase(a.begin()+1, a.begin()+3);  //删除a中第1个（从第0个算起）到第2个元素，也就是说删除的元素从a.begin()+1算起（包括它）一直到a.begin()+3（不包括它）
    （10）a.push_back(5);      //在a的最后一个向量后插入一个元素，其值为5
    （11）a.insert(a.begin()+1, 5);         //在a的第1个元素（从第0个算起）的位置插入数值5，如a为1,2,3,4，插入元素后为1,5,2,3,4
    （12）a.insert(a.begin()+1, 3,5);       //在a的第1个元素（从第0个算起）的位置插入3个数，其值都为5
    （13）a.insert(a.begin()+1,b+3, b+6);   //b为数组，在a的第1个元素（从第0个算起）的位置插入b的第3个元素到第5个元素（不包括b+6），如b为1,2,3,4,5,9,8，插入元素后为1,4,5,9,2,3,4,5,9,8
    （14）a.size();            //返回a中元素的个数；
    （15）a.capacity();        //返回a在内存中总共可以容纳的元素个数
    （16）a.resize(10);        //将a的现有元素个数调至10个，多则删，少则补，其值随机
    （17）a.resize(10, 2);      //将a的现有元素个数调至10个，多则删，少则补，其值为2
    （18）a.reserve(100);      //将a的容量（capacity）扩充至100，也就是说现在测试a.capacity();的时候返回值是100.这种操作只有在需要给a添加大量数据的时候才显得有意义，因为这将避免内存多次容量扩充操作（当a的容量不足时电脑会自动扩容，当然这必然降低性能） 
    （19）a.swap(b);           //b为向量，将a中的元素和b中的元素进行整体性交换
    （20）a.begin();           // 返回指向容器第一个元素的迭代器
    （21）a.end();             // 返回指向容器最后一个元素的迭代器
    （22）a==b;                //b为向量，向量的比较操作还有!=,>=,<=,>,<
    (23) reverse(a.begin(),a.end()); //对a中的从a.begin()（包括它）到a.end()（不包括它）的元素倒置，但不排列，如a中元素为1,3,2,4,倒置后为4,2,3,1
   （24）copy(a.begin(),a.end(),b.begin()+1); //把a中的从a.begin()（包括它）到a.end()（不包括它）的元素复制到b中，从b.begin()+1的位置（包括它）开        始复制，覆盖掉原有元素
```





# 知识点四：让无人机进入offboard模式

1.有定位源。查看/mavros/local/position有数据输出

2.发布频率大于2HZ

3./cmd_pose_enu话题和/mavros/ setpoint_position/local话题控制位置区别:用第一个不能进入offfboard模式，用第二个可以进入。

![image-20240622201253099](C++学习记录.assets/image-20240622201253099.png)





# 知识点五：类模版，命名空间

## 在这段代码中，`square<double> test(x);` 是在 C++ 中创建一个类模板 `square` 的实例对象 `test`。以下是详细解释：

### 1. **类模板 `square` 的定义**
```cpp
template <typename T>
class square {
public:
    T a;
    square(T _a) {
        a = _a * _a;
    }
};
```
- 这里定义了一个类模板 `square`，其中 `T` 是一个模板参数，表示类型参数。`T` 可以是任何数据类型，如 `int`、`float`、`double` 等。
- 类中有一个公共成员变量 `a`，类型为 `T`。
- 构造函数 `square(T _a)` 接受一个类型为 `T` 的参数 `_a`，并将 `_a * _a` 的结果赋值给成员变量 `a`。

### 2. **创建类模板的实例**
```cpp
square<double> test(x);
```
- `square<double>`：这里的 `square<double>` 表示将模板参数 `T` 指定为 `double` 类型，生成一个具体类型的类 `square<double>`。
- `test(x)`：`test` 是一个 `square<double>` 类型的对象，`x` 作为参数传递给 `square<double>` 的构造函数。

### 3. **工作原理**
当你执行 `square<double> test(x);` 时，以下操作会发生：
- 变量 `x` 被传递给 `square<double>` 类的构造函数。
- 在构造函数中，`_a * _a` 被计算出来，结果赋值给 `a`。
- 由于 `x` 是 `5.5`，`_a * _a` 的结果是 `5.5 * 5.5 = 30.25`。
- 因此，`test.a` 的值为 `30.25`。

### 4. **程序输出**
```cpp
std::cout << "the square of " << x << " is " << test.a << std::endl;
```
- 最后，程序输出 `the square of 5.5 is 30.25`，这表明 `test.a` 保存了 `x` 的平方值。

综上所述，`square<double> test(x);` 创建了一个 `square` 类的 `double` 类型实例，计算并存储了 `x` 的平方值。