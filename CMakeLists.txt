cmake_minimum_required(VERSION 3.16)
#this file needs at least CMake 3.16 to work
project(ZoneRunner LANGUAGES C CXX)
#naming the project name and saying it uses C and C++

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
#C++ should be used and stop with error if C++17 is not available

include(FetchContent)
set(SDL_SHARED OFF CACHE BOOL "" FORCE)
SET(SDL_STATIC ON CACHE BOOL "" FORCE)
FetchContent_Declare(
    SDL3
    GIT_REPOSITORY https://github.com/libsdl-org/SDL.git
    GIT_TAG        release-3.4.18
    GIT_SHALLOW    TRUE
    )
FetchContent_MakeAvailable(SDL3)
#downloads SDL3 from the given git repository and makes it available for use in the project

add_executable(zone_runner src/main.cpp)
target_link_libraries(zone_runner PRIVATE SDL3::SDL3-static)
#build a program called zone_runner from src/main.cpp, executable is a program u can run
#connect the SDL3 to the program, making it available for linking