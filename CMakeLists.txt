cmake_minimum_required(VERSION 3.25.2)

project(Make LANGUAGES C)

add_library(HEADER-ONLY INTERFACE)
add_library(PROJECTLIB INTERFACE)
target_include_directories(HEADER-ONLY INTERFACE ${CMAKE_SOURCE_DIR}/include)
target_include_directories(PROJECTLIB INTERFACE ${CMAKE_SOURCE_DIR}/lib)
target_link_libraries(HEADER-ONLY INTERFACE PROJECTLIB)

add_executable(main ./src/main.c)

target_link_libraries(main PRIVATE HEADER-ONLY)