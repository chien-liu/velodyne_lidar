# LiDar操作手冊
tags `manual`
原文http://wiki.ros.org/velodyne/Tutorials/Getting%20Started%20with%20the%20Velodyne%20VLP16?fbclid=IwAR3hBGPD3qT8OwBaVadg2o3axV4LbCaIUmdITumixt24L3zRRpjUGHFCXSQ

![](https://i.imgur.com/w4HV44g.png)



## 測試LiDAR網路線連線

**一、硬體設置**

    1. 插上LiDAR 電源線
    2. 把LiDAR 網路線插到筆電上

**二、電腦IP配置**

    1. 新增ethernet connection (見下圖）
        - IPV4
        - IP adress 192.168.1.100
        - Metmask 255.255.255.0
        - Gateway 0.0.0.0
![](https://i.imgur.com/dmYMGpI.png)


**三、打開瀏覽器**

    1. 打開瀏覽器連結192.168.1.201
    2. **看到畫面代表連線成功，若無法連線請拔掉LiDAR的網路線重插**
![](https://i.imgur.com/n5eAEQm.png)



## 安裝ROS套件

**一、ROS dependencies**

     `$ sudo apt-get install ros-VERSION-velodyne`
    (VERSION = ROS distribution

 
**二、VLP16 driver**
make sure "~/catkin_ws/src/" exists.

    $ cd ~/catkin_ws/src/ && git clone https://github.com/ros-drivers/velodyne.git
    $ cd ~/catkin_ws/ && rosdep install --from-paths src --ignore-src --rosdistro YOURDISTRO -y
    $ cd ~/catkin_ws/ && catkin_make


## 查看LiDAR傳輸資料

**一、開啟必要程式**
`$ roslaunch velodyne_pointcloud VLP16_points.launch`
**二、check messenge of the topic**
`$ rostopic echo /velodyne_points`
**三、使用圖像化界面看數據**
`$ rosrun rviz rviz -f velodyne`
界面剛開啟時不會顯示座標點。開啟界面後，在界面中執行以下步驟：

1. In the "displays" panel, click "Add", then select "Point Cloud2", then press "OK".
2. In the "Topic" field of the new "Point Cloud2" tab, enter "/velodyne_points".
3. Congratulations. Now, your Velodyne is ready to build the "real" world inside your system. Enjoy it.
![](https://i.imgur.com/Uek8VtA.png)

## Developement Information
    $ rostopic info /velodyne_points
    
    Type: sensor_msgs/PointCloud2
    
    Publishers: 
     * /velodyne_nodelet_manager 
    
    Subscribers: None

Tutorial:
http://wiki.ros.org/pcl/Tutorials#pcl.2BAC8-Tutorials.2BAC8-hydro.Download_the_source_code_from_the_PCL_tutorial
http://www.pointclouds.org/documentation/

# 撰寫自己的PCL節點
## Download PCL official package (for Ubuntu)
    sudo add-apt-repository ppa:v-launchpad-jochen-sprickerhof-de/pcl
    sudo apt-get update
    sudo apt-get install libpcl-all


