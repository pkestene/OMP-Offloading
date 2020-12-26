add_executable(accelQuery "")

target_sources(accelQuery
  PRIVATE
  accelQuery.c
  prtAccelInfo.c)

target_link_libraries(accelQuery
  PRIVATE
  CUDA::cudart)
