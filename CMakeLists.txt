cmake_minimum_required(VERSION 3.22)

project( PathTracer )

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if (DEFINED VCPKG_TARGET_ARCHITECTURE)
    set(DIRECTX_ARCH ${VCPKG_TARGET_ARCHITECTURE})
elseif(CMAKE_GENERATOR_PLATFORM MATCHES "^[Ww][Ii][Nn]32$")
    set(DIRECTX_ARCH x86)
elseif(CMAKE_GENERATOR_PLATFORM MATCHES "^[Xx]64$")
    set(DIRECTX_ARCH x64)
endif()

add_subdirectory(src)


set(EXECUTABLE_RELEASE_PATH ${PROJECT_BINARY_DIR}/src/Release)
set(EXECUTABLE_DEBUG_PATH ${PROJECT_BINARY_DIR}/src/Debug)

configure_file(shader/path_tracer.hlsl ${EXECUTABLE_RELEASE_PATH}/shader/path_tracer.hlsl COPYONLY)
configure_file(shader/path_tracer.hlsl ${EXECUTABLE_DEBUG_PATH}/shader/path_tracer.hlsl COPYONLY)