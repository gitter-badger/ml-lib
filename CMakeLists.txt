CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

set(PROJECT_NAME ml-lib)
project(${PROJECT_NAME})

set(LIBRARY     "lib_${PROJECT_NAME}")
set(TESTS       "test_${PROJECT_NAME}")

include_directories("${CMAKE_CURRENT_SOURCE_DIR}/include")

FILE(GLOB hdrs "*.h*" "${CMAKE_CURRENT_SOURCE_DIR}/include/*.h*")
FILE(GLOB srcs "*.cpp" "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp")

add_library(${LIBRARY} STATIC ${srcs} ${hdrs})

#
# Add Google Test
#
include_directories("${CMAKE_CURRENT_SOURCE_DIR}/3rdparty")
add_subdirectory("${CMAKE_CURRENT_SOURCE_DIR}/3rdparty/gtest")
set(LIBRARY_DEPS "gtest")

add_subdirectory(samples)
add_subdirectory(test)
