cmake_minimum_required(VERSION 3.14)
project(index)

set(CMAKE_CXX_STANDARD 17)

add_library(
        ${PROJECT_NAME} SHARED
        include/Index.hpp
        src/Index.cpp
)

target_include_directories(${PROJECT_NAME} PRIVATE include)

add_custom_command(
        TARGET ${PROJECT_NAME} POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy $<TARGET_FILE:${PROJECT_NAME}> ${ZIA_MODULE_DIR}
)
