cmake_minimum_required(VERSION 2.8)
project(useEigen)

set(CMAKE_BUILD_TYPE "Release")
set(CMAKE_CXX_FLAGS "-O3")

# 添加Eigen头文件
find_package(Eigen3 QUIET)
if(EIGEN3_FOUND)
    include_directories(${EIGEN3_INCLUDE_DIR})
else()
    include_directories("/usr/include/eigen3")
endif()

add_executable(eigenMatrix eigenMatrix.cpp)
add_executable(linearEqSolution linearEqSolution.cpp)
add_executable(matrixExtractAssign matrixExtractAssign.cpp)
