cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

add_definitions(-std=c++11)

set(CXX_FLAGS "-Wall")
set(CMAKE_CXX_FLAGS, "${CXX_FLAGS}")

project(playback)

find_package(PCL 1.2 REQUIRED)

include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})
list(REMOVE_ITEM PCL_LIBRARIES "vtkproj4")

add_library(UKF src/ukf.cpp )
add_library(TOOLS src/tools.cpp )
add_library(RENDERS src/render/render.cpp )

add_executable (ukf_highway src/main.cpp)
target_link_libraries (ukf_highway UKF TOOLS RENDERS ${PCL_LIBRARIES}  )




