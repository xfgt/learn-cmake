add_library(LibMyCustom1
    sayHello.cpp
    sayHello.h
)

target_include_directories( LibMyCustom1 PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}")