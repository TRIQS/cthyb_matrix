triqs_make_target_to_copy_all_py_files_from_python_dir_to_build_dir()

# Build the cython module
triqs_add_rpath_for_cxx_code() # necessary for python module to load the C++ so file
triqs_cython_module(ctqmc_hyb_matrix ctqmc_hyb_matrix applications/impurity_solvers/ctqmc_hyb_matrix)
target_link_libraries(ctqmc_hyb_matrix ctqmc_hyb_matrix_c)
include_directories( ${TRIQS_INCLUDE_ALL} ${CMAKE_CURRENT_SOURCE_DIR}/../ )

# to be able to run from toplevel
execute_process(COMMAND ln -fs ${CMAKE_CURRENT_BINARY_DIR}/ctqmc_hyb_matrix.so ${CMAKE_BINARY_DIR})

# Install 
SET(PYTHON_SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/__init__.py ${CMAKE_CURRENT_SOURCE_DIR}/old_solver.py ${CMAKE_CURRENT_SOURCE_DIR}/models.py )
install (FILES ${PYTHON_SOURCES} DESTINATION ${TRIQS_PYTHON_LIB_DEST}/applications/impurity_solvers/ctqmc_hyb_matrix)

#make sure that the __init__.py empty files are present ...
file (WRITE __init__.py.all_empty  "__all__=[]")
install (FILES __init__.py.all_empty DESTINATION ${TRIQS_PYTHON_LIB_DEST}/applications/impurity_solvers/ RENAME __init__.py)
install (FILES __init__.py.all_empty DESTINATION ${TRIQS_PYTHON_LIB_DEST}/applications/                  RENAME __init__.py)


