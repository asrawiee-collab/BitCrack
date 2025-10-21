add_library(cudautil STATIC cudaUtil.cpp)

target_link_libraries(cudautil PRIVATE CUDA::cudart)
target_include_directories(cudautil PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
