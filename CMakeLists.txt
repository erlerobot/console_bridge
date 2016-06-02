cmake_minimum_required(VERSION 2.8.3)

project(console_bridge)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -Wall -Wextra")

find_package(ament_cmake REQUIRED)

## Add serial library
add_library(${PROJECT_NAME} SHARED 
  src/console.cpp
)

ament_export_libraries(${PROJECT_NAME})

ament_package()

## Include headers
include_directories(include)

install(
  TARGETS ${PROJECT_NAME}
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION bin
)

install(
  DIRECTORY include/
  DESTINATION include
)