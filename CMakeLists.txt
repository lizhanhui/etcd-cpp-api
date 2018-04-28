cmake_minimum_required (VERSION 3.1.3 FATAL_ERROR)
project (etcd-cpp-api)

find_library(CPPREST_LIB NAMES cpprest)
find_package(Boost REQUIRED COMPONENTS system thread locale random)

find_package(OpenSSL REQUIRED)

set (etcd-cpp-api_VERSION_MAJOR 0)
set (etcd-cpp-api_VERSION_MINOR 1)


include_directories(${CMAKE_CURRENT_SOURCE_DIR} ${OPENSSL_INCLUDE_DIR})
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror")

add_subdirectory(src)
option(RUN_TEST "off")

if(RUN_TEST)
enable_testing()
add_subdirectory(tst)
endif()
