cmake_minimum_required(VERSION 3.0)
project(MakeGeneratorsWork VERSION 1.0.0)


add_custom_command(
	OUTPUT generated.cpp
	COMMAND my_cmake_generator ${CMAKE_CURRENT_BINARY_DIR}/generated.cpp
)

add_custom_command(
	OUTPUT local.cpp
	COMMAND my_cmake_generator local.cpp
)

add_custom_command(
	OUTPUT local.h
	COMMAND my_cmake_generator local.h
)

add_custom_command(
	OUTPUT echo.h
	#COMMAND echo "#define PI 7" > ${CMAKE_CURRENT_BINARY_DIR}/echo.h
	COMMAND date > ${CMAKE_CURRENT_BINARY_DIR}/echo.h
)

add_executable(myapp
	main.cpp
	local.cpp
	echo.h
	local.h
	${CMAKE_CURRENT_BINARY_DIR}/generated.cpp
)
