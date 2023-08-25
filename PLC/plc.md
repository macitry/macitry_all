# PLC相关知识点整理

[toc]

## 1.软件

### 1.Plug & Drive Studio 2

适用于步进电机控制器以及带集成控制器的电机

* 免费
* 调试和编程Nanotec控制器
* 优化电机
* 支持CAN(IXXAT和PEAK)
* 串行接口
* 以太网
* USB接口
* 开发语言:NanoJ V2
  
### 2.TwinCat3

倍福EtherCAT的ADS通讯
Beckhoff ADS(Automation DeviceSpecification)是一个提供程序之间相互通信的接口

* TWinCat3系统中，TWinCat PLC,NC,CNC被设计成虚拟的自动化设备
* 每一个任务均存在一个服务模块，服务端/客户端
* 由MEssage Router统一交换数据
* TwinCATADS Router(ADS Server)
基于TCP/IP协议，监听端口48898用于等待新的客户端
基于UDP协议，使用通讯端口48899用于广播的方式查找路由。

## 2.通信协议

### 1.EtherCAT

* 用于控制自动化技术的以太网，基于以太网
* 开放架构，以以太网为基础的现场总线系统
* 和以太网使用相同的物理和数据链路层

#### 1.机制

* 主站发送数据
* 主站是唯一允许发送帧的节点，子站只能转发帧。
* 数据帧从主站发出，途径各个子站，将数据下发或者收集，最后回到主站确保实时操作，避免延迟
* 每个EtherCat设备通常有两个以太网设备，第一个为接收端，另一个为发送端
* 使用分布式时钟系统，当EtherCAT的数据帧通过每个节点时，节点向其数据添加“已接收消息”时间戳。每个节点在收到消息时添加时间戳，然后在返回主站的路上，当数据帧移回节点时，每个节点再次附加一个时间戳

### 2.Ethernet/IP

* 服务于各类工业自动化应用
* 基于标准的IEEE802.3与TCP/IP Suite
* 应用层采用通用工业协议CIP
* IT集成，包括Web，OPC等服务
* 基于标准的以太网控制器
* 传输端口
    >UDP/IP(Port 44.818)
    >TCP/IP(Port 44.818)

### 3.CAN

#### 1.介绍

* controller Area Network，控制器局域网，应用最为广泛的现场总线之一。
* 是德国Bosch公司为解决的现代汽车中众多控制单元，测试仪器之间的实时数据交换而开发的一种串行通信协议

#### 2.OSI模型

* CAN只定义物理层和数据链路层，没有规定应用层
* 
  
## 3.其他

### 1.ODVA协会

* 一致性测试认证与互测试
* 授权Ethernet/IP技术
* Vendor ID
* SIG - Special Interest Groups

### 2.CIA

CAN in Automation 非盈利组织

### 3.OSI模型

数据链路层:包括介质访问控制(MAC)层和逻辑链路控制(LLC)层，关键是形成数据帧
