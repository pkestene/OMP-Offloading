# Introduction

# List of Projects

* 00_build_OpenMP_offload

  Documentation and scripts for building GCC as well as Clang/LLVM with OpenMP
  support for Nvidia GPU offloading.

* 01_accelQuery

  `accelQuery` searches accelerator(s) on a heterogeneous computer.
  Accelerator(s), if found, will be enumerated with some basic info.

  The directory tree:

  - src: source code
  - docs: documentation
  - tests: some tests

* 02_dataTransRate

  `dataTransRate` gives the data transfer rate (in MB/sec) from `src` to `dst`.

  The possible situations are:

  * h2h: `src` = host  and `dst` = host
  * h2a: `src` = host  and `dst` = accel
  * a2a: `src` = accel and `dst` = accel

  The directory tree:

  - src: source code
  - docs: documentation
  - tests: some tests

* 03_taskwait

  `taskwait` checks the `taskwait` construct for the deferred target task.
  At the time of writing, this hasn't been implemented in the GCC 9.2 compiler.

  The directory tree:

  - src: source code
  - docs: documentation
  - tests: some tests

* 04_scalarAddition

  `scalarAddition` adds two integers on host and accelerator, and also compares
  the performance.

  The directory tree:

  - src: source code
  - docs: documentation
  - tests: some tests

* 05_saxpy_v1

  `saxpy` performs the `axpy` operation on host as well as accelerator and then
  compares the FLOPS performance.

  The `axpy` operation is defined as:

  $$ y := a * x + y $$

  where:

  - `a` is a scalar.
  - `x` and `y` are vectors each with n elements.

  The initial value of `a` and elements of `x[]` and `y[]` are specially
  designed, so that the floating-point calculations on host and accelerator
  can be compared _exactly_.

  Please note that only _one GPU thread_ is used for the `axpy` calculation on
  accelerator in this version. This can be verified by uncomment the `CFLAGS`
  line in `configure.ac`.

  The directory tree:

  - src: source code
  - docs: documentation
  - tests: some tests

