cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project(custom_ops)
set(Torch_DIR /Users/peng/libtorch/share/cmake/Torch)
set(OpenCV_DIR /usr/local/lib/cmake/opencv4/)

include_directories( ${OpenCV_INCLUDE_DIRS} )
include_directories(/Users/peng/libtorch/include/ATen)
include_directories(/opt/anaconda3/pkgs/pytorch-1.7.1-py3.7_0/lib/python3.7/site-packages/torch/include/torch)

find_package(Torch REQUIRED)
find_package( OpenCV REQUIRED )

message(STATUS "Pytorch status:")
message(STATUS "    libraries: ${TORCH_LIBRARIES}")


message(STATUS "OpenCV library status:")
message(STATUS "    version: ${OpenCV_VERSION}")
message(STATUS "    libraries: ${OpenCV_LIBS}")
message(STATUS "    include path: ${OpenCV_INCLUDE_DIRS}")


add_executable(example-app example-app.cpp)
target_link_libraries(example-app ${TORCH_LIBRARIES} ${OpenCV_LIBS})
set_property(TARGET example-app PROPERTY CXX_STANDARD 14)

