cmake_minimum_required(VERSION 3.12)
project(BitCrack LANGUAGES CXX)

if(BUILD_CUDA)
    enable_language(CUDA)
endif()

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_CUDA_STANDARD 17)
set(CMAKE_CUDA_STANDARD_REQUIRED ON)

option(BUILD_CUDA "Build with CUDA support" ON)
option(BUILD_OPENCL "Build with OpenCL support" ON)

if(BUILD_CUDA)
    find_package(CUDA)
endif()

if(BUILD_OPENCL)
    find_package(OpenCL)
endif()

add_subdirectory(util)
add_subdirectory(CryptoUtil)
add_subdirectory(secp256k1lib)
add_subdirectory(AddressUtil)
add_subdirectory(CmdParse)
add_subdirectory(Logger)
add_subdirectory(KeyFinderLib)

if(CUDA_FOUND AND BUILD_CUDA)
    add_subdirectory(cudaUtil)
    add_subdirectory(CudaKeySearchDevice)
endif()

if(OpenCL_FOUND AND BUILD_OPENCL)
    add_subdirectory(clUtil)
    add_subdirectory(CLKeySearchDevice)
endif()

add_subdirectory(KeyFinder)
