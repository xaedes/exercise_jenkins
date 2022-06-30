cmake_minimum_required(VERSION 2.8.12)
project(example_ros_pkg)

find_package(
    catkin 
    REQUIRED 
    COMPONENTS
    roscpp
    std_msgs
    sensor_msgs
    geometry_msgs
    nodelet
)
catkin_package(
    LIBRARIES 
    ${LIBRARY_NAME}
    CATKIN_DEPENDS 
    roscpp 
    std_msgs 
    sensor_msgs 
    geometry_msgs 
    nodelet
)

add_library(${PROJECT_NAME} STATIC src/lib.cpp)
target_include_directories(${PROJECT_NAME} PUBLIC include/)
target_link_libraries(${PROJECT_NAME} catkin)

# install library 
install(
    TARGETS 
    ${PROJECT_NAME}
    ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
    LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
    RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

# install header files
install(
    DIRECTORY 
    include/${PROJECT_NAME}/
    DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
    FILES_MATCHING PATTERN "*.h"
)
