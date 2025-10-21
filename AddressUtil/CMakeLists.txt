add_library(addressutil STATIC Base58.cpp hash.cpp)

target_include_directories(addressutil PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ../CryptoUtil ../secp256k1lib)
