cmake_minimum_required(VERSION 3.16)
project(TetroNixC  VERSION 0.1.0 LANGUAGES C)

set(CMAKE_C_STANDARD 17)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS OFF)

find_package(Curses REQUIRED)

if(CURSES_FOUND)
    message(STATUS "   NCurses encontrado:")
    message(STATUS "   Include path: ${CURSES_INCLUDE_DIRS}")
    message(STATUS "   Libraries: ${CURSES_LIBRARIES}")
    if(HAVE_CURSES_COLOR)
        message(STATUS "   Soporte para COLOR detectado")
    endif()
endif()

add_compile_options(
    -Wall
    -Wextra
    -Werror
    -Wpedantic
    -Wshadow
    -Wunused
    -Wconversion
    -Wno-deprecated-declarations
)

add_executable(${PROJECT_NAME} 
    src/main.c
)

target_link_libraries(${PROJECT_NAME} PRIVATE ${CURSES_LIBRARIES})
target_include_directories(${PROJECT_NAME} PRIVATE ${CURSES_INCLUDE_DIRS} include)
