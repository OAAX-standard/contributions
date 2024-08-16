# MemryX Accelerator

This folder contains the shared library and the Docker image that can be used by users and application developers to
benefit from the acceleration offered by the MemryX Accelerator.

The OAAX conversion toolchain takes in any ONNX model and compiles it into a DFP (DataFlow Program) that can be executed on the MemryX Accelerator. The resulting model file is a DFP that's optimized and efficient for deployment.

It's possible that the chip doesn't accelerate all the operations in the model, in which case the toolchain will also generate a pre-/post-processing ONNX files that the user can run on a CPU or GPU.


## Artifacts

The OAAX runtime is available as a shared library that can be used by developers to load and run optimized models on
x86_64.
It's available for:
- [x86_64](artifacts-x86_64/libRuntimeLibrary.so)
- [aarch64](artifacts-aarch64/libRuntimeLibrary.so)

The OAAX conversion toolchain is available as a Docker image that can be used to convert non-optimized models to
optimized models. Due to its significant size, the Docker image is made available for
download [here](https://download.sclbl.net/OAAX/toolchains/onnx-to-mxa.tar).
> Please note that you'll need to have credentials from MemryX to able to install the MemryX SDK when running the conversion.
## How to use

### Conversion toolchain

After downloading the conversion toolchain file as ".tar", it needs to be loaded by running the following command:

```shell
docke load -i conversion-toolchain-latest.tar
```

After that, you can use the Docker image to create a container that carries out the conversion by running this command (
assuming that you have a model named `model.onnx` in the current directory):

```shell
docker run -it -v "$pwd:/root" conversion-toolchain "/root/model.onnx" "/root/build"
```

Upon success, the optimized model (along with additional pre/post processing files) will be located in `./build` folder in the host filesystem in a ZIP archive.

### Runtime

To use the runtime to run that optimized model, you can refer to any example in
the [examples](https://github.com/oaax-standard/examples) repository.
