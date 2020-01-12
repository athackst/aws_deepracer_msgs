cmake_minimum_required(VERSION 3.5)

project(inference_pkg)

if(NOT WIN32)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -Wall -Wextra")
endif()
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()


find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(sensor_msgs REQUIRED)

# declare the message files to generate code for
set(msg_files
   "msg/InferResults.msg"
   "msg/InferResultsArray.msg"
)

# declare the service files to generate code for
set(srv_files
   "srv/InferenceStateSrv.srv"
   "srv/LoadModelSrv.srv"
   "srv/ModelOptimize.srv"
)

 rosidl_generate_interfaces(${PROJECT_NAME}
   ${msg_files}
   ${srv_files}
   DEPENDENCIES builtin_interfaces sensor_msgs
 )

 ament_export_dependencies(rosidl_default_runtime)

ament_package()

install(
  FILES rosbridge_mapping_rules.yaml
  DESTINATION share/${PROJECT_NAME})
