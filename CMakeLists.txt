cmake_minimum_required(VERSION 3.25)
project(HalogenGameEngine)

set(CMAKE_CXX_STANDARD 17)

# OpenGL
find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIRS})

# GLFW
set(GLFW_BUILD_EXAMPLES OFF CACHE INTERNAL "Build the GLFW example programs")
set(GLFW_BUILD_TESTS OFF CACHE INTERNAL "Build the GLFW test programs")
set(GLFW_BUILD_DOCS OFF CACHE INTERNAL "Build the GLFW documentation")
set(GLFW_INSTALL OFF CACHE INTERNAL "Generate installation target")
add_subdirectory(extern/glfw)

include_directories(${CMAKE_SOURCE_DIR}/extern/glfw/include)

add_executable(HalogenGameEngine main.cpp)

# Link against GLFW and OpenGL
target_link_libraries(HalogenGameEngine glfw)
target_link_libraries(HalogenGameEngine OpenGL::GL)
