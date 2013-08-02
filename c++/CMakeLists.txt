
FILE(GLOB cpp_sources RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} *.cpp)
add_library(cthyb_matrix_c ${cpp_sources})
target_link_libraries(cthyb_matrix_c ${TRIQS_LIBRARY_ALL})
include_directories(${TRIQS_INCLUDE_ALL})
triqs_set_rpath_for_target(cthyb_matrix_c)

install(TARGETS cthyb_matrix_c DESTINATION lib)

