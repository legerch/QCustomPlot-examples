cmake_minimum_required(VERSION 3.14)
project(qcustomplotexamples LANGUAGES CXX)

# Find architecture property
if(CMAKE_SIZEOF_VOID_P EQUAL 8)
    set(PROJECT_ARCH_TARGET "amd64")    # x64
elseif(CMAKE_SIZEOF_VOID_P EQUAL 4)     
    set(PROJECT_ARCH_TARGET "i386")     # x86
else()
    message(FATAL_ERROR "Unkwnown architecture, CMake will exit.")
endif()

# Export generated binaries
if(NOT PROJECT_BUILD_OUTPUT)
    set(PROJECT_BUILD_OUTPUT ${CMAKE_SOURCE_DIR}/build/output/${PROJECT_ARCH_TARGET}/${CMAKE_BUILD_TYPE})

    SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_BUILD_OUTPUT}/bin)
    SET(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${PROJECT_BUILD_OUTPUT}/lib)
    SET(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_BUILD_OUTPUT}/lib)
    SET(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_BUILD_OUTPUT}/bin)
endif()

# Run subdirectory routine
add_subdirectory(dependencies/QCustomPlot-library)

add_subdirectory(app-axis-tags)
add_subdirectory(app-interactions)
add_subdirectory(app-plots)
add_subdirectory(app-scrollbar-axis-range-control)
add_subdirectory(app-text-document-integration)
