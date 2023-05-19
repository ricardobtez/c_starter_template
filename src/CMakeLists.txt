
cmake_minimum_required (VERSION 3.16)
set(CMAKE_C_STANDARD 11)
set(SOURCE_INCLUDE_DIRS
        ../include
        ./
        ./inc
        )

SET(PROJECT_API_INCLUDE_DIRS
    ../include
    )

set(AUX_SOURCE
        example.c
        )

# Add source to this project's executable.
add_library (c_started_project ${AUX_SOURCE})
target_include_directories(c_started_project PRIVATE ${SOURCE_INCLUDE_DIRS})
target_include_directories(c_started_project PUBLIC ${PROJECT_API_INCLUDE_DIRS})
target_link_libraries(c_started_project PRIVATE project_warnings project_options)

add_executable(c_started_project_exec main.c ${AUX_SOURCE})
target_include_directories(c_started_project_exec PRIVATE ${SOURCE_INCLUDE_DIRS})
target_include_directories(c_started_project_exec PUBLIC ${PROJECT_API_INCLUDE_DIRS})
target_link_libraries(c_started_project_exec PRIVATE project_warnings project_options)


