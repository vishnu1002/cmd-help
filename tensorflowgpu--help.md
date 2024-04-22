## Tensorflow local GPU setup: Windows Native

### Hardware Requirements

> **Note:** TensorFlow binaries use  [AVX instructions](https://en.wikipedia.org/wiki/Advanced_Vector_Extensions#CPUs_with_AVX)  which may not run on older CPUs.

- [NVIDIA® GPU drivers](https://www.nvidia.com/drivers)  version 450.80.02 or higher.
- [CUDA® Toolkit 11.8](https://developer.nvidia.com/cuda-toolkit-archive).
- [cuDNN SDK 8.6.0](https://developer.nvidia.com/cudnn). (Nvidia login required).
- (Optional)  [TensorRT](https://docs.nvidia.com/deeplearning/tensorrt/archives/index.html#trt_7)  to improve latency and throughput for inference.

### Software Requirements

- [MultiPack Installer](https://mpvci.co.uk/) Microsoft Visual C++ .
- Install [Miniconda](https://docs.anaconda.com/free/miniconda/) or [Anaconda](https://www.anaconda.com/download/success)

### Create Environment

Open Anaconda Prompt.

```
conda create --name tf python=3.6
```

```
conda deactivate
conda activate tf
```

### Install conda packages (Miniconda)

> If you have installed Miniconda, follow the give commands


```
conda install -c conda-forge cudatoolkit=11.2 cudnn=8.1.0
```

```
pip install --upgrade pip
```

```
pip install "tensorflow<2.11"
```

### Installing conda packages (Anaconda)

- Open Anaconda and select `tf` environment and install the following packages:
- `keras`
- `tensorflow`
- `tensorflow-gpu`
- The dependency packages will be installed automatically.

### Verify the installation

- Verify GPU setup:

```
python -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"
```

- Verify CPU setup:
```
python -c "import tensorflow as tf; print(tf.reduce_sum(tf.random.normal([1000, 1000])))"
```

### Verify with Jupyter Notebook

Download [verify-tf](https://github.com/vishnu1002/cmd-help/blob/b866f4a73e7f1f70dfa33ade8e9b9a48763095aa/etc/verify-tf.ipynb) and import inside `tf` environment jupyter notebook
