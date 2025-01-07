mjpg-streamer input plugin: input_ros2
========================================

这个模块启动一个ROS2节点（节点名称为 `/ros2_publish_to_mjpg_streamer_input_converter` ，节点订阅图像消息作为mjpg-streamer的输入。

Usage
=====

首先需要确保环境已完整安装ROS2

通过CMake进行编译，编译方法同其他模块


节点默认订阅 `/image_raw` topic

在节点运行过程中，执行以下命令切换订阅topic实现视频流信号源切换：

`ros2 param set /ros2_publish_to_mjpg_streamer_input_converter topic_name /image_raw`

Authors
-------

Mactarvish https://github.com/Mactarvish
