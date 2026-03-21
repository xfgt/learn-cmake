# This is how you make comments
# This is the root CMakeLists.txt
# there can be others CMakeLists for each subdirectory if that's necessary;


cmake_minimum_required(VERSION 3.23)

project (MyProjectName) 

set(CMAKE_CXX_STANDARD 11) # set the c++ version 

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

#add_subdirectory("LibraryDir/") # add a subdir which has another CMakeLists.txt file with instructions. (for example a folder of a library)



