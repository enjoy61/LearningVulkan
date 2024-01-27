cmake_minimum_required( VERSION 3.28 )

project(HelloTriangle)

set(CMAKE_CXX_STANDARD 17)


# export GLFW_HOME="/usr/local/Cellar/glfw/3.3.9"

# 检查环境变量
# if (NOT DEFINED ENV{GLFW_HOME})
#    message(FATAL_ERROR "found no env named GLFW_HOME")
# endif()

# set(GLFW_HOME $ENV{GLFW_HOME})

add_executable(HelloTriangle main.cpp)

# 添加 GLFW3 预编译库
add_library(glfw SHARED IMPORTED)
# SET_TARGET_PROPERTIES(glfw PROPERTIES IMPORTED_LOCATION "${GLFW_HOME}/lib/libglfw.3.3.dylib")
SET_TARGET_PROPERTIES(glfw PROPERTIES IMPORTED_LOCATION "/usr/local/Cellar/glfw/3.3.9/lib/libglfw.3.3.dylib")

# Vulkan
# find_package(Vulkan REQUIRED FATAL_ERROR)
find_package(Vulkan REQUIRED)
target_link_libraries(${PROJECT_NAME} glfw Vulkan::Vulkan)
# include_directories(${Vulkan_INCLUDE_DIRS})
# target_include_directories(${PROJECT_NAME} PUBLIC ${Vulkan_INCLUDE_DIRS})

# copy the shader files to the cmake-build-debug folder
file(COPY shaders DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
