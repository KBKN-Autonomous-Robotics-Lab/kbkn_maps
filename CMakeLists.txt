cmake_minimum_required(VERSION 3.8)
project(kbkn_maps)

if($ENV{ROS_VERSION} EQUAL "1")
  find_package(catkin REQUIRED)
  catkin_package()
elseif($ENV{ROS_VERSION} EQUAL "2")
  find_package(ament_cmake REQUIRED)

  install(DIRECTORY
    maps
    waypoints
    multi_map
    DESTINATION share/${PROJECT_NAME})

  ament_package()
endif()
