# 运行rplidar节点

## 1.1 **构建** **rplidar ros** 包

功能包下载地址：https://github.com/Slamtec/rplidar_ros/

注意：如果没有将更新环境变量写到【.bahsrc】中，每次执行运行程序前，必须先更新环境变量。(已经写入)

~~~~
source devel/setup.bash
~~~~

在catkin根目录下编译**(新克隆需要重新编)**

````
catkin_make
````



## 1.2 映射USB串口（已完成）

在rplidar_ros功能包路径下，安装 USB 端口重映射：

````
./scripts/create_udev_rules.sh
````

使用以下命令修改重映射：

````
ls -l /dev | grep ttyUSB
````

更改 USB 端口重新映射后，更改有关 serial_port 值的启动文件。

**端口名称更改为“ttyUSB0”**

**记得给ttyUSB0访问权限**

````
sudo chmod 777 /dev/ttyUSB0
````

或者也可以通过以下指令更改.launch的默认读取端口

````
rosed rplidar_ros view_rplidar_s1.launch
rosed rplidar_ros rplidar_s1.launch
````

## 1.3 **运行** **rplidar ros** 包

* 运行rplidar节点，在rviz中查看

````
roslaunch rplidar_ros view_rplidar_s1.launch
````

+ 运行 rplidar 节点

````
roslaunch rplidar_ros rplidar_s1.launch
````

启动测试应用程序

````
rosrun rplidar_ros rplidarNodeClient
````

使用一下指令查看节点是否在运行

`````shell
rostopic list
`````

雷达的节点应该是：/scan

使用以下指令打印节点传出的信息

````
rostopic echo /scan 
````



## Tips:

使用以下指令查看ROS是否在执行：

````
ps -e | grep ROS
````

杀掉进程：

````
kill -9 + 上条指令查询出来的ROS进程编号
````

