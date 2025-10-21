add_library(secp256k1 STATIC secp256k1.cpp)

target_link_libraries(secp256k1 PRIVATE cryptoutil)
target_include_directories(secp256k1 PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
