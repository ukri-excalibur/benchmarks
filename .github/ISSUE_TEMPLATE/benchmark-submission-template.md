---
name: Benchmark submission template
about: Use this template to request a new benchmark to be included in the ExCALIBUR
  benchmark repo.
title: "[BENCHMARK]"
labels: ''
assignees: ''

---

# Benchmark application name

- [ ] Add here a short description of your proxy app. This summary will be used in the official, public-facing ExCALIBUR benchmark list when the benchmark is accepted.

- [ ] Add below a link to the public source code repository (e.g. on GitHub) containing the proxy app source code. This should point to a stable release git tag or commit that points to a stable release.

## Quality criteria review
The reviewer(s) will tick off the following criteria after they check that they are satisfied. Please add any review comments and discussion in subsequent comments in the issue, and not in this list.

### Required

#### Build Systems
- [ ] The build system exposes common flags and variables (e.g. CXX, CXXFLAGS, CC, CFLAGS, FC, FLAGS, LDFLAGS) for easy testing.
- [ ] The proxy app can be built on a standard Linux distribution without need for modification of the standard FHS (Filesystem Hierarchy Standard).
- [ ] The proxy app can be built and adjusted without deep changes to the build system (e.g. commenting and uncommenting lines in the makefile).
- [ ] Mechanism exists (e.g. searching PATH, LIBNAME_DIR) to allow for passing of any library dependencies to the build system.

- [ ] Building the app according to the instructions works and is reasonably easy.

#### Expected Running Modes
- [ ] A quick test exists to verify correct compilation and, if applicable, track kernel performance.
  - [ ] The test runs in a reasonably short time (order of seconds if possible) and passes/produces sensible results.

#### Documentation
- [ ] A general description of what the proxy is and which algorithms it comprises/computational science
motifs it represents.
- [ ] Documentation of the general scope of the proxy app and where it does/doesn’t represent
the parent application correctly.
- [ ] Documented analysis of how the app proxy represents the parent application.
- [ ] Documentation mentions what aspect of the parent application the proxy is a proxy for (e.g. computation, memory, communication, I/O).
- [ ] Documentation covers the build process (including dependencies) and how to test the final executable.
- [ ] Documentation covers all configuration options and command-line parameters a user is expected to use. It also explains why the user might use each option, not just what each option enables.
- [ ] The running mode documentation includes input decks as well as expected outputs for each of the input decks.

#### Verification of Correctness
- [ ] An automatable regression test exists, that checks the final output against a known good reference.
  - [ ] The test runs and passes.

#### Reported Performance metrics/models
- [ ] The proxy app includes a figure of merit (FOM) that can be used to compare performance under different conditions.

### Recommended

#### Build Systems
- [ ] Proxy is distributed via a packaging tool, eg. Spack.
  - [ ] Installation of the package is sensible and easy

#### Design
- [ ] Code doesn't contain obvious useless repetitions and code common or beneficial to multiple applications is factored out into library dependencies.
- [ ] The number of lines of code is kept to a minimum (ideally fewer than 10k lines of code).

#### Expected Running Modes
- [ ] A running mode (weak and strong scaling) exists, representing a current workload.
- [ ] A running mode (weak and strong scaling) exists, representing an exascale workload.

#### Documentation
- [ ] Documented aspects of the proxy app that may look simple enough that some quick optimizations
can be applied but should not be applied because they will not be feasible in the parent application.
- [ ] The documentation discusses minimum/maximum reasonable problem sizes to prevent users running at extreme scaling points or running unrealistic cases.

####  Verification of Correctness
- [ ] Regression test exists that compares final output against a reference within an acceptable threshold
based upon the science being simulated.
  - [ ] Test runs and passes.

#### Reported Performance metrics/models
- [ ] There exist one or more timers around the most important code regions and an option to output the execution time of those regions.
- [ ] There exists a performance model based on the resource the proxy app is stressing.
