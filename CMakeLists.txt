cmake_minimum_required(VERSION 3.13)
project(chacha20)

include_directories(chacha)

option(OPTIMIZE_NAIVE "Enable -march=native -mtune=native" OFF)

add_library(chacha20 INTERFACE)
target_include_directories(chacha20 INTERFACE
	${CMAKE_CURRENT_SOURCE_DIR})
target_compile_features(chacha20 INTERFACE cxx_std_17)

add_executable(demo
	demo.cpp)
target_link_libraries(demo PRIVATE chacha20)

if (${OPTIMIZE_NATIVE})
	target_compile_options(demo PRIVATE "-march=native" "-mtune=native")
endif ()
