cmake_minimum_required(VERSION 3.5)

project(ctrl_pkg)

if(NOT WIN32)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -Wall -Wextra")
endif()

find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)

# declare the message files to generate code for
set(msg_files
   "msg/ServoCtrlMsg.msg"
)

# declare the service files to generate code for
set(srv_files
   "srv/ActiveStateSrv.srv"
   "srv/EnableStateSrv.srv"
   "srv/ModelStateSrv.srv"
   "srv/NavThrottleSrv.srv"
)

rosidl_generate_interfaces(${PROJECT_NAME}
    ${msg_files}
    ${srv_files}
    DEPENDENCIES builtin_interfaces
)

ament_export_dependencies(rosidl_default_runtime)

ament_package()

install(
  FILES rosbridge_mapping_rules.yaml
  DESTINATION share/${PROJECT_NAME})
