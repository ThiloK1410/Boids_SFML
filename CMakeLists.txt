cmake_minimum_required(VERSION 3.19)
project(Boids)

set(CMAKE_CXX_STANDARD 14)

add_executable(Boids src/main.cpp src/Engine.cpp headers/Engine.h src/Boid.cpp headers/Boid.h)

include_directories(headers c:/SFML/include)
set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake_modules")
find_package(SFML REQUIRED system window graphics)
if (SFML_FOUND)
    include_directories(${SFML_INCLUDE_DIR})
    target_link_libraries(Boids ${SFML_LIBRARIES})
endif()

file(COPY assets DESTINATION ${CMAKE_BINARY_DIR})

if(WIN32)
    file(GLOB BINARY_DEP_DLLS "${SFML_INCLUDE_DIR}/../bin/*.dll")
    file(COPY ${BINARY_DEP_DLLS} DESTINATION ${CMAKE_BINARY_DIR})
endif()