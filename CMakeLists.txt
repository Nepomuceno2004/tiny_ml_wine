cmake_minimum_required(VERSION 3.13)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
# == DO NOT EDIT THE FOLLOWING LINES for the Raspberry Pi Pico VS Code Extension to work ==
if(WIN32)
    set(USERHOME $ENV{USERPROFILE})
else()
    set(USERHOME $ENV{HOME})
endif()
set(sdkVersion 2.2.0)
set(toolchainVersion 14_2_Rel1)
set(picotoolVersion 2.2.0-a4)
set(picoVscode ${USERHOME}/.pico-sdk/cmake/pico-vscode.cmake)
if (EXISTS ${picoVscode})
    include(${picoVscode})
endif()
# ====================================================================================
set(PICO_BOARD pico_w CACHE STRING "Board type")

include(pico_sdk_import.cmake)
project(ttiny_ml_wine C CXX ASM)
pico_sdk_init()

add_subdirectory(lib/pico-tflmicro EXCLUDE_FROM_ALL)

add_executable(ttiny_ml_wine
    tiny_ml_wine.c
    tflm_wrapper.cpp
    tflm_wrapper.h
    wine_mlp_float.h
)

pico_set_program_name(ttiny_ml_wine "ttiny_ml_wine")
pico_set_program_version(ttiny_ml_wine "0.1")

pico_enable_stdio_uart(ttiny_ml_wine 0)
pico_enable_stdio_usb(ttiny_ml_wine 1)

target_link_libraries(ttiny_ml_wine
    pico_stdlib
    hardware_sync
    pico-tflmicro
)

target_include_directories(ttiny_ml_wine PRIVATE
    ${CMAKE_CURRENT_LIST_DIR}
)

pico_add_extra_outputs(ttiny_ml_wine)