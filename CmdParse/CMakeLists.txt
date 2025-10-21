add_library(cmdparse STATIC CmdParse.cpp)

target_include_directories(cmdparse PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
