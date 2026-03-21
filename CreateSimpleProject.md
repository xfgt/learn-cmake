1.	Create CMakeLists.txt
2.	Insert the four command-functions:



cmake_minimum_required(VERSION 3.23)

project (MyProjectName)

add_executable(MyProgram) // start exe 1
add_executable(MyProgram2) // start exe 2 (different exercise for example)


target_sources(MyProgram	// exe 1
	PRIVATE
	"Folder1/main.cpp"
	"Folder1/function.cpp"
)


target_sources(MyProgram2	// exe 2
	PRIVATE
	"Folder2/main.cpp"
	"Folder2/fucntion.cpp"
)



// and at the end just choose which exe you want to run
// save the cmake lists file and if no errors you are good to go! :D


cmake -B build
cmake --build build
