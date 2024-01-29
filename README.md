Requirement: Python 3.7-3.10

VS Code
1. Open terminal in VS Code
2. Install tensorflow, runtime, onnxruntime and tf2onnx

```pip install tensorflow```
```pip install runtime```
```pip install onnxruntime```
```pip install -U tf2onnx```

3. Install latest from github

```pip install git+https://github.com/onnx/tensorflow-onnx```

4. Once dependencies are installed, from the tensorflow-onnx folder call:  
###for python, you need to recall the path of python.exe (eg. D:\Python\python.exe) before the execution of command.

```python setup.py install``` or ```python setup.py develop```  ### you can manually allocate the folder of set.py inside the folder


5. To get started with `tensorflow-onnx`, run the `t2onnx.convert` command, providing:

* the path to your TensorFlow model (where the model is in `saved model` format)

```python -m tf2onnx.convert --saved-model tensorflow-model-path --output model.onnx```

6. The above command uses a default of `15` for the ONNX opset. If you need a newer opset, or want to limit your model to use an older opset then you can provide the `--opset` argument to the command. If you are unsure about which opset to use, refer to the [ONNX operator documentation](https://github.com/onnx/onnx/releases).

```python -m tf2onnx.convert --saved-model tensorflow-model-path --opset 18 --output model.onnx```

If your TensorFlow model is in a format other than `saved model`, then you need to provide the inputs and outputs of the model graph.

7. For `checkpoint` format:

```python -m tf2onnx.convert --checkpoint  tensorflow-model-meta-file-path --output model.onnx --inputs input0:0,input1:0 --outputs output0:0```

For `graphdef` format:

```python -m tf2onnx.convert --graphdef  tensorflow-model-graphdef-file --output model.onnx --inputs input0:0,input1:0 --outputs output0:0```

8. If your model is in `checkpoint` or `graphdef` format and you do not know the input and output nodes of the model, you can use the [summarize_graph](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/tools/graph_transforms) TensorFlow utility. The `summarize_graph` tool does need to be downloaded and built from source. If you have the option of going to your model provider and obtaining the model in `saved model` format, then we recommend doing so.

You find an end-to-end tutorial for ssd-mobilenet [here](tutorials/ConvertingSSDMobilenetToONNX.ipynb)

9. We recently added support for tflite. You convert ```tflite``` models via command line, for example:

```python -m tf2onnx.convert --opset 16 --tflite tflite--file --output model.onnx```



source: https://github.com/onnx/tensorflow-onnx.git


