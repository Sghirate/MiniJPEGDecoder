cmake_minimum_required(VERSION 3.10 FATAL_ERROR)

project(jpeg_decoder)

option(JPEG_DECODER_BUILD_TEST "Build the test app" ON)

add_library(jpeg_decoder INTERFACE)
target_include_directories(jpeg_decoder INTERFACE include/)
target_sources(jpeg_decoder INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/include/jpeg_decoder.hpp)

if(JPEG_DECODER_BUILD_TEST)
    add_executable(jpeg_decoder_test src/jpeg_decoder_test.cpp)
    target_link_libraries(jpeg_decoder_test PRIVATE jpeg_decoder)
endif()
