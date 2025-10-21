
set(CUDA_SOURCES
    CudaKeySearchDevice.cu
    cudabridge.cu
)

add_library(cudakeysearchdevice STATIC CudaKeySearchDevice.cpp ${CUDA_SOURCES})
target_link_libraries(cudakeysearchdevice PRIVATE keyfinderlib cudautil CUDA::cudart)
target_include_directories(cudakeysearchdevice PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ../KeyFinderLib ../cudaUtil)

# Set the CUDA architecture flags.
# This is just an example, a more robust implementation would detect the available architectures.
set_target_properties(cudakeysearchdevice PROPERTIES
    CUDA_ARCHITECTURES "60;61;62;70;72;75;80;86"
)
