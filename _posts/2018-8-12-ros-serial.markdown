---
title:      "Serial Program for ROS"
subtitle:   " \"Hello World to ROS\""
date:       2018-8-12
author:     "LIN JIANING"
header-img: "img/post-serial-ros.jpg"
permalink: /posts/2018/08/Serial Program for ROS/
tags:
    - ROS
---

# ROS_SERIAL //ROS 串口

在搭实验室的SLAM小车的时候，由于底盘是用STM32F427做control的，因此需要和上层的TK1进行通讯。用串口协议进行通讯写起来比较简单，而且刚好有现成的设备，所以就选择了串口。最后实现的功能：TK1发送小车目标速度，STM32F427接收到数据后控制小车达到目标速度。

## Drivers

```bash
1.serial包安装（serial-1.2.1）
make install
2.CH341驱动安装（CH341***）
make load
3.source setup.bash
4.roscore
5.rosrun *** ***
```

## Program

```C
#include <ros/ros.h> 
#include <serial/serial.h>  //ROS已经内置了的串口包 
#include <std_msgs/String.h> 
#include <std_msgs/Empty.h> 
  
serial::Serial ser; //声明串口对象 
  
//回调函数 
void write_callback(const std_msgs::String::ConstPtr& msg) 
{ 
    ROS_INFO_STREAM("Writing to serial port" <<msg->data); 
    ser.write(msg->data);   //发送串口数据 
} 
  
int main (int argc, char** argv) 
{ 
    //初始化节点 
    ros::init(argc, argv, "serial_example_node"); 
    //声明节点句柄 
    ros::NodeHandle nh; 
  
    //订阅主题，并配置回调函数 
    ros::Subscriber write_sub = nh.subscribe("write", 1000, write_callback); 
    //发布主题 
    ros::Publisher read_pub = nh.advertise<std_msgs::String>("read", 1000); 
  
    try 
    { 
    //设置串口属性，并打开串口 
        ser.setPort("/dev/ttyUSB0"); 
        ser.setBaudrate(115200); 
        serial::Timeout to = serial::Timeout::simpleTimeout(1000); 
        ser.setTimeout(to); 
        ser.open(); 
    } 
    catch (serial::IOException& e) 
    { 
        ROS_ERROR_STREAM("Unable to open port "); 
        return -1; 
    } 
  
    //检测串口是否已经打开，并给出提示信息 
    if(ser.isOpen()) 
    { 
        ROS_INFO_STREAM("Serial Port initialized"); 
    } 
    else 
    { 
        return -1; 
    } 
  
    //指定循环的频率 
    ros::Rate loop_rate(50); 
    while(ros::ok()) 
    { 
  
        if(ser.available()){ 
            ROS_INFO_STREAM("Reading from serial port\n"); 
            std_msgs::String result; 
            result.data = ser.read(ser.available()); 
            ROS_INFO_STREAM("Read: " << result.data); 
            read_pub.publish(result); 
        } 

        //处理ROS的信息，比如订阅消息,并调用回调函数 
        ros::spinOnce(); 
        loop_rate.sleep(); 
  
    } 
} 
```