
if(TARGET cudakeysearchdevice)
    add_executable(cuKeyFinder main.cpp)
    target_link_libraries(cuKeyFinder PRIVATE cudakeysearchdevice)
endif()

if(TARGET clkeysearchdevice)
    add_executable(clKeyFinder main.cpp)
    target_link_libraries(clKeyFinder PRIVATE clkeysearchdevice)
endif()
