cmake_minimum_required (VERSION 2.8)  # 필수 정보

project (IDD)  # 필수 정보

include_directories( src src/Invn  
			src/Invn/Devices src/Invn/Drivers/Icm20948
			src/Invn/DynamicProtocol 
			src/Invn/Images 
			src/Invn/VSensor  
			src/Invn/EmbUtils )

file(GLOB SOURCES src/Invn/EmbUtils/*.c 
		src/Invn/VSensor/*.c 
		src/Invn/Devices/Drivers/Icm20948/*.c 
		src/Invn/Devices/*.c 
		src/Invn/VSensor/*.c 
		src/Invn/EmbUtils/*.c 
		src/Invn/DynamicProtocol/*.c )

add_compile_options( -Wall )
add_definitions( -DLINUX -DDEBUG )

set(CMAKE_C_FLAGS_RELEASE "-O2")

#add_library (libIDD SHARED "${ROJECT_SOURCE_DIR}/src")  
add_library (IDD SHARED ${SOURCES})  

install(TARGETS IDD LIBRARY DESTINATION  ${PROJECT_SOURCE_DIR}/lib 
	            RUNTIME DESTINATION  ${PROJECT_SOURCE_DIR}/bin )

