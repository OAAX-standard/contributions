# CPU X86_64

This folder contains the shared library and the Docker image that can be used by users and application developers to
benefit from the acceleration offered by x86_64 CPUs (both Intel & AMD).

The OAX conversion toolchain takes in any ONNX model, validates it, then optimizes it. Hence, the resulting model file
is an ONNX model that's optimized and efficient for deployment.

On the other hand, the OAX Runtime is leveraging ONNXRuntime under the hood. It expects the model to an ONNX.

## Artifacts

The OAX runtime is available as a shared library that can be used by developers to load and run optimized models on
x86_64.
It's available in [libRuntimeLibrary.so](artifacts%2FlibRuntimeLibrary.so).

The OAX conversion toolchain is available as a Docker image that can be used to convert non-optimized models to
optimized models. Due to its significant size, the Docker image is available for
download [here](https://download.sclbl.net/OAX/toolchains/conversion-toolchain-latest.tar).

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
the [examples](https://github.com/oax-standard/examples) repository.
