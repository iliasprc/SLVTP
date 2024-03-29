# Installation
ir-CSN-152 utilizes depthwise Conv3D. However, the naïve implementation of channelwise 3D convolution in the current Pytoch is very slow.
In order to accelerate GPU runtime, we have to use the following [pull request(pytorch1.6)](https://github.com/pytorch/pytorch/pull/40801).

For simplicity, we install the custom 3d depthwise pytorch ([3d-depthwise](https://github.com/linziyi96/pytorch/tree/3d-depthwise)) by building from source.

We recommend anaconda environment.

## Pytorch Depthwise Conv3D patch & tochvision build from source

- CUDA 10.2 & cudnn 7.5.0
- torch 1.6.0a0+4a03290
- torchvision 0.6.0a0+b68adcf

### Prerequisites
```
conda create --name pytorch1.6dw
conda activate pytorch1.6dw

conda install numpy ninja pyyaml mkl mkl-include setuptools cmake cffi typing_extensions future six requests dataclasses
conda install -c pytorch magma-cuda101   # or [ magma-cuda102 | magma-cuda100 | magma-cuda92 ] depending on your cuda version
```

### Install pytorch
```
git clone https://github.com/linziyi96/pytorch.git
cd pytorch
git submodule update --init --recursive
git checkout 3d-depthwise
python setup.py install
cd

# version check
conda list # check torch version
# or
python
# >>> import torch
# >>> torch.__version__
# '1.6.0a0+4a03290'

```

### Install torchvision
```
git clone https://github.com/pytorch/vision.git
git checkout tags/v0.6.0
python setup.py install

# version check
conda list # check torchvision version
# or
python
# >>> import torchvision
# >>> torchvision.__version__
# '0.6.0a0+b68adcf'
```

## Requirements

- Python >= 3.6
- Numpy
- simplejson: `pip install simplejson`
- GCC >= 4.9
- OpenCV: `pip install opencv-python`
- tensorboard: `pip install tensorboard`

## PT
```
git clone 
cd 
python setup.py build develop
```