cmake_minimum_required(VERSION 3.0.2)

project(MandelLandscape CXX)

set(CMAKE_CXX_STANDARD 17)

include(CheckCXXCompilerFlag)

CHECK_CXX_COMPILER_FLAG(-Wall WALL)
if(WALL)
  add_definitions("-Wall")
endif()

CHECK_CXX_COMPILER_FLAG(-Werror WERROR)
if(WERROR)
  add_definitions("-Werror")
endif()

file(GLOB src "*.h" "*.cpp")

add_executable(app main.cpp ${src})

find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)
find_package(GLEW REQUIRED)

include_directories(
    ${OPENGL_INCLUDE_DIRS} 
    ${GLUT_INCLUDE_DIRS}
    ${GLEW_INCLUDE_DIRS})
target_link_libraries(app 
    ${OPENGL_LIBRARIES} 
    ${GLUT_LIBRARY}
    ${GLEW_LIBRARIES})
