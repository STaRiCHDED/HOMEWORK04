cmake_minimum_required(VERSION 3.10)
project(Solver)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CURRENT_SOURCE_DIR /home/nikitaklimov/STaRiCHDED/workspace/projects/HOMEWORK04/tmp)
add_executable(Solver ${CMAKE_CURRENT_SOURCE_DIR}/solver_application/equation.cpp)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/formatter_lib ${CMAKE_CURRENT_SOURCE_DIR}/formatter_ex_lib ${CMAKE_CURRENT_SOURCE_DIR}/solver_lib)
add_library(solver STATIC /home/nikitaklimov/STaRiCHDED/workspace/projects/HOMEWORK04/tmp/solver_lib/solver.cpp 
/home/nikitaklimov/STaRiCHDED/workspace/projects/HOMEWORK04/tmp/formatter_ex_lib/formatter_ex.cpp 
/home/nikitaklimov/STaRiCHDED/workspace/projects/HOMEWORK04/tmp/formatter_lib/formatter.cpp)
target_link_libraries(Solver solver)
