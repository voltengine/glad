cmake_minimum_required(VERSION 3.20)
project(Glad LANGUAGES C)

file(GLOB_RECURSE TARGET_SOURCES CONFIGURE_DEPENDS
	"${CMAKE_CURRENT_SOURCE_DIR}/include/*.h"
	"${CMAKE_CURRENT_SOURCE_DIR}/src/*.c"
)

add_library(${PROJECT_NAME} SHARED ${TARGET_SOURCES})
add_library(${PROJECT_NAME}::${PROJECT_NAME} ALIAS ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME} PUBLIC
	"${CMAKE_CURRENT_SOURCE_DIR}/include/"
)

target_compile_definitions(${PROJECT_NAME} PUBLIC GLAD_API_CALL_EXPORT)
target_compile_definitions(${PROJECT_NAME} PRIVATE GLAD_API_CALL_EXPORT_BUILD)

set_target_properties(${PROJECT_NAME} PROPERTIES
	OUTPUT_NAME "glad"
)
