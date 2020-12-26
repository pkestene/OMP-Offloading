add_executable(dataTransRate "")

target_sources(dataTransRate
  PRIVATE
  dataTransRate.c
  check1ns.c)

target_link_libraries(dataTransRate
  PRIVATE
  CUDA::cudart)
