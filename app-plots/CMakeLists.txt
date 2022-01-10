cmake_minimum_required(VERSION 3.14)

# Set project properties
set(PROJECT_NAME example-plots)
set(PROJECT_VERSION_SEMANTIC 1.0.0)

# Set project configuration
project(${PROJECT_NAME} LANGUAGES CXX)
project(${PROJECT_NAME} VERSION ${PROJECT_VERSION_SEMANTIC})

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_AUTOUIC ON)   # Specific to Qt
set(CMAKE_AUTOMOC ON)   # Specific to Qt
set(CMAKE_AUTORCC ON)   # Specific to Qt

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Configure file project - File containing macro that can be used in project
configure_file("${CMAKE_CURRENT_SOURCE_DIR}/config.h.in" "${CMAKE_CURRENT_SOURCE_DIR}/config.h")

# Find Qt packages
find_package(QT NAMES Qt6 Qt5 COMPONENTS Core Widgets REQUIRED)
find_package(Qt${QT_VERSION_MAJOR} COMPONENTS Core Widgets REQUIRED)

# Manage application files
set(PROJECT_HEADERS
    config.h
    mainwindow.h
)

set(PROJECT_SOURCES
    main.cpp
    mainwindow.cpp
)

set(PROJECT_UI
    mainwindow.ui
)

set(PROJECT_RSC

)

set(PROJECT_FILES ${PROJECT_RSC} ${PROJECT_UI} ${PROJECT_HEADERS} ${PROJECT_SOURCES})

# Platform dependant stuff
# Windows (for both x86/x64)
if(WIN32)   
    SET(PROJECT_BUILD_ARGS WIN32)
endif()

# MacOS (for both x86/x64)
if(UNIX AND APPLE)   
    SET(PROJECT_BUILD_ARGS "")
endif()

# Linux, BSD, Solaris, Minix (for both x86/x64)
if(UNIX AND NOT APPLE)   
    SET(PROJECT_BUILD_ARGS "")
endif()

# Add files to the application
add_executable(${PROJECT_NAME} ${PROJECT_BUILD_ARGS} ${PROJECT_FILES})

# Set version of executable
set_target_properties(${PROJECT_NAME} PROPERTIES 
                        VERSION ${PROJECT_VERSION}
                        SOVERSION ${PROJECT_VERSION_MAJOR})

# Link needed libraries
# Qt Library
target_link_libraries(${PROJECT_NAME} PRIVATE Qt${QT_VERSION_MAJOR}::Core)
target_link_libraries(${PROJECT_NAME} PRIVATE Qt${QT_VERSION_MAJOR}::Widgets)

# QCustomPlot library
target_link_libraries(${PROJECT_NAME} PRIVATE qcustomplot)

# Compile needed definitions
# No definitions to compile
