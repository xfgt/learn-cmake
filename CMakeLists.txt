# This is how you make comments
# This is the root CMakeLists.txt
# there can be others CMakeLists for each subdirectory if that's necessary;


cmake_minimum_required(VERSION 3.23) # start

project (MyProjectName) 

# set the c++ version
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)


#add_subdirectory("LibraryDir/") # add a subdir which has another CMakeLists.txt file with instructions. (for example a folder of a library)


add_executable(MyProgram)
add_executable(MyProgram2)

target_sources(MyProgram
	PRIVATE
	"Start-1/main.cpp"
	"Start-1/printMessage.cpp"
)

target_sources(MyProgram2
	PRIVATE
	"Primer-2/main.cpp"
	"Primer-2/function1.cpp"
)

# Simpler version
#add_executable(MyProgram "Start-1/main.cpp" "Start-1/printMessage.cpp")
#add_executable(MyProgram2 "Primer-2/main.cpp" "Primer-2/function1.cpp")


# Primer-3-Library
# Add an executable as usual and include the entry point path.
add_executable(Primer-3)
target_sources(Primer-3
	PRIVATE
	"Primer-3-Library/main.cpp"
)

# Make a Library object and link the sources
# https://youtu.be/abuCXC3t6eQ?list=PLK6MXr8gasrGmIiSuVQXpfFuE1uPT615s&t=235
add_library(MyLibrary1
	"Primer-3-Library/headers/displayMessage.hpp"
	"Primer-3-Library/displayMessage.cpp"
)

# Add a second library

add_library(MyLibrary2

	"Primer-3-Library/headers/getCPPVersion.hpp"
	"Primer-3-Library/getCPPVersion.cpp"
)

# Link the Libraries(MyLibrary1), (MyLibrary2) to the Executable (Primer-3)
target_link_libraries(Primer-3 PRIVATE MyLibrary1 MyLibrary2)


add_subdirectory(cmake101)


# Apply this to ALL targets so the __cplusplus macro is correct everywhere
if(MSVC)
    target_compile_options(Primer-3 PRIVATE "/Zc:__cplusplus")
    target_compile_options(MyLibrary1 PRIVATE "/Zc:__cplusplus")
    target_compile_options(MyLibrary2 PRIVATE "/Zc:__cplusplus")
endif()


# Last track: https://youtu.be/SYgESCQeGJY?si=nxHxVm1aRIhHSdll

