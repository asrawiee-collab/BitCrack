add_library(clutil STATIC clContext.cpp clUtil.cpp clerrors.cpp)

target_link_libraries(clutil PRIVATE OpenCL::OpenCL)
target_include_directories(clutil PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
