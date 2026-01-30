file(GLOB_RECURSE files "*.c")

add_library(Fusion ${files})
target_include_directories(Fusion PUBLIC $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}> $<INSTALL_INTERFACE:include> )
set_target_properties(Fusion PROPERTIES PUBLIC_HEADER ${CMAKE_CURRENT_SOURCE_DIR}/Fusion.h)

#target_include_directories(Fusion PUBLIC .)

if(UNIX AND NOT APPLE)
    target_link_libraries(Fusion m) # link math library for Linux
endif()
