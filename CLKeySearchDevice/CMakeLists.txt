
add_executable(embedcl ../embedcl/main.cpp)

add_custom_command(
    OUTPUT bitcrack.cl
    COMMAND cat ../clMath/sha256.cl ../clMath/secp256k1.cl ../clMath/ripemd160.cl keysearch.cl > bitcrack.cl
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    DEPENDS keysearch.cl ../clMath/sha256.cl ../clMath/secp256k1.cl ../clMath/ripemd160.cl
    COMMENT "Concatenating OpenCL kernels"
)

add_custom_command(
    OUTPUT bitcrack_cl.cpp
    COMMAND embedcl bitcrack.cl bitcrack_cl.cpp _bitcrack_cl
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    DEPENDS embedcl bitcrack.cl
    COMMENT "Embedding OpenCL kernel"
)

add_library(clkeysearchdevice STATIC CLKeySearchDevice.cpp ${CMAKE_CURRENT_BINARY_DIR}/bitcrack_cl.cpp)
target_link_libraries(clkeysearchdevice PRIVATE keyfinderlib clutil)
target_include_directories(clkeysearchdevice PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ../KeyFinderLib ../clUtil)
