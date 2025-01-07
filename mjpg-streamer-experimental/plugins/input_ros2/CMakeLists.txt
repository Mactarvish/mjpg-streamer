
# TODO: which components do I need?
# To fix the error: "undefined symbol: _ZN2cv12VideoCaptureC1Ev"
find_package(OpenCV COMPONENTS core imgproc highgui videoio)

MJPG_STREAMER_PLUGIN_OPTION(input_ros2 "ROS2 input plugin"
                            ONLYIF OpenCV_FOUND ${OpenCV_VERSION_MAJOR} EQUAL 4)
set(PLUGIN_INPUT_ROS2 TRUE)
if (PLUGIN_INPUT_ROS2)
    enable_language(CXX)
    include_directories(${OpenCV_INCLUDE_DIRS})

    MJPG_STREAMER_PLUGIN_COMPILE(input_ros2 input_ros2.cpp)
    
    target_link_libraries(input_ros2 ${OpenCV_LIBS})
endif()


cmake_minimum_required(VERSION 3.8)
#project(visual_perception)

#if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
#    add_compile_options(-Wall -Wextra -Wpedantic)
#endif()

# find dependencies
find_package(ament_cmake REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

find_package(rclcpp REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(cv_bridge REQUIRED)
find_package(OpenCV REQUIRED)
#find_package(usb_cam REQUIRED)

# Add other find_package as needed

#include_directories(include ${OpenCV_INCLUDE_DIRS})

ament_target_dependencies(input_ros2 rclcpp sensor_msgs cv_bridge OpenCV)
#ament_package()
