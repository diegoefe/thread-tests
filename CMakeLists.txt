cmake_minimum_required( VERSION 3.0 )

PROJECT(thread-tests)

if(DEFINED ENV{ACE_ROOT})
	set(ACE_INCLUDE_DIR=$ENV{ACE_ROOT}/include)
	set(ACE_LIBRARY=$ENV{ACE_ROOT}/lib/libACE.a)
endif()

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${PROJECT_SOURCE_DIR}")

find_package(ACE REQUIRED)
add_library(ace INTERFACE )
target_link_libraries(ace INTERFACE ${ACE_LIBRARIES})
target_include_directories(ace INTERFACE ${ACE_INCLUDE_DIRS})

add_executable(ace01 ace_ao_01.cpp)
target_link_libraries(ace01 ace)

add_executable(ace02 ace_pc_01.cpp)
target_link_libraries(ace02 ace)

add_executable(ace03 ace_reactor_01.cpp)
target_link_libraries(ace03 ace)

add_executable(ace04 ace_reactor_02.cpp)
target_link_libraries(ace04 ace)