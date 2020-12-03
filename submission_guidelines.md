# Proxy App Quality Standards and Best Practices

This page describes the quality standards and best practices for ExCALIBUR mini-benchmarks and proxy apps.
Standards and practices in this guide are designated as either required or recommended.
In order for a proxy app to be accepted in the official ExCALIBUR set, it has to satisfy the required items.

## Code Distribution and Availability

**Required**: A public source code repository (e.g. on GitHub) is the only acceptable mechanism to distribute source code
as it also provides an easy way of funneling changes from the proxy team or vendors back to the upstream developers.
Distributing code as a web link to a tarball, private git/svn repositories or email/forms to request source code are not acceptable.

**Required**: Provide a stable release git tag or commit that points to a stable release.

**Recommended**: Use a packaging tool to distribute your proxy, to ease installation for the users.
Eg. Create a spackage to distribute through Spack.

**Recommended**: Proxy apps should be self-contained. Proxy apps with large or complex library dependencies
will be difficult or impossible to run on minimal testbed or simulator platforms typically used by vendors
during early design phases. If dependencies are necessary, creation of eg. a spackage to distribute the proxy
along with the required dependencies will greatly assist potential proxy users.

## Build Systems

**Required**: The build system should expose common flags and variables (e.g. CXX, CXXFLAGS, CC, CFLAGS, FC, FLAGS, LDFLAGS)
for easy testing.

**Required**: The proxy app should be able to be built on a standard Linux distribution without need for
modification of the standard FHS (Filesystem Hierarchy Standard).

**Required**: The proxy app should be able to be built and adjusted without deep changes to the build system
(e.g. commenting and uncommenting lines in the makefile is fragile to automate).

**Required:** Provide mechanism (e.g. searching PATH, LIBNAME_DIR) to allow for passing of any library dependencies
to the build system.

**Recommended**: Easy integration with packaging tools (eg. Spack).
This should be handled through the above requirements.

## Design

**Recommended**: Follow DRY (Don’t Repeat Yourself) practices and refactor code common or beneficial
to multiple applications into library dependencies.

**Recommended**: Keep the number of lines of code to a minimum without negating the intended purpose of the proxy application.
A larger codebase may allow for further exploration of the design space but adds to the difficulty of working with the proxy.
A suggested goal is to have an proxy application with fewer than 10k lines of code.

## Expected Running Modes to be specified

**Required**: A quick test to verify correct compilation and, if applicable, track kernel performance.
This should have an execution time on the order of seconds but can be larger if necessary.
See Verification of Correctness below.

**Recommended**: A running mode (weak and strong scaling) representing a current workload.

**Recommended**: A running mode (weak and strong scaling) representing an exascale workload.

## Documentation

### General Description

**Required**: A general description of what the proxy is and which algorithms it comprises/computational science
motifs it represents.

**Required**: Documentation of the general scope of the proxy app and where it does/doesn’t represent
the parent application correctly.

### Intent and Limitations of Proxy Application with Respect to Parent

**Required**: Documented analysis of how the app proxy represents the parent application.

**Required**: Documentation should mention what aspect of the parent application the proxy is a proxy for
(e.g. computation, memory, communication, I/O).

**Recommended**: Documented aspects of the proxy app that may look simple enough that some quick optimizations
can be applied but should not be applied because they will not be feasible in the parent application.

### Building and running/testing

**Required**: Documentation should cover the build process (including dependencies) and how to test the final executable.
See Verification of Correctness below.

**Required**: Documentation should cover all configuration options and command-line parameters a user is expected to use.

**Required**: Documentation should explain why the user might use each option, not just what each option enables.

### Running mode documentation

**Required**: The running mode documentation should include input decks as well as expected outputs
for each of the input decks. See Verification of Correctness below.

**Recommended**: The documentation should discuss minimum/maximum reasonable problem sizes to prevent users running
at extreme scaling points or running unrealistic cases.

## Verification of Correctness

**Required**: Inclusion of an automatable regression test that checks the final output against a known good reference.

**Recommended**: Regression test that compares final output against a reference within an acceptable threshold
based upon the science being simulated.

**Recommended**: Tests should cover most code paths provided by the proxy app.

## Reported Performance metrics/models

**Required**: The proxy app should include a figure of merit (FOM) that can be used to compare performance
under different conditions. This could be based on the science being simulated or what the proxy app is stressing
(e.g., computational power, memory etc.). The FOM should be representative of the performance of the parent application.

**Recommended**: If applicable, include one or more timers around the most important code regions and an option
to output the execution time of those regions.

**Recommended**: If applicable, include a performance model based on the resource the proxy app is stressing.
