cmake_minimum_required(VERSION 2.8.3)
project(camera_driver)

add_compile_options(-std=c++11)
find_package(catkin REQUIRED COMPONENTS roscpp cv_bridge image_transport sensor_msgs roscpp rospy std_msgs)

catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES my_image_transport
#  CATKIN_DEPENDS cv_bridge image_transport opencv2 sensor_msgs
#  DEPENDS system_lib
)


find_package(OpenCV REQUIRED)
include_directories(  ${catkin_INCLUDE_DIRS}  ${OpenCV_INCLUDE_DIRS} )


add_executable(camera_driver_node src/camera_driver.cpp)
add_dependencies(camera_driver_node ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(camera_driver_node ${catkin_LIBRARIES} ${OpenCV_LIBRARIES}
)

add_executable(cameraInfo_node  src/publish_cameraInfo.cpp)
add_dependencies(cameraInfo_node ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(cameraInfo_node ${catkin_LIBRARIES} ${OpenCV_LIBRARIES})



