project(BTSK)

cmake_minimum_required(VERSION 2.6.2)

if(${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_BINARY_DIR})
  message(FATAL_ERROR "In-source builds not allowed. Please make a new directory (called a build directory) and run CMake from there. You may need to remove CMakeCache.txt. ")
endif()

if (NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE "Release")
endif()

string(TOLOWER "${CMAKE_BUILD_TYPE}" cmake_build_type_tolower)
if(    NOT cmake_build_type_tolower STREQUAL "debug"
   AND NOT cmake_build_type_tolower STREQUAL "release"
   AND NOT cmake_build_type_tolower STREQUAL "relwithdebinfo")
  message(FATAL_ERROR "Unknown build type \"${CMAKE_BUILD_TYPE}\". Allowed values are Debug, Release, RelWithDebInfo (case-insensitive).")
endif()

add_definitions("-std=c++11")

include_directories(include)

set(SOURCE_FILES 
  src/BehaviorTreeShared.cpp
  src/BehaviorTree.cpp
  src/BehaviorTreeEvent.cpp
  src/Test.cpp
  src/BehaviorTreeOptimized.cpp
)

add_library(btsk ${SOURCE_FILES})

