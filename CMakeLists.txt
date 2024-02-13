cmake_minimum_required(VERSION 3.0.0)
project(opengl-engine VERSION 0.1.0 LANGUAGES C CXX)
# add_library(
#     hello
#     hello.h
#     hello.cpp

# )
find_package(OpenGL REQUIRED)

include_directories(
        ${PROJECT_SOURCE_DIR}/include
        ${PROJECT_SOURCE_DIR}/src
        ${PROJECT_SOURCE_DIR}/lib
)

file(GLOB all_SRCS
        "${PROJECT_SOURCE_DIR}/include/*.h"
        "${PROJECT_SOURCE_DIR}/include/*.hpp"
        "${PROJECT_SOURCE_DIR}/src/*.cpp"
        "${PROJECT_SOURCE_DIR}/src/*.c"
        )
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# add_executable(opengl-engine main.cpp)
add_executable(opengl-engine ${all_SRCS})
target_link_libraries(opengl-engine
        ${OPENGL_LIBRARY} 
        ${CMAKE_SOURCE_DIR}/lib/libglfw3.a)
# target_link_libraries(opengl-engine PRIVATE hello)
