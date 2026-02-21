cmake_minimum_required(VERSION 3.26.0)
project(proj_ray1 VERSION 1.0.0)
#cmake_policy(SET CMP0072 NEW)

# place for finding Findglfw3.cmake
#set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

# we are going to use smart pointers
set(CMAKE_CXX_STANDARD 17)


#if(NOT CMAKE_BUILD_TYPE)
#  set(CMAKE_BUILD_TYPE Release)
#endif()

#set(CMAKE_CXX_FLAGS "-Wall")
#set(CMAKE_CXX_FLAGS_DEBUG "-g")
#set(CMAKE_CXX_FLAGS_RELEASE "-O2")


# specify the executable name and 
# add source files to our exectuable programs
add_executable(ray01 src/main.cpp)

# specify include directories
target_include_directories(ray01 PRIVATE include)

# copy the images folder 
add_custom_command(
        TARGET ray01 POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_directory
		"${CMAKE_CURRENT_SOURCE_DIR}/images"
                $<TARGET_FILE_DIR:run01>/models         
        )

