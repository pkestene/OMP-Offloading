# cmake 3.17 required to use find_package(CUDAToolkit)
cmake_minimum_required(VERSION 3.17)

project(01-accelQuery)

if(PROJECT_SOURCE_DIR STREQUAL PROJECT_BINARY_DIR)
  message(
    FATAL_ERROR
      "In-source builds not allowed. Please make a new directory (called a build directory) and run CMake from there."
  )
endif()

#
# default local cmake macro repository (FindMKL)
#
list(APPEND CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake)


# set C++14 standard as default
set(CMAKE_CXX_STANDARD 14 CACHE STRING "C++ standard to conform to")
set(CMAKE_CXX_STANDARD_REQUIRED YES)

# CUDA config, setup for cudart
find_package(CUDAToolkit)

# MKL config
find_package(MKL)

# default compiler flags
if(CMAKE_C_COMPILER_ID MATCHES "Clang")
  add_compile_options(-fopenmp -fopenmp-targets=nvptx64-nvidia-cuda -Xopenmp-target -march=sm_75)
  add_link_options(-fopenmp -fopenmp-targets=nvptx64-nvidia-cuda)
elseif(CMAKE_C_COMPILER_ID MATCHES "GNU")
  add_compile_options(-fopenmp -foffload=nvptx-none)
  add_link_options(-fopenmp -foffload=nvptx-none)
endif()

add_subdirectory(src)
add_subdirectory(docs)

##################### PRINT CONFIGURE STATUS ######################
message("//===================================================")
message("// ${PROJECT_NAME} build configuration:")
message("//")
message("// Compiler               : ${CMAKE_C_COMPILER}")
message("// CUDA toolkit   version : ${CUDAToolkit_VERSION}")
message("// CUDA toolkit   inc     : ${CUDAToolkit_INCLUDE_DIRS}")
message("// CUDA toolkit   lib     : ${CUDAToolkit_LIBRARY_DIR}")
message("// MKL found ?            : ${MKL_FOUND}")
message("//===================================================")
