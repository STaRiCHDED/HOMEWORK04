cmake_minimum_required(VERSION 3.10)
project(hello_world)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CURRENT_SOURCE_DIR /home/nikitaklimov/STaRiCHDED/workspace/projects/HOMEWORK03/tmp)

add_executable(hello_world ${CMAKE_CURRENT_SOURCE_DIR}/hello_world_application/hello_world.cpp)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/formatter_lib ${CMAKE_CURRENT_SOURCE_DIR}/formatter_ex_lib)

add_library(hello STATIC /home/nikitaklimov/STaRiCHDED/workspace/projects/HOMEWORK03/tmp/formatter_ex_lib/formatter_ex.cpp /home/nikitaklimov/STaRiCHDED/workspace/projects/HOMEWORK03/tmp/formatter_lib/formatter.cpp)

target_link_libraries(hello_world hello)
