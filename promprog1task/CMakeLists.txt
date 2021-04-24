cmake_minimum_required(VERSION 3.15)
project(promprog1task)

set(CMAKE_CXX_STANDARD 17)

add_executable(promprog1task main.cpp)



set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# generate file for project A
execute_process(
        COMMAND python ${CMAKE_SOURCE_DIR}/A/preparing.py
)

set(MAIN C/main.cpp B/lib.h B/lib.cpp C/main.cpp)

include_directories(.)

add_subdirectory(B)

add_executable(promprog1task ${MAIN})

target_link_libraries(promprog1task B_lib)