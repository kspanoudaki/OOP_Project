cmake_minimum_required(VERSION 3.10)
set(CMAKE_TOOLCHAIN_FILE "C:/Users/path/to/vcpkg.cmake" CACHE STRING "")
project(MyProject)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(wxWidgets CONFIG REQUIRED COMPONENTS net core base)
find_package(cpr CONFIG REQUIRED)
find_package(nlohmann_json CONFIG REQUIRED)

#if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/logo.png")
#    file(COPY "${CMAKE_CURRENT_SOURCE_DIR}/logo.png" DESTINATION "${CMAKE_CURRENT_BINARY_DIR}/logo.png")
#endif()

file(COPY "${CMAKE_CURRENT_SOURCE_DIR}/images"
     DESTINATION "${CMAKE_CURRENT_BINARY_DIR}")
     
add_executable(MyProject WIN32 
    MyFrame.cpp
    MyApp.cpp
    Keyboard.cpp 
    Languages.h
)

target_link_libraries(MyProject PRIVATE 
    wx::wxnet
    wx::wxcore
    wx::wxbase
    cpr::cpr
    nlohmann_json::nlohmann_json
)