cmake_minimum_required(VERSION 3.22)
project(platformer)

set(CMAKE_CXX_STANDARD 17)

find_package(raylib CONFIG REQUIRED)
find_package(glfw3  CONFIG REQUIRED)
if(APPLE)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fsanitize=address")
elseif(UNIX)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread -fsanitize=address -fsanitize=undefined")
endif()

add_executable(platformer src/platformer.cpp src/globals.h src/assets.h src/utilities.h src/level.h src/graphics.h src/player.h)
target_link_libraries(platformer PRIVATE raylib glfw)
