大家好，我是小鱼，好久没写文章了，最近工作比较忙(同时兼顾底盘和机械臂开发)，每次到家就想睡觉觉，就偷懒没有写文章，结果一早被小仙女截图警告了，这周不敢偷懒了。

今天早上和公司导航开发的负责人Z聊了下关于目前的导航通信架构，Z说目前自研的导航架构不能说是一个系统，因为没有通信中间件做支撑，前段时间小鱼做ROS2，也接触了ROS2的DDS中间件，来分析一下。

## 1.DDS是什么？
DDS，全称 Data Distribution Service (数据分发服务)。是由对象管理组 (OMG) 于 2003 年发布并于 2007 年修订的开分布式系统放标准。

通过类似于ROS中的话题发布和订阅形式来进行通信，同时提供了丰富的服务质量管理来保证可靠性、持久性、传输设置等。


## 2.DDS通信模型

DDS的模型是非常容易理解，我们可以定义话题的数据结构（类似于ROS2中的接口类型）。
下图中的例子:
- Pos：一个编号id的车子的位置x,y

DDS的参与者(Participant)通过发布和订阅主题数据进行通信。
![DDS模型](https://img-blog.csdnimg.cn/927c8314623141dea98329f64123cb94.png)
DDS的应用层通过DDS进行数据订阅发布，DDS通过传输层进行数据的收发。
![DDS结构](https://img-blog.csdnimg.cn/bcd7fa5984b14335ae8cc395db90d152.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA6bG86aaZUk9T,size_12,color_FFFFFF,t_70,g_se,x_16)

DDS优势
- 发布/订阅模型：简单解耦，可以轻松实现系统解耦
- 性能：在发布/订阅模式中，与请求/回复模式相比，延迟更低，吞吐量更高。
- 远程参与者的自动发现：此机制是 DDS 的主要功能之一。通信是匿名的、解耦的，开发者不必担心远程参与者的本地化。
- 丰富的 Qos 参数集，允许调整通信的各个方面：可靠性、持久性、冗余、寿命、传输设置、资源......
- 实时发布订阅协议 ( RTPS )：该协议几乎可以通过任何传输实现，允许在 UDP、TCP、共享内存和用户传输中使用 DDS，并实现不同 DDS 实现之间的真正互操作性。


## 3.FastDDS
eProsima Fast DDS是DDS（数据分发服务）规范的 C++ 实现。特点是开源。

明天小鱼带你一起安装和体验下DDS


参考资料：
- 白皮书:https://www.eprosima.com/index.php/resources-all/whitepapers/dds
- DDS-Docker:https://www.eprosima.com/index.php/component/ars/repository/eprosima-dds-suite/eprosima-dds-suite-1-0-0/ubuntu-eprosima-dds-suite-v1-0-0-tar




