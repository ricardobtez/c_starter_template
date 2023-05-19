cmake_minimum_required(VERSION 3.16)
project(c_started_project C)
include(CMake/StandardProjectSettings.cmake)
set(CMAKE_C_STANDARD 17)

add_library(project_options INTERFACE)

# Option specifications
option(ENABLE_TESTING "Enable Test Builds" OFF)

# Link this 'library' to use the warnings specified in CompilerWarnings.cmake
add_library(project_warnings INTERFACE)

# standard compiler warnings
include(CMake/CompilerWarnings.cmake)
set_project_warnings(project_warnings)

#include sub-projects
add_subdirectory(src)

if(ENABLE_TESTING)
    enable_testing()
    #add_subdirectory(googletest)
    add_subdirectory(test)
endif()
