<p align="center">
  <img width="500" alt="logo" src="https://autokeras.com/img/row_red.svg"/>
</p>

Official Website: [autokeras.com](https://autokeras.com)

##
AutoKeras: An AutoML system based on Keras.
It is developed by <a href="http://faculty.cs.tamu.edu/xiahu/index.html" target="_blank" rel="nofollow">DATA Lab</a> at Texas A&M University.
The goal of AutoKeras is to make machine learning accessible to everyone.

## This Project
Adding several time series classification models, ResNet34, InceptionTime, TemporalConvnet, Xception1D.

## Example
Here is a short example of using the package.

```python
import autokeras as ak

# Initialize the classifier, such as InceptionTime.
input_node = ak.Input()
output_node = ak.InceptionTimeBlock()(input_node)
output_node = ak.ClassificationHead()(output_node)
clf = ak.AutoModel(inputs=input_node, outputs=output_node, max_trials=20)

clf.tuner.search_space_summary()

# Search for the best model.
clf.fit(x_train, y_train, epochs=100, validation_split=0.1, batch_size=128, callbacks=[keras.callbacks.EarlyStopping(patience=10)],verbose=1)
clf.tuner.results_summary()
```

For a detailed tutorial, please check [here](https://autokeras.com/tutorial/overview/).

## Installation

0. 安装kerastuner和autokeras(v1.0.0),可直接pip install autokeras==1.0.0（会自动安装kerastuner）
1. 将keras-tuner文件夹下的文件添加（替换）到包文件夹：site-packages/kerastuner/
2. 将auto-keras文件夹下的文件添加（替换）到包文件夹：site-packages/autokeras/
3. executions_per_trial=4(每个trial执行次数)可在 kerastuner/engine/multi_execution_tuner.py中修改

[autokeras v1.0.0](https://github.com/keras-team/autokeras/releases/tag/1.0.0)