# Contributions

This repository contains OAAX artifacts contributed by the community.
The contributions are organized into folders, each of which contains a README file that describes the contribution and
how to use it, as each AI accelerator has its own specific requirements for the model it can run, configuration of the
conversion toolchain, and the runtime, etc.

## Overview

The table below serves as an overview of the contributions available in this repository.

These contributions are meant to be downloaded and used directly by developers on any compatible machine.  
For example, a Hailo-8 OAAX runtime can only be used on an x86_64 machine, with a Hailo-8 AI accelerator attached.
However, the conversion toolchain can be used on any machine that has Docker installed.

In principle, an OAAX user would first convert a model using the conversion toolchain on any machine with Docker
installed, and then copy the generated optimized model from that machine to the target machine.   
On the target machine, the user would also download the runtime from this repository to the target machine, and then use
it to
load and run the optimized model on that machine using his/her application.
> **Note**: We provide a set of off-the-shelf examples in C and Python that demonstrate how to use the runtime to load
> and run an optimized model in the [examples](https://github.com/oaax-standard/examples) repository.

| AI Accelerator    | Target Architecture | Runtime file                                                                                                               | Conversion toolchain                                                                       | Documentation                      |
|-------------------|---------------------|----------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|------------------------------------|
| CPU     | x86_64              | [Artifacts](CPU/artifacts-x86_64)                                                                                      | [Docker image](https://download.sclbl.net/OAAX/toolchains/conversion-toolchain-latest.tar) | [README](CPU/README.md) |
| CPU     | arm64              | [Artifacts](CPU/artifacts-aarch64)                                                                                      | [Docker image](https://download.sclbl.net/OAAX/toolchains/conversion-toolchain-latest.tar) | [README](CPU/README.md) |
| Hailo-8 (v4.16.0) | x86_64              | [Artifacts](Hailo-8/artifacts-16)                                                                                           | [Docker image](https://download.sclbl.net/OAAX/toolchains/onnx-to-hailo-latest.tar)        | [README](Hailo-8/README.md)        |
| Hailo-8 (v4.17.0) | x86_64              | [Artifacts](Hailo-8/artifacts-17)                                                                                           | [Docker image](https://download.sclbl.net/OAAX/toolchains/onnx-to-hailo-latest.tar)        | [README](Hailo-8/README.md)        |
| Nvidia            | x86_64              | [CUDA 11](https://download.sclbl.net/OAAX/runtimes/CUDA-11/), [CUDA 12](https://download.sclbl.net/OAAX/runtimes/CUDA-12/) | [Docker image](https://download.sclbl.net/OAAX/toolchains/conversion-toolchain-latest.tar) | [README](Nvidia-X86_64/README.md)  |