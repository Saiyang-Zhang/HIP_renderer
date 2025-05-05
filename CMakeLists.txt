cmake_minimum_required(VERSION 3.26)

set(CMAKE_HIP_PLATFORM nvidia CACHE STRING "")
set(CMAKE_HIP_ARCHITECTURES 89 CACHE STRING "")

project(HIP_Renderer LANGUAGES HIP CXX)

find_package(hip REQUIRED)
find_package(SDL2 REQUIRED)

add_executable(renderer main.hip)
target_link_libraries(renderer PRIVATE SDL2::SDL2 hip::device)
target_compile_features(renderer PRIVATE hip_std_17)