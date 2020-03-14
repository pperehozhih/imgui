project(imgui)
cmake_minimum_required(VERSION 2.8)
set (SRC_IMGUI_LIST
	imgui.cpp
	imgui_draw.cpp
	imgui_demo.cpp
	imgui_widgets.cpp
	misc/freetype/imgui_freetype.cpp
)
file (GLOB HEADER_IMGUI_LIST "*.h*")
include_directories(misc/freetype .)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
if (NOT FREETYPE_FOUND)
	find_package(Freetype REQUIRED)
endif()
include_directories(${FREETYPE_INCLUDE_DIR_ft2build} ${FREETYPE_INCLUDE_DIR_freetype2})
if (BUILD_SHARED_LIBS)
	add_library(${PROJECT_NAME} SHARED ${SRC_IMGUI_LIST} ${HEADER_IMGUI_LIST})
	target_link_libraries(${PROJECT_NAME} ${FREETYPE_LIBRARIES})
else (BUILD_SHARED_LIBS)
	add_library(${PROJECT_NAME} ${SRC_IMGUI_LIST} ${HEADER_IMGUI_LIST})
	target_link_libraries(${PROJECT_NAME} ${FREETYPE_LIBRARIES})
endif()
