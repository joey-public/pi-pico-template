cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
#set(PICO_BOARD pico)  #if using the base pico board
set(PICO_BOARD pico_w) #if using the pico w board 
set(PICO_PLATFORM rp2040)
set(PICO_COMPILER pico_arm_gcc)

set(PROJECT_NAME template)

# Optional Line: note this needs to be copied into your project directory
# cp $PICO_SDK_PATH/external/pico_sdk_import.cmake ./
include(pico_sdk_import.cmake)
# Another way of doing it without any copying  
# include($ENV{PICO_SDK_PATH}/external/pico_sdk_import.cmake)

project(${PROJECT_NAME} C CXX ASM)

pico_sdk_init()

add_executable(${PROJECT_NAME}
    ${PROJECT_NAME}.c
)

#for pico_w
target_link_libraries(${PROJECT_NAME}
        pico_stdlib              # for core functionality
        pico_cyw43_arch_none     # we need Wifi to access the GPIO, but we don't need anything else
        )

pico_enable_stdio_usb(${PROJECT_NAME} 1)
pico_enable_stdio_uart(${PROJECT_NAME} 0)

pico_add_extra_outputs(${PROJECT_NAME})
