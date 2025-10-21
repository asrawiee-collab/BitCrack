add_library(keyfinderlib STATIC KeyFinder.cpp)

target_link_libraries(keyfinderlib PRIVATE secp256k1 logger cmdparse addressutil)
target_include_directories(keyfinderlib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ../secp256k1lib ../Logger ../CmdParse ../AddressUtil)
