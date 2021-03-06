# Version number of the application
set (CTHYB_MATRIX_VERSION "1.0")
set (CTHYB_MATRIX_RELEASE "1.0.0")

# Append triqs installed files to the cmake load path
list(APPEND CMAKE_MODULE_PATH ${TRIQS_PATH}/share/triqs/cmake)

# start configuration 
cmake_minimum_required(VERSION 2.8)
project(cthyb_matrix CXX)
set(CMAKE_BUILD_TYPE Release)
enable_testing()

# We use shared libraries
option(BUILD_SHARED_LIBS "Build shared libraries" ON)

# Load TRIQS, including all predefined variables from TRIQS installation
find_package(TRIQS REQUIRED)

# Check that versions are compatible
if(NOT CTHYB_MATRIX_VERSION EQUAL TRIQS_VERSION)
  message(FATAL_ERROR "The application version is not compatible with the TRIQS library (TRIQS library version: ${TRIQS_VERSION} while this application version: ${CTHYB_MATRIX_VERSION})")
endif()

# We want to be installed in the TRIQS tree
set(CMAKE_INSTALL_PREFIX ${TRIQS_PATH})

# Compile C++ code
add_subdirectory(c++)

# Python interface
if (${TRIQS_WITH_PYTHON_SUPPORT})
 add_subdirectory(python)
 add_subdirectory(test)
 option(BUILD_DOC "Build documentation" OFF)
 if(${BUILD_DOC})
   if(NOT TRIQS_WITH_DOCUMENTATION)
     message("Error: TRIQS library has not been compiled with its documentation")
   endif()
   add_subdirectory(doc)
 endif(${BUILD_DOC})
endif()
