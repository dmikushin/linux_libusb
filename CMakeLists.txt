cmake_minimum_required(VERSION 3.1)

project(libusb LANGUAGES C VERSION 3.0)

set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

add_library(${PROJECT_NAME} STATIC
    libusb20.c
    libusb20_desc.c
    libusb20_ugen20.c
    libusb01.c
    libusb10.c
    libusb10_desc.c
    libusb10_hotplug.c
    libusb10_io.c)
add_library(LibUSB::LibUSB ALIAS ${PROJECT_NAME})
set_target_properties(${PROJECT_NAME} PROPERTIES POSITION_INDEPENDENT_CODE ON)
target_link_libraries(${PROJECT_NAME} PRIVATE Threads::Threads)
