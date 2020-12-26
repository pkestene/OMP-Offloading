add_executable(scalarAddition "")

target_sources(scalarAddition
  PRIVATE
  scalarAddition.c
  check1ns.c)

target_link_libraries(scalarAddition
  PRIVATE
  CUDA::cudart)
