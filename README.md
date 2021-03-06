3D DenseNet in torch 
============================

3D DenseNet is using 3D Convolutional(VolumetricConvolution in torch), Pooling, BatchNormalization layers with 3D kernel. This implements is based on [DenseNet](https://github.com/liuzhuang13/DenseNet) and [fb.resnet.torch](https://github.com/facebook/fb.resnet.torch/). DenseNet introduced in the paper "Densely Connected Convolutional Networks" (CVPR 2017, Best Paper Award)

## Requirements
See the [installation instructions](https://github.com/facebook/fb.resnet.torch/blob/master/INSTALL.md) for a step-by-step guide.
- luarock install hdf5 nninit
- Download the [ModelNet40](http://3dshapenets.cs.princeton.edu/) dataset and hdf5 format ([Google Drive](https://drive.google.com/file/d/0B1S5mVkJgRwqRUZjakNuMi1yck0/view?usp=sharing), [Baidu Cloud Disk](https://pan.baidu.com/s/1hsN81qG))

## Dataset
 1. Download data through above link;
 2. and modify the file path in `train.list` and `test.list` file;
 3. then modify the `datadir` variable in `examples/run_modelnet40.sh`.

## Training
See the [training recipes](https://github.com/facebook/fb.resnet.torch/blob/master/TRAINING.md) for addition examples.

For Modelnet40, just run shell `examples/run_modelnet40.sh 0,1`, `0,1` is the GPU ids with multi-GPU supported. 
```bash
cd examples
./run_modelnet40_h5.sh 0,1
```



## Trained models


#### modelnet40_60x validation error rate

| Network        | Top-1 error | Top-5 error |
| -------------- | ----------- | ----------- |
| Voxnet         | 13.74       | 1.92        |
| DenseNet-20-12 | 12.99       | 2.03        |
| DenseNet-30-12 | 12.11       | 1.94        |
| DenseNet-30-16 | 11.08       | 1.61        |
| DenseNet-40-12 | 11.57       | 1.78        |
## Notes

This implementation differs from the ResNet paper in a few ways:

**3D Convolution**: We use the [VolumetricConvolution](https://github.com/torch/nn/blob/master/doc/convolution.md) to implement 3D Convolution.


