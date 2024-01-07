
cmake_minimum_required(VERSION 3.1.4)
project(consthash)

option(BUILD_TESTS "Build unit tests" OFF)

add_library(consthash INTERFACE)
target_include_directories(consthash INTERFACE include)

if (BUILD_TESTS)
    enable_testing()
    add_subdirectory(tests)
endif()
