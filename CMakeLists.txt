#minimum required cmake version
cmake_minimum_required(VERSION 3.0.0)

#set the project name and version
project(opengl-engine VERSION 0.1.0 LANGUAGES C CXX)

# add opengl lib to project
find_package(OpenGL REQUIRED)

#add the include directories for header files
include_directories(
        ${PROJECT_SOURCE_DIR}/include
        ${PROJECT_SOURCE_DIR}/src
        ${PROJECT_SOURCE_DIR}/lib
)

# Collect all source files from src folder
file(GLOB SOURCES
        "${PROJECT_SOURCE_DIR}/include/*.h"
        "${PROJECT_SOURCE_DIR}/include/*.hpp"
        "${PROJECT_SOURCE_DIR}/src/*.cpp"
        "${PROJECT_SOURCE_DIR}/src/*.c"
        )

# Set the output directory for binaries        
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# Define the executable target
add_executable(opengl-engine ${SOURCES})

# link the included libraries
target_link_libraries(opengl-engine
        ${OPENGL_LIBRARY} 
        ${CMAKE_SOURCE_DIR}/lib/libglfw3.a)
