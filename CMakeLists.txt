cmake_minimum_required(VERSION 3.15)
project(BinaryShield VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Zydis CONFIG REQUIRED)

set(SOURCES
    src/main.cpp
    src/pe.cpp
    src/vm.cpp
    src/vm_section.cpp
    src/vm_handler.cpp
    src/virtual_instruction.cpp
    src/util.cpp
    src/function.cpp
    src/instruction.cpp
)

set(HEADERS
    src/pe.h
    src/vm.h
    src/vm_section.h
    src/vm_handler.h
    src/virtual_instruction.h
    src/util.h
    src/function.h
    src/instruction.h
)

add_executable(binaryshield ${SOURCES} ${HEADERS})

target_link_libraries(binaryshield PRIVATE Zydis::Zydis)

if(WIN32)
    set_target_properties(binaryshield PROPERTIES WIN32_EXECUTABLE FALSE)
endif()
