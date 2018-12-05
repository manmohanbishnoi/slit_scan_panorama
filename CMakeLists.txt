cmake_minimum_required(VERSION 3.13)

project(RealTimeOpenCV)

# Enable C++11 features 
set(CMAKE_CXX_STANDARD 11)

find_package(OpenCV REQUIRED)

include_directories(${OpenCV_INCLUDE_DIRS})
include_directories(${PROJECT_SOURCE_DIR}/include)

add_executable(RealTimeOpenCV ${PROJECT_SOURCE_DIR}/src/UTILITY.cpp 
                                ${PROJECT_SOURCE_DIR}/src/PRIMEPANORAMA.cpp
                                ${PROJECT_SOURCE_DIR}/src/DRAWIMAGE.cpp
                                ${PROJECT_SOURCE_DIR}/src/main.cpp )

target_link_libraries(RealTimeOpenCV ${OpenCV_LIBS})

set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT RealTimeOpenCV)

# copy files to binary directory for Visual Studio 2017+ under Windows
# Debug
file(COPY "${PROJECT_SOURCE_DIR}/data" DESTINATION "${PROJECT_BINARY_DIR}/Debug/")
file(COPY "${PROJECT_SOURCE_DIR}/output" DESTINATION "${PROJECT_BINARY_DIR}/Debug/")
# Release
file(COPY "${PROJECT_SOURCE_DIR}/data" DESTINATION "${PROJECT_BINARY_DIR}/Release/")
file(COPY "${PROJECT_SOURCE_DIR}/output" DESTINATION "${PROJECT_BINARY_DIR}/Release/")
