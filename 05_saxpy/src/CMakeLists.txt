add_executable(saxpy "")

target_sources(saxpy
  PRIVATE
  saxpy.c
  check1ns.c
  hsaxpy.c
  asaxpy.c
  wtcalc.c)

target_link_libraries(saxpy
  PRIVATE
  CUDA::cudart
  CUDA::cublas
  mkl::mkl_intel_64bit_seq_dyn)
