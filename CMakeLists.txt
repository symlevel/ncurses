cmake_minimum_required(VERSION 3.0)
project(ncurses)

add_subdirectory(ncurses)
add_subdirectory(panel)

# Install rules for headers
file(GLOB_RECURSE headers RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}/include" "${CMAKE_CURRENT_SOURCE_DIR}/include/*.h")
foreach(header ${headers})
    get_filename_component(subdir "${header}" DIRECTORY)
    install(FILES "${CMAKE_CURRENT_SOURCE_DIR}/include/${header}" DESTINATION "include/ncurses/${subdir}")
endforeach()

# Install rules for pre generated headers
file(GLOB_RECURSE headers RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}/gen/include" "${CMAKE_CURRENT_SOURCE_DIR}/gen/include/*.h")
foreach(header ${headers})
    get_filename_component(subdir "${header}" DIRECTORY)
    install(FILES "${CMAKE_CURRENT_SOURCE_DIR}/gen/include/${header}" DESTINATION "include/ncurses/${subdir}")
endforeach()
