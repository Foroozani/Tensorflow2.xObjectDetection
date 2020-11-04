
# TensorFlow 2 Object Detection API on ubuntu 18.04
[![TensorFlow 2.2](https://img.shields.io/badge/TensorFlow-2.2-FF6F00?logo=tensorflow)](https://github.com/tensorflow/tensorflow/releases/tag/v2.2.0) [![Documentation Status](https://readthedocs.org/projects/tensorflow-object-detection-api-tutorial/badge/?version=latest)](http://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/?badge=latest)

## Set up and running TensorFlow  API

---

A "short" tutorial that started off as self notes on how to set-up and running with the TensorFlow Object Detection API. In July 10, 2020 TensorFlow introduced That the  Object Detection API officially supports [TensorFlow 2](https://blog.tensorflow.org/2020/07/tensorflow-2-meets-object-detection-api.html). Therefore, an updated version of the tutorial was created to cover itS. 

To read the tutorial, visit [http://tensorflow-object-detection-api-tutorial.readthedocs.io](http://tensorflow-object-detection-api-tutorial.readthedocs.io).


## Install TensorFlow 2 on Ubuntu 18.04 OS
---
**step 1**. Creating a virtual environment

Create a virtual environment in order to install TensorFlow into it without compromising with other projects. I am utilizing `Anaconda` usually. To create a new virtual environment called `tf2.3`, for instance. Run the following command to create and activate the environment:

```bash 
conda create --name tf2.3 python=3.8

conda activate ft2.3
```
Create a new folder and name it _test_, for instance. Navigate to this directory `$ cd test`,

```bash
(tf2.3) user@username:~/test$
```

**step 2.** (a)-Download

Download or clone *TensorFlow repo.*  from  [Tensorflow official link](https://github.com/tensorflow/models "TensorFlow") in your _test_ directory 

```bash 
git clone https://github.com/tensorflow/models
```
Then extract all the files from `model-master.zip`. Then copy `research` folder from `$test/model-master/` to ``

```bash 
(tf2.3) user@username:~/test/model-master$
(tf2.3) user@username:~/test$scp -r model-master/research .
(tf2.3) user@username:~/test$rm -r model-master   # you can delet this folder 
(tf2.3) user@username:~/test$cd research 
(tf2.3) user@username:~/test/research$cp object_detection/colab_tutorials/object_detection_tutorial.ipynb . #copy notebook file to research folder 
```

Now we have all the required files to start object detection tutorial. 


(b)- installing libraries

Start by installing `jupyter notebook`

```bash 
pip install jupyter
pip install "tensorflow == 2.3.0" # instlling the latest version
pip install tf_slim

pip install pycocotools
# Successfully installed cycler-0.10.0 cython-0.29.21 kiwisolver-1.3.1 matplotlib-3.3.2 pillow-8.0.1 pycocotools-2.0.2
```

(c) Protobuf compilation

The TensorFlow object detection API uses protobufs, protocol buffers -- Google's data interchange format (https://github.com/protocolbuffers/protobuf/releases), to configure the models and their training parameters. Before the framework can be used, the protobuf libraries must be compiled, and that requires different steps if you are in a Unix (Linux or Mac) or Windows OS environment.

So for the Linux OS, download **protoc-3.13.0-linux-x86_64.zip** from [protobuf](https://github.com/protocolbuffers/protobuf/releases) in your *test* folder and unzip it `unzip protoc-3.13.0-linux-x86_64.zip `. 
```bash
# From test/research directory
(tf2.3) user@username:~/test/research$ ~/test/protoc-3.13.0-linux-x86_64/bin/protoc object_detection/protos/*.proto --python_out=.
```
**step 3.** running
open a jupyter notebook from *research path*. Accordingly set the relative path in **Loading label map* section:

```python 
#Note: you are alrady in research folder
PATH_TO_LABELS = 'object_detection/data/mscoco_label_map.pbtxt'  

PATH_TO_TEST_IMAGES_DIR = pathlib.Path('object_detection/test_images') 
```
if you get error,

```python 
import pathlib
```
The `object_detection_tutorial_mod.ipynb` will run fine.


---
## Credits 
Source code (https://github.com/tensorflow/models)

Installation (https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/install.html)

Installation (https://www.tensorflow.org/install) 
