cmake_minimum_required (VERSION 3.8)
set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED TRUE)
# set(CMAKE_C_COMPILER "C:/Program Files/LLVM/bin/clang.exe" CACHE PATH "" FORCE)
set (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -std=c99")
set(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} -DZL_DEBUG")

set(CMAKE_TOOLCHAIN_FILE ${CMAKE_CURRENT_SOURCE_DIR}/vcpkg/scripts/buildsystems/vcpkg.cmake
  CACHE STRING "Vcpkg toolchain file")

project (ctemplate C)

if (WIN32)
    # ignore cross platform code
    add_definitions("-D_CRT_SECURE_NO_WARNINGS")
    add_definitions("-D_CRT_SCL_SECURE_NO_WARNINGS")
    add_definitions("-D_CRT_SECURE_NO_DEPRECATE")
    add_definitions("-D_CRT_NONSTDC_NO_DEPRECATE")
endif(WIN32)

add_subdirectory ("src")
add_subdirectory("test")

# add external dependecies
add_subdirectory("external/unity")