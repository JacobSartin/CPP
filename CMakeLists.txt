cmake_minimum_required(VERSION 4.0.0)

# find and replace all cpp with the name of your project
project(cpp
    VERSION 0.1.0
    LANGUAGES CXX
)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

option(WARNINGS_AS_ERRORS "Treat compiler warnings as errors" ON)

add_executable(cpp)

target_sources(cpp
    PRIVATE
        src/main.cpp
)

target_compile_features(cpp
    PRIVATE
        cxx_std_20
)

set_target_properties(cpp
    PROPERTIES
        CXX_EXTENSIONS OFF
)

if(CMAKE_CXX_COMPILER_FRONTEND_VARIANT STREQUAL "MSVC")
    target_compile_options(cpp
        PRIVATE
            /W4
            $<$<BOOL:${WARNINGS_AS_ERRORS}>:/WX>
    )
else()
    target_compile_options(cpp
        PRIVATE
            -Wall
            -Wextra
            -Wpedantic
            -Wconversion
            -Wsign-conversion
            $<$<BOOL:${WARNINGS_AS_ERRORS}>:-Werror>
    )
endif()
