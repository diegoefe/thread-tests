cmake_minimum_required( VERSION 3.0 )

PROJECT(thread-tests)

if(DEFINED ENV{ACE_ROOT})
	set(ACE_INCLUDE_DIR=$ENV{ACE_ROOT}/include)
	set(ACE_LIBRARY=$ENV{ACE_ROOT}/lib/libACE.a)
endif()

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${PROJECT_SOURCE_DIR}")

#include(FindACE.cmake)
find_package(ACE REQUIRED)
add_library(ace INTERFACE )
target_link_libraries(ace INTERFACE ${ACE_LIBRARIES})
target_include_directories(ace INTERFACE ${ACE_INCLUDE_DIRS})

add_executable(ace01 ace_ao_01.cpp)
target_link_libraries(ace01 ace)
