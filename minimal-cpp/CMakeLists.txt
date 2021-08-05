cmake_minimum_required(VERSION 3.1)
project(HelloWorld)
message("Current source directory is " ${CMAKE_CURRENT_SOURCE_DIR})
#add_executable(generator generator.cpp)
#add_custom_command(OUTPUT generated.h COMMAND generator)

# Next is broken
add_custom_command(OUTPUT generated.h 
	COMMAND ${CMAKE_CURRENT_SOURCE_DIR}/generator.sh)

add_custom_command(OUTPUT echo.h
	COMMAND echo "#define GENERATED_PI 5.0" > generated.h)

add_custom_command(OUTPUT foo.h
	COMMAND pwd && ls ../ && cat generated.h)

add_custom_command(OUTPUT ${CMAKE_BINARY_SOURCE_DIR}/generated-sub.h
	COMMAND echo "#define AND_AGAIN" > ${CMAKE_BINARY_SOURCE_DIR}/generated-sub.h)

add_executable(hw hw.cpp hw.h echo.h foo.h generated.h generated-sub.h)


