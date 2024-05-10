# Hailo-8 on X86_64

This folder contains the shared library and the Docker image that can be used by users and application developers to
benefit from the acceleration offered by Hailo-8 chip on x86_64 machines with v4.16.0 of the driver.

## Artifacts

The OAX runtime is available as a shared library that can be used by developers to load and run optimized models on
a Hailo-8 AI Accelerator.
It's available at [libRuntimeLibrary.so](artifacts%2FlibRuntimeLibrary.so). 
> Please note, that the runtime library depends on the other 3 shared libraries that are available in the 
same directory. Make sure all files are present in the same directory when using the runtime library.  

The OAX conversion toolchain is available as a Docker image that can be used to convert non-optimized models to
optimized models.    
Due to its significant size, the Docker image is available for
download [here](https://download.sclbl.net/OAX/toolchains/onnx-to-hailo-latest.tar).

## Usage

### Using the conversion toolchain

The Hailo conversion toolchain requires certain dependencies to function properly, namely:

- hailo_dataflow_compiler-3.26.0-py3-none-linux_x86_64.whl
- hailort-4.16.0-cp38-cp38-linux_x86_64.whl
- hailort_4.16.0_amd64.deb

Those dependencies need to be accessible to the toolchain to be able to convert models.
The toolchain expects them to be available in the `/app/hailo-deps` directory of the container's filesystem when it's
started.  
That can be achieved by mounting a volume to the container when it's started, like so:

```bash
docker run -v /path/to/hailo-deps:/app/hailo-deps ...
```

Now, the remaining part of the puzzle is running the conversion toolchain with the model you want to convert.
Hailo's toolchain expects the input file to be a zipped file containing:

- ONNX model
- A folder containing a set of images to use for calibration
- A configuration file in JSON format containing the following information:
    - start_node_names: List of the names of the input nodes of the model
    - end_node_names: List of the names of the output nodes of the model
    - height: Height of the input images
    - width: Width of the input images
    - channels: Number of channels of the input images
    - nchw: Whether the model expects the input images in NCHW format or not (NHWC format)
    - means: List of the means to use for normalization
    - stds: List of the standard deviations to use for normalization

      For example:
      ```json
      {
        "start_node_names": ["Conv1", "Conv3"],
        "end_node_names": ["Softmax1", "Relu102"],
        "height": 416,
        "width": 416,
        "channels": 3,
        "nchw": true,
        "means": [0.485, 0.456, 0.406],
        "stds": [0.229, 0.224, 0.225]
      }
      ```

The command to run the conversion toolchain (after loading it from the tarball file) is as follows:

```bash
docker run -v /path/to/hailo-deps:/app/hailo-deps \
    -v /path/to/input:/app/input \
    -v /path/to/output:/app/output \
    onnx-to-hailo:latest /app/input/input.zip /app/output
```

### Using the runtime library

To use the runtime library, you need to have the version v1.16.0 of the Hailo-8 driver installed on your X86_64 machine.

The Hailo runtime can be used just like the other runtimes. You can find various and diverse usage examples in
the [examples](https://github.com/oax-standard/examples) repository.

