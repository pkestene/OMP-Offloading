add_executable(taskwait "")

target_sources(taskwait
  PRIVATE
  taskwait.c)

target_link_libraries(taskwait
  PRIVATE
  CUDA::cudart)
