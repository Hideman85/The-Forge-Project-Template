cmake_minimum_required(VERSION 3.13)

if(COMMAND cmake_policy)
    cmake_policy(SET CMP0077 NEW) # for option overriding
    cmake_policy(SET CMP0003 NEW)
endif(COMMAND cmake_policy)

project(TheForgeTemplateProject)

##########################################
##      Configure our build system
##########################################
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_EXTENSIONS ON)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

include_directories(SYSTEM include)

##########################################
##      Copy resources
##########################################
file(MAKE_DIRECTORY "${CMAKE_BINARY_DIR}/Resources")
file(GLOB resources "Resources/*/")
foreach(resource ${resources})
    file(COPY "${resource}" DESTINATION "${CMAKE_BINARY_DIR}/Resources")
endforeach()

##########################################
##      Add libs
##########################################
add_subdirectory(Libs)
get_directory_property(COMPILE_DEFINITIONS DIRECTORY Libs/The-Forge DEFINITION COMPILE_DEFINITIONS)
get_directory_property(THE_FORGE_LIBS DIRECTORY Libs/The-Forge DEFINITION THE_FORGE_LIBS)
add_compile_definitions(${COMPILE_DEFINITIONS})
link_libraries(${THE_FORGE_LIBS})

##########################################
##      Add libs
##########################################
add_subdirectory(Sources)
