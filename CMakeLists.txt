cmake_minimum_required(VERSION 3.10)
project(OpenGL3_Tutorial)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_MODULE_PATH /home/peixoto/cmake)

FIND_PATH( SOIL_INCLUDE_DIRS SOIL.h PATH_SUFFIXES SOIL )
FIND_LIBRARY( SOIL_LIBRARIES SOIL)

include_directories(include ${OPENGL_INCLUDE_DIR}  ${GLU_INCLUDE_DIRS} ${GLEW_INCLUDE_DIRS})

find_package (OpenGL REQUIRED)
include_directories(${OpenGL_INCLUDE_DIRS})
link_directories(${OpenGL_LIBRARY_DIRS})
add_definitions(${OpenGL_DEFINITIONS})

if(NOT OpenGL_FOUND)
    message(Error "OpenGL not found")
endif(NOT OpenGL_FOUND)

find_package (GLEW REQUIRED)
include_directories(${GLEW_INCLUDE_DIRS})
add_definitions(${GLEW_DEFINITIONS})
if(NOT GLEW_FOUND)
    message(Error " GLEW not found")
endif(NOT GLEW_FOUND)

find_package(GLFW REQUIRED)
include_directories(${GLFW_INCLUDE_DIRS})
link_directories(${GLFW_LIBRARY_DIRS})
add_definitions(${GLFW_DEFINITIONS})
if(NOT GLFW_FOUND)
    message(Error "GLFW not found")
endif(NOT GLFW_FOUND)

find_package(GLM REQUIRED)
include_directories(${GLM_INCLUDE_DIRS})
link_directories(${GLM_LIBRARY_DIRS})
add_definitions(${GLM_DEFINITIONS})

if(NOT GLM_FOUND)
    message(Error "GLM not found")
endif(NOT GLM_FOUND)

#add_executable(OpenGL3_Tutorial common/shader.cpp common/shader.hpp tutorial01.cpp)
#add_executable(OpenGL3_Tutorial common/shader.cpp common/shader.hpp tutorial02.cpp)
#add_executable(OpenGL3_Tutorial common/shader.cpp common/shader.hpp tutorial03.cpp)
#add_executable(OpenGL3_Tutorial common/shader.cpp common/shader.hpp tutorial04.cpp)
#add_executable(OpenGL3_Tutorial common/shader.cpp common/shader.hpp tutorial04_1.cpp)
add_executable(OpenGL3_Tutorial common/texture.cpp common/texture.hpp common/shader.cpp common/shader.hpp tutorial05.cpp tutorial05.cpp)

target_link_libraries (OpenGL3_Tutorial ${OPENGL_LIBRARIES} ${GLFW_LIBRARIES} ${GLEW_LIBRARIES} ${GLM_LIBRARIES} ${SOIL_LIBRARIES})