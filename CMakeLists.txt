cmake_minimum_required(VERSION 3.0)
project(DG_AUG)

set(CMAKE_CXX_STANDARD 14)
set(DDK_HOME "/home/ubuntu/tools/che/ddk_C30B890")
set(CMAKE_C_COMPILER  ${DDK_HOME}/toolchains/aarch64-linux-gcc6.3/bin/aarch64-linux-gnu-gcc)
set(CMAKE_CXX_COMPILER ${DDK_HOME}/toolchains/aarch64-linux-gcc6.3/bin/aarch64-linux-gnu-g++)
SET(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -std=c11")
SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
SET(CMAKE_BUILD_TYPE "Release")
include_directories(${DDK_HOME}/include/inc)
include_directories(${DDK_HOME}/include/inc/custom)
include_directories(${DDK_HOME}/include/libc_sec/include)
include_directories(${DDK_HOME}/include/third_party/protobuf/include)
include_directories(${DDK_HOME}/include/third_party/cereal/include)
link_directories(${DDK_HOME}/device/lib/)



add_executable(DG_AUG main.cpp)

target_link_libraries(DG_AUG
        "-Wl,-Bdynamic"
        -lDvpp_api
        -lDvpp_vpc
        -ldevmm
        -lmmpa
        -lc_sec
        -lslog
        )