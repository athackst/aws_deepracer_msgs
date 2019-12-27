cmake_minimum_required(VERSION 2.8.3)
project(software_update_pkg)

# Get the information about this package's buildtime dependencies
find_package(catkin REQUIRED
    COMPONENTS message_generation std_msgs)

# Declare the service files to be built
add_service_files(FILES
    BeginSoftwareUpdateSrv.srv
    ConsoleUploadModelSrv.srv
    GetDeviceInfoSrv.srv
    OTGLinkStateSrv.srv
    SoftwareUpdateGetStateSrv.srv
    SoftwareUpdateStatusSrv.srv
    VerifyModelReadySrv.srv
)

# Actually generate the language-specific message and service files
generate_messages(DEPENDENCIES std_msgs)

# Declare that this catkin package's runtime dependencies
catkin_package(
CATKIN_DEPENDS message_runtime std_msgs
)
