cmake_minimum_required(VERSION 3.21)

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Release")
endif()

project(myapp CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# -----------------------------------------------------------------------------
# Paths
# -----------------------------------------------------------------------------
set(SDL3_DIR "C:/libs/sdl3-3.4.18-android")

# -----------------------------------------------------------------------------
# Native Shared Library Target
# -----------------------------------------------------------------------------
add_library(main SHARED
    src/main.cpp
)

# -----------------------------------------------------------------------------
# Include Directories
# -----------------------------------------------------------------------------
target_include_directories(main PRIVATE
    ${SDL3_DIR}/${ANDROID_ABI}/include
)

# -----------------------------------------------------------------------------
# Link SDL3 & Android System Libraries
# -----------------------------------------------------------------------------
target_link_libraries(main PRIVATE
    ${SDL3_DIR}/${ANDROID_ABI}/lib/libSDL3.so
    GLESv3
    EGL
    android
    log
)