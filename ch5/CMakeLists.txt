cmake_minimum_required(VERSION 3.1)

project(slambook2)

# 默认构建类型（允许通过 -DCMAKE_BUILD_TYPE=Debug/Release 覆盖）
if(NOT CMAKE_BUILD_TYPE)
	set(CMAKE_BUILD_TYPE "Release" CACHE STRING "Build type" FORCE)
endif()

# 生成 compile_commands.json，供 VS Code IntelliSense/clangd 使用
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
# 使用现代 CMake 指定 C++ 标准为 C++14（Pangolin/sigslot 需要 C++14）
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# 优化选项：仅在 Release 时开启（避免 Debug 也被 -O2 影响断点/变量查看）
if(CMAKE_BUILD_TYPE STREQUAL "Release")
	add_compile_options(-O2)
endif()

# Eigen
include_directories("/usr/include/eigen3")

# 寻找OpenCV库
find_package(OpenCV REQUIRED)
# 添加头文件
include_directories(${OpenCV_INCLUDE_DIRS})

add_subdirectory(imageBasics)
add_subdirectory(stereo)
add_subdirectory(rgbd)
