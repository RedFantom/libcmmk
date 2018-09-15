# Author: RedFantom
# License: GNU GPLv3
# Copyright (c) 2018 RedFantom
cmake_minimum_required(VERSION 3.9)
project(libcmmk VERSION 0.1.0 DESCRIPTION "MasterKeys RGB Library")
include(FindLibUSB.txt)

add_library(cmmk SHARED libcmmk.c)
set_target_properties(cmmk PROPERTIES
        VERSION ${PROJECT_VERSION}
        PUBLIC_HEADER libcmmk.h
        PREFIX "")
target_link_libraries(cmmk usb-1.0)
include_directories(${LIBUSB_INCLUDE_DIR})

install(TARGETS cmmk
        LIBRARY DESTINATION lib
        PUBLIC_HEADER DESTINATION include)

add_executable(debug debug.c)
target_include_directories(debug PUBLIC .)
target_link_libraries(debug PUBLIC cmmk usb-1.0)
add_executable(test_cmmk test.c)
target_include_directories(test_cmmk PUBLIC .)
target_link_libraries(test_cmmk PUBLIC cmmk usb-1.0)
