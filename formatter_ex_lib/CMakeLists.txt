set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CURRENT_SOURCE_DIR /home/nikitaklimov/STaRiCHDED/workspace/projects/HOMEWORK04/tmp/formatter_ex_lib)

add_library(formatter_ex STATIC ${CMAKE_CURRENT_SOURCE_DIR}/formatter_ex.cpp)

include_directories(${CMAKE_CURRENT_SOURCE_DIR})
include_directories(/home/nikitaklimov/STaRiCHDED/workspace/projects/HOMEWORK04/tmp/formatter_lib)
target_link_libraries(formatter_ex formatter)
