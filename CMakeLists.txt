cmake_minimum_required(VERSION 3.8)
project(bittle_msgs)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(sensor_msgs REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/Detection.msg"
  "msg/Command.msg"
  "msg/CommandList.msg"
  "msg/State.msg"
  "msg/SerialResponse.msg"
  "msg/AprilTag.msg"
  "msg/Yolo.msg"
  "srv/SerialCommand.srv"
  "srv/CapturePhoto.srv"
  "srv/ExecuteCommand.srv"
  "action/MoveToGrid.action"
  DEPENDENCIES sensor_msgs
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()

