file(GLOB_RECURSE files "*.c")

get_filename_component(FUSION_INCLUDE_DIR "${CMAKE_CURRENT_SOURCE_DIR}" REALPATH)

add_library(Fusion ${files})
target_include_directories(Fusion PUBLIC $<BUILD_INTERFACE:${FUSION_INCLUDE_DIR}> $<INSTALL_INTERFACE:include>)
set_target_properties(Fusion PROPERTIES PUBLIC_HEADER ${CMAKE_CURRENT_SOURCE_DIR}/Fusion.h)

#target_include_directories(Fusion PUBLIC .)

if(UNIX AND NOT APPLE)
    target_link_libraries(Fusion PUBLIC m) # propagate libm to static library consumers
endif()
