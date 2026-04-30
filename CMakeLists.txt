cmake_minimum_required(VERSION 3.10)
project(CompressorApp)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Includes path for external libraries
include_directories(external)

# Add source files for CLI
set(CLI_SOURCES
    src/main.cpp
    src/FileCompressor.cpp
    src/ImageCompressor.cpp
)

# Add source files for GUI
set(GUI_SOURCES
    src/gui_main.cpp
    src/FileCompressor.cpp
    src/ImageCompressor.cpp
)

# Create CLI executable
add_executable(compressor ${CLI_SOURCES})

# Create GUI executable (Windows only)
if(WIN32)
    add_executable(CompressionUI WIN32 ${GUI_SOURCES})
    target_link_libraries(CompressionUI comdlg32)
endif()

