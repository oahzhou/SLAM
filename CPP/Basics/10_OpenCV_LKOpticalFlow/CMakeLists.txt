cmake_minimum_required( VERSION 2.8 )
project( opticalFlowLK )

## configure build
set( CMAKE_BUILD_TYPE Release )
add_compile_options(-std=c++11)
# Optimization flag, (low) O1 -> O3 (high)
set( CMAKE_CXX_FLAGS_RELEASE "-O3" )
# generate compile commands
set( CMAKE_EXPORT_COMPILE_COMMANDS ON )

# OpenCV
find_package( OpenCV REQUIRED )
include_directories( ${OpenCV_DIRS} )

# CPU version
add_executable( opticalFlowLK main.cpp )
target_link_libraries( opticalFlowLK ${OpenCV_LIBS} )
# CUDA version
add_executable( opticalFlowLKCUDA main_cuda.cpp )
target_link_libraries( opticalFlowLKCUDA ${OpenCV_LIBS} )
