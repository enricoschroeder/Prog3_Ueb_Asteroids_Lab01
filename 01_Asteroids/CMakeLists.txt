cmake_minimum_required(VERSION 3.11)

set(EXECUTABLE_NAME 01_Asteroids)

set(SRC_FILES
        ${CMAKE_CURRENT_LIST_DIR}/src/main.cpp)

set(INCLUDE_DIRS
        ${CMAKE_CURRENT_LIST_DIR}/raylib-cpp/v451
        ${CMAKE_CURRENT_LIST_DIR}/include)

add_executable(${EXECUTABLE_NAME} ${SRC_FILES})
target_include_directories(${EXECUTABLE_NAME} PRIVATE ${INCLUDE_DIRS})
target_link_libraries(${EXECUTABLE_NAME} raylib)

# Checks if OSX and links appropriate frameworks (only required on MacOS)
if (APPLE)
    target_link_libraries(${EXECUTABLE_NAME} "-framework IOKit")
    target_link_libraries(${EXECUTABLE_NAME} "-framework Cocoa")
    target_link_libraries(${EXECUTABLE_NAME} "-framework OpenGL")
endif()

# Copy resources to target directory
file(COPY ${CMAKE_CURRENT_LIST_DIR}/resources
     DESTINATION ${CMAKE_CURRENT_BINARY_DIR})