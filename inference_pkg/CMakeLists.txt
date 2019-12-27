cmake_minimum_required(VERSION 2.8.3)
project(inference_pkg)

# Get the information about this package's buildtime dependencies
find_package(catkin REQUIRED
    COMPONENTS message_generation std_msgs sensor_msgs)

add_message_files(FILES
    InferResults.msg
    InferResultsArray.msg
)

# Declare the service files to be built
add_service_files(FILES
    InferenceStateSrv.srv
    LoadModelSrv.srv
    ModelOptimize.srv
)

# Actually generate the language-specific message and service files
generate_messages(DEPENDENCIES std_msgs sensor_msgs)

# Declare that this catkin package's runtime dependencies
catkin_package(
CATKIN_DEPENDS message_runtime std_msgs sensor_msgs
)
