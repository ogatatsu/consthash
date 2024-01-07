
cmake_minimum_required(VERSION 3.1.4)

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror -std=c++11")

include(FetchContent)
FetchContent_Declare(
  googletest
  # Specify the commit you depend on and update it regularly.
  URL https://github.com/google/googletest/archive/5376968f6948923e2411081fd9372e71a59d8e77.zip
)
# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

add_executable(consthashtests
    dep/crc32.c
    dep/crc64.c
    dep/cityhash/city.cc
    crc32.cxx
    crc64.cxx
    city.cxx
    city32.cxx
    city64.cxx
    city128.cxx
)

target_include_directories(consthashtests PRIVATE dep/cityhash)
target_include_directories(consthashtests PRIVATE dep)

target_link_libraries(consthashtests
    consthash
    gtest_main
)

add_test(NAME consthashtests COMMAND consthashtests)
