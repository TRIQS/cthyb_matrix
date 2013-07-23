triqs_add_rpath_for_cxx_code() # necessary for python module to load the C++ so file
FILE(GLOB cpp_files RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} *.cpp)
add_library(ctqmc_hyb_matrix_c ${cpp_files})
target_link_libraries (ctqmc_hyb_matrix_c ${TRIQS_LIBRARY_ALL})
include_directories(${TRIQS_INCLUDE_ALL})

install(TARGETS ctqmc_hyb_matrix_c DESTINATION lib)


