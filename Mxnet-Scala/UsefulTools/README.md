# MXNET-Scala Some Useful Tools

Implementation of the estimates of model size and flop counts for convolutional neural networks with MXNET-Scala.

https://github.com/albanie/convnet-burden

For now, the estimation of flops only consider Layers: Convolution, Deconvolution, FullyConnected, Pooling, relu

## Building

Tested on Ubuntu 14.04

### Requirements

* sbt 0.13
* Mxnet

### steps

1, compile Mxnet with CUDA, then compile the scala-pkg;

2, 
```bash
cd Mxnet-Scala/UsefulTools
mkdir lib
```

3, copy your compiled `mxnet-full_2.11-linux-x86_64-gpu-1.3.1-SNAPSHOT.jar` into lib folder;

4, run sbt, compile the project

## Running

run `cal_flops.sh` under scripts folder



