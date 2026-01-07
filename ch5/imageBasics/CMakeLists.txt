project(imageBasics)

# 确保本子目录也能找到 OpenCV（顶层通常已搜索）
find_package(OpenCV REQUIRED)
message(STATUS "imageBasics: OpenCV ${OpenCV_VERSION}")

add_executable(imageBasics imageBasics.cpp)
target_include_directories(imageBasics PRIVATE ${OpenCV_INCLUDE_DIRS})
# 链接OpenCV库
target_link_libraries(imageBasics PRIVATE ${OpenCV_LIBS})

add_executable(undistortImage undistortImage.cpp)
target_include_directories(undistortImage PRIVATE ${OpenCV_INCLUDE_DIRS})
# 链接OpenCV库
target_link_libraries(undistortImage PRIVATE ${OpenCV_LIBS})
