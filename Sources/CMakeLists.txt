file(GLOB_RECURSE SOURCES "*.cpp" "*.hpp" "*.c")
add_executable(${CMAKE_PROJECT_NAME} ${SOURCES})
#target_include_directories(${CMAKE_PROJECT_NAME} "${CMAKE_SOURCE_DIR}/include")
