# X86_64

This folder contains the shared library and the Docker image that can be used by users and application developers to
benefit from the acceleration offered by x86_64 CPUs.

## Artifacts

The OAX runtime is available as a shared library that can be used by developers to load and run optimized models on
x86_64.
It's available at [libRuntimeLibrary.so](artifacts%2FlibRuntimeLibrary.so).

The OAX conversion toolchain is available as a Docker image that can be used to convert non-optimized models to
optimized models. Due to its significant size, the Docker image is available for
download [here](https://download.sclbl.net/OAX/toolchains/conversion-toolchain-latest.tar).