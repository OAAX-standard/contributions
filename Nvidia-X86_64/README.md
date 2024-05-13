# Nvidia X86_64

This folder contains the shared library and the Docker image that can be used by users and application developers to
benefit from the acceleration offered by Nvidia GPUs (both CUDA 11 & 12 versions).

The OAAX conversion toolchain takes in any ONNX model, validates it, then optimizes it. Hence, the resulting model file
is an ONNX model that's optimized and efficient for deployment.

On the other hand, the OAAX Runtime is leveraging ONNXRuntime under the hood with the CUDA EP, hence the runtime expects
the model to be an ONNX.

## Artifacts

The OAAX runtime is available as a shared library, but it depends on other shared libraries that are all available here:
- [CUDA 11](https://download.sclbl.net/OAAX/runtimes/CUDA-11/)
- [CUDA 12](https://download.sclbl.net/OAAX/runtimes/CUDA-12/)

> Make sure all files are present in the same directory when using the runtime library, or that they accessible to the 
runtime library by setting the `LD_LIBRARY_PATH` environment variable.
> Also, make sure that CUDA-X libraries are installed on the target machine.

The OAAX conversion toolchain is available as a Docker image that can be used to convert non-optimized models to
optimized models. Due to its significant size, the Docker image is available for
download [here](https://download.sclbl.net/OAAX/toolchains/conversion-toolchain-latest.tar).

## How to use

### Conversion toolchain

After downloading the conversion toolchain file as ".tar", it needs to be loaded by running the following command:

```shell
docke load -i conversion-toolchain-latest.tar
```

After that, you can use the Docker image to create a container that carries out the conversion by running this command (
assuming that you have a model named `model.onnx` in the current directory):

```shell
docker run -v ".:/app/run" conversion-toolchain "/app/run/model.onnx" "/app/run/build"
```

Upon success, the optimized model will be located in `./build` folder in the host filesystem.

### Runtime

To use the runtime to run that optimized model, you can refer to any example in
the [examples](https://github.com/oaax-standard/examples) repository.
