print_running_filename(${CMAKE_CURRENT_LIST_FILE})
set(TARGET uECC)
# Specify the minimum version of CMake required
cmake_minimum_required(VERSION 3.0)
# Add the source files for the library
set(SOURCES
    uECC.c
)
# Add the library target and link the sources
add_library(${TARGET} ${SOURCES})

if(MICRO_ECC_EMB)
target_link_libraries(uECC PUBLIC MemoryUtilities)
endif()

# Add the include directory
target_include_directories(${TARGET} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
# Install the library
install(TARGETS ${TARGET} DESTINATION ${INSTALL_LIBRARY_DESTINATION})
