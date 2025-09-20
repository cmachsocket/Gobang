cmake_minimum_required(VERSION 4.0)
project(gobang)
#set(CMAKE_CROSSCOMPILING 1)
#set(CMAKE_SYSTEM_NAME Windows)
#set(CMAKE_C_COMPILER   i686-w64-mingw32-gcc)
#set(CMAKE_CXX_COMPILER i686-w64-mingw32-g++)
set(CMAKE_CXX_STANDARD 20)
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()
set(CMAKE_CXX_FLAGS_RELEASE -Ofast)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -march=native")
set(CMAKE_CXX_FLAGS "${CMAKE_C_FLAGS} -O3  -Wall")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O3  -Wall")
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)
find_package(Qt6 REQUIRED COMPONENTS Concurrent)
include_directories(${CMAKE_CURRENT_BINARY_DIR})
find_package(Qt6 COMPONENTS
        Core
        Gui
        Widgets
        REQUIRED)
qt6_wrap_ui(UI_HEADERS mainwindow.ui)  # 处理UI文件

add_executable(gobang main.cpp
        ${UI_HEADERS}
        checkerboard.cpp
        checkerboard.h
        mainwindow.cpp
        mainwindow.h
        mainwindow.ui

)
target_link_libraries(gobang
        Qt::Core
        Qt::Gui
        Qt::Widgets
        Qt6::Concurrent
)