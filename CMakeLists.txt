project(imgui)
cmake_minimum_required(VERSION 2.8)
set (SRC_IMGUI_LIST
	imgui.cpp
	imgui_draw.cpp
	imgui_demo.cpp
)
file (GLOB HEADER_IMGUI_LIST "*.h*")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
if (BUILD_SHARED_LIBS)
	add_library(${PROJECT_NAME} SHARED ${SRC_IMGUI_LIST} ${HEADER_IMGUI_LIST})
else (BUILD_SHARED_LIBS)
	add_library(${PROJECT_NAME} ${SRC_IMGUI_LIST} ${HEADER_IMGUI_LIST})
endif()
