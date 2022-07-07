# CMakeList.txt : CMake project for uniarm, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)

if(WIN32)
	add_definitions(-D_WIN32_WINNT=0x0601)
endif()

# Add source to this project's executable.
add_executable (uniarm "uniarm.cpp" "uniarm.h")

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET uniarm PROPERTY CXX_STANDARD 20)
endif()

set(UNICORN_HAS_ARM TRUE)
add_subdirectory("unicorn-2.0.0")

target_link_libraries(uniarm arm-softmmu)

# TODO: Add tests and install targets if needed.
