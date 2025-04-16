# CPU

## How to use

### Conversion toolchain

After downloading the conversion toolchain file as ".tar", it needs to be loaded by running the following command:

```shell
docke load -i conversion-toolchain-latest.tar
```

After that, you can use the Docker image to create a container that carries out the conversion by running this command (
assuming that you have a model named `model.onnx` in the current directory):

```shell
docker run --rm -v ".:/app/run" conversion-toolchain:latest "/app/run/model.onnx" "/app/run/build"
```

Upon success, the optimized model will be located in `./build` folder in the host filesystem.

### Runtime

To use the runtime to run that optimized model, you can refer to any example in
the [examples](https://github.com/oaax-standard/examples) repository.
