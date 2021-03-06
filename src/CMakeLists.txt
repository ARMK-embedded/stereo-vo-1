#####################################################################################
# Stereo Visual Odometry using registration with Gaussian mixtures					#
# Alankar Kotwal <alankar.kotwal@iitb.ac.in>, Anand Kalvit <anandiitb12@gmail.com>	#
# CMakeLists																		#
#####################################################################################

cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

project(stereo-vo)

find_package(PCL 1.4 REQUIRED)
find_package(OpenCV REQUIRED)

include_directories(${PCL_INCLUDE_DIRS} )
link_directories(${PCL_LIBRARY_DIRS} )
add_definitions(${PCL_DEFINITIONS} )

add_executable (stereo-pointcloud stereo-pointcloud.cpp)
add_executable (pointset-matching pointset-matching.cpp)
add_executable (pointset-matching-cpd pointset-matching-cpd.cpp)
add_executable (pointcloud-stitching pointcloud-stitching.cpp)
add_executable (matrix-transform matrix-transform.cpp)
target_link_libraries (stereo-pointcloud ${PCL_LIBRARIES} ${OpenCV_LIBS})
target_link_libraries (pointset-matching ${PCL_LIBRARIES} ${OpenCV_LIBS})
target_link_libraries (pointset-matching-cpd ${PCL_LIBRARIES} ${OpenCV_LIBS})
target_link_libraries (pointcloud-stitching ${PCL_LIBRARIES} ${OpenCV_LIBS})
target_link_libraries (matrix-transform ${PCL_LIBRARIES})

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
