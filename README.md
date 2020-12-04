# benchmarks
Repository for information on benchmarks contributed as part of the ExCALIBUR programme

## BabelStream

BabelStream is a benchmark used to measure the memory transfer rates to/from capacity memory. Unlike other memory bandwidth benchmarks this does not include any PCIe transfer time for attached devices. This benchmark is similar in spirit, and based on, the STREAM benchmark for CPUs.

The choice of one programming model over another should ideally not limit the performance that can be achieved on a device. As such there are multiple implementations in a variety of programming models. Currently implemented are:

* OpenCL
* CUDA
* OpenACC
* OpenMP 3 and 4.5
* Kokkos
* RAJA
* SYCL

As such this tool can be used as a kind of Rosetta Stone which provides both a cross-platform and cross-programming model array of results of achievable memory bandwidth.

* [Web site](https://uob-hpc.github.io/BabelStream/)
* [Code download](https://github.com/UoB-HPC/BabelStream/releases/tag/v3.4)
* [Build instructions](https://github.com/UoB-HPC/BabelStream#usage)
* [Run instructions](https://uob-hpc.github.io/BabelStream/)

