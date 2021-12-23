cmake_minimum_required(VERSION 3.20)
project(Glad LANGUAGES C)

add_library(${PROJECT_NAME} SHARED
	"${CMAKE_CURRENT_SOURCE_DIR}/include/glad/gl.h"
	"${CMAKE_CURRENT_SOURCE_DIR}/include/glad/vulkan.h"
	"${CMAKE_CURRENT_SOURCE_DIR}/include/KHR/khrplatform.h"
	"${CMAKE_CURRENT_SOURCE_DIR}/include/vk_platform.h"
	"${CMAKE_CURRENT_SOURCE_DIR}/src/gl.c"
	"${CMAKE_CURRENT_SOURCE_DIR}/src/vulkan.c"
)
add_library(${PROJECT_NAME}::${PROJECT_NAME} ALIAS ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME} PUBLIC
	"${CMAKE_CURRENT_SOURCE_DIR}/include/"
)

target_compile_definitions(${PROJECT_NAME}
	PUBLIC GLAD_API_CALL_EXPORT
	PRIVATE GLAD_API_CALL_EXPORT_BUILD
)

set_target_properties(${PROJECT_NAME} PROPERTIES
	OUTPUT_NAME "glad"
)
