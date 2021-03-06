# Parsing MXNet Parameter File In C++

This small project aims to extract parameters from pretrained MXNet .params file in C++, and only depends on the [dmlc-core](https://github.com/dmlc/dmlc-core) project. 

If you want to run your MXNet pretrained model on mobile devices with other light weight frameworks,
for example [ncnn](https://github.com/Tencent/ncnn) . You need to first extract the pretrained parameters from the .params file.

This project provides you the facility to parse the .params file and extract the weights in C++.

## Build The Project
### Compile dmlc-core

```bash
cd dmlc-core && mkdir build && cmake .. && make -j
```

### Compile The Project

```bash
mkdir build && cd build && cmake .. && make -j
```

## Testing

The `test.py` script constructs a simple nerwork with only 2 fc layers. 
```python
import mxnet as mx

data = mx.sym.Variable('data')
fc = mx.sym.FullyConnected(data=data, num_hidden=100, no_bias=False, name='fc1')
fc = mx.sym.FullyConnected(data=fc, num_hidden=1, no_bias=False, name='fc2')
```
And it will generate a .params file contains random init weights by running the script.
```bash
cd testData && python test.py
```

Then you can load the .params file and perform forward operation in C++.
```bash
cd build && ./read_nd
```
And the forward result will be the same as the output of python script.


## Some Limitations & Future Works
1. This tool has only been tested on the lastest MXNet version V 1.2.0, which may not work with older MXNet version.
2. I have only implemented the parsing of normal storage type NDArray, if your .params file contains sparse NDArray, this tool will fail to parse the file.
3. For now this project has to depend on the dmlc-core project, which I want to remove the dependency in the future improvement.
