cmake_minimum_required(VERSION 3.5)
project(tunable_static_tf_broadcaster)

if (NOT CMAKE_CXX_STANDARD)
    set(CMAKE_CXX_STANDARD 17)
    set(CMAKE_CXX_STANDARD_REQUIRED ON)
    set(CMAKE_CXX_EXTENSIONS OFF)
endif ()

find_package(ament_cmake_auto REQUIRED)
ament_auto_find_build_dependencies()

ament_auto_add_library(tunable_static_tf_broadcaster_node_component SHARED
  src/tunable_static_tf_broadcaster_node.cpp
)

rclcpp_components_register_node(tunable_static_tf_broadcaster_node_component
  PLUGIN "tunable_static_tf_broadcaster::TunableStaticTfBroadcasterNode"
  EXECUTABLE tunable_static_tf_broadcaster_node
)

## Package
ament_auto_package(
  INSTALL_TO_SHARE
    params
    launch
)
