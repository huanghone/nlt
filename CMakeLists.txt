cmake_minimum_required(VERSION 3.22)

project(nlc)

include_directories(${CMAKE_SOURCE_DIR})

find_package(OpenGL REQUIRED)
list(APPEND LINK_LIBS ${OPENGL_LIBRARIES})

include_directories(${CMAKE_SOURCE_DIR}/lib/glm/include)

set(glfw3_DIR ${CMAKE_SOURCE_DIR}/lib/glfw/lib/cmake/glfw3)
find_package(glfw3 REQUIRED)
list(APPEND LINK_LIBS glfw)

set(glew_DIR ${CMAKE_SOURCE_DIR}/lib/glew)
set(GLEW_INCLUDE_DIRS ${glew_DIR}/include)
if(WIN32)
	set(GLEW_LIBS ${glew_DIR}/lib/glew.lib)
elseif(APPLE)
	set(GLEW_LIBS ${glew_DIR}/lib/libglew.dylib)
else()
	set(GLEW_LIBS ${glew_DIR}/lib/libglew.so)
endif()
INCLUDE_DIRECTORIES(${GLEW_INCLUDE_DIRS})
list(APPEND LINK_LIBS ${GLEW_LIBS})
#add_definitions(-DGLEW_STATIC)

set(assimp_DIR ${CMAKE_SOURCE_DIR}/lib/assimp/lib/cmake/assimp-3.3)
#set(assimp_DIR ${CMAKE_SOURCE_DIR}/lib/assimp)
find_package(assimp REQUIRED)
include_directories(${ASSIMP_INCLUDE_DIR})
list(APPEND LINK_LIBS ${ASSIMP_LIBRARY_DIRS}/${ASSIMP_LIBRARIES}.lib)

if(WIN32)
	set(OpenCV_DIR ${CMAKE_SOURCE_DIR}/lib/opencv)
else()
	set(OpenCV_DIR ${CMAKE_SOURCE_DIR}/lib/opencv/share/OpenCV)
endif()
find_package(OpenCV REQUIRED)
INCLUDE_DIRECTORIES(${OpenCV_INCLUDE_DIRS})
list(APPEND LINK_LIBS ${OpenCV_LIBS})

add_subdirectory(src)
#add_subdirectory(CVX)
#add_subdirectory(BFC)