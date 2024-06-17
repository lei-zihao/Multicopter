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