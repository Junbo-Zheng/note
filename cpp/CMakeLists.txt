# Date      2022.02.01
# Author    dingddding@163.com
# Bref      The CMakeLists.txt

cmake_minimum_required(VERSION 3.21)
note_generate_target(./ cpp TARGETS)

project(note-cpp LANGUAGES CXX)

find_package(Threads)

foreach (TARGET ${TARGETS})
    target_link_libraries(${TARGET} Threads::Threads)
    set_target_properties(
            ${TARGET}
            PROPERTIES
            C_STANDARD 11
            C_EXTENSIONS OFF
            C_STANDARD_REQUIRED ON
            CXX_STANDARD 23
            CXX_EXTENSIONS OFF
            CXX_STANDARD_REQUIRED OFF
    )
endforeach ()

if (CMAKE_VERSION VERSION_GREATER_EQUAL 3.8)
    add_subdirectory(module)
endif ()
