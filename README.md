
This is the repository containing information on benchmarks contributed as part of the ExCALIBUR programme.

# Instructions for submitting benchmarks

To submit a benchmark application for inclusion in the ExCALIBUR benchmark suite, first read the [guidelines](./submission_guidelines.md).

Once you are confident your app fulfills the requirements, open a new issue in this repository, and follow the instructions in the issue template. A reviewer will be assigned for your request and will add feedback on the issue. Once you have addressed all the reviewer's comments, your app will be added to the repository.

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

