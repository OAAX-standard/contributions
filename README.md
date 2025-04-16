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
it to load and run the optimized model on that machine running the application.
> **Note**: We provide a set of off-the-shelf examples in C and Python that demonstrate how to use the runtime to load
> and run an optimized model in the [examples](https://github.com/oaax-standard/examples) repository.


| AI Accelerator        | Target Architecture | Runtime file                                                                                                                                                                                                                                                                                                                                                     | Conversion toolchain                                                                               |                             |
|-----------------------|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|-----------------------------|
| CPU                   | x86_64              | [Runtime](https://artifactory.nxvms.dev/artifactory/nxai_open/OAAX/runtimes/async/cpu-x86_64-ort.tar.gz)                                                                                                                                                                                                                                                         | [Docker image](https://drive.google.com/file/d/1Xz9m1ATwmM9w81bDuZ1ibNqcyLmOKFWW/view?usp=sharing) | [README](CPU/README.md)     |
| CPU                   | aarch64             | [Runtime](https://artifactory.nxvms.dev/artifactory/nxai_open/OAAX/runtimes/async/cpu-aarch64-ort.tar.gz)                                                                                                                                                                                                                                                        | [Docker image](https://drive.google.com/file/d/1Xz9m1ATwmM9w81bDuZ1ibNqcyLmOKFWW/view?usp=sharing) | [README](CPU/README.md)     |
| Intel (OpenVINO 2025) | x86_64              | [Runtime](https://artifactory.nxvms.dev/artifactory/nxai_open/OAAX/runtimes/async/cpu-1.21-x86_64-openvino.tar.gzcpu-2024-x86_64-openvino.tar.gz)                                                                                                                                                                                                                | [Docker image](https://drive.google.com/file/d/1Xz9m1ATwmM9w81bDuZ1ibNqcyLmOKFWW/view?usp=sharing) | [README](Intel/README.md)   |
| Hailo-8 (v4.20.0)     | x86_64              | [Runtime](https://artifactory.nxvms.dev/artifactory/nxai_open/OAAX/runtimes/async/hailo8-4.20.0-x86_64-ort.tar.gz)                                                                                                                                                                                                                                               | [Docker image](https://drive.google.com/file/d/1iL2UvjRpeAJmRpoudNc1sNbCe2VNixYl/view?usp=sharing) | [README](Hailo-8/README.md) |
| Hailo-8 (v4.20.0)     | aarch64             | [Runtime](https://artifactory.nxvms.dev/artifactory/nxai_open/OAAX/runtimes/async/hailo8-4.20.0-aarch64-ort.tar.gz)                                                                                                                                                                                                                                              | [Docker image](https://drive.google.com/file/d/1iL2UvjRpeAJmRpoudNc1sNbCe2VNixYl/view?usp=sharing) | [README](Hailo-8/README.md) |
| Nvidia                | x86_64              | [CUDA 11](https://artifactory.nxvms.dev/artifactory/nxai_open/OAAX/runtimes/async/nvidia-cuda_11-x86_64-ort.tar.gz), [CUDA 12](https://artifactory.nxvms.dev/artifactory/nxai_open/OAAX/runtimes/async/nvidia-cuda_12-x86_64-ort.tar.gz)                                                                                                                         | [Docker image](https://drive.google.com/file/d/1Xz9m1ATwmM9w81bDuZ1ibNqcyLmOKFWW/view?usp=sharing) | [README](Nvidia/README.md)  |
| Nvidia                | aarch64             | [CUDA 10](https://artifactory.nxvms.dev/artifactory/nxai_open/OAAX/runtimes/async/nvidia-cuda_10-aarch64-ort.tar.gz), [CUDA 11](https://artifactory.nxvms.dev/artifactory/nxai_open/OAAX/runtimes/async/nvidia-cuda_11-aarch64-ort.tar.gz), [CUDA 12](https://artifactory.nxvms.dev/artifactory/nxai_open/OAAX/runtimes/async/nvidia-cuda_12-aarch64-ort.tar.gz) | [Docker image](https://drive.google.com/file/d/1Xz9m1ATwmM9w81bDuZ1ibNqcyLmOKFWW/view?usp=sharing) | [README](Nvidia/README.md)  |
| Qualcomm (QCS6490)    | aarch64             | Coming soon                                                                                                                                                                                                                                                                                                                                                      | Coming soon                                                                                        | Coming soon                 |
