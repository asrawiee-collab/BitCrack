add_library(cryptoutil STATIC Rng.cpp checksum.cpp hash.cpp ripemd160.cpp sha256.cpp)

target_link_libraries(cryptoutil PRIVATE util)
target_include_directories(cryptoutil PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
