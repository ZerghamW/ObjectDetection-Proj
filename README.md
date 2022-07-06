# ObjectDetection Using Image Ai in Python
##Note:
**You can Download the [Google Colab](https://colab.research.google.com/?utm_source=scs-index) file of mine by clicking on this 👉 [Link](https://colab.research.google.com/drive/1_QZq3XRdB1mXHSKnEh8I6Os0maX0O9LA#scrollTo=40nrdw50nFfF) 👈


## What is ***Object Detection***?
> It is a *Computer Vision Technique* deals with
*   Detection of Different and Certain Classes in Images and Videos
*   Location and Manupilation of the occurences of these Objects and items.

---

**Beginning of the Object Detection Project**

- ***Pre-requistes***
    - Python
    - ImageAI Module with Basic Computer Vision Knowledge
    - Tensorflow
    - Keras
    - os Module

---

Following are the required liberaries for further working
Suggestion: Use Google Colab if you have a low-end device...

**Works only with Installing Required Liberaries for smooth running of ImageAI Module**

These are



*   Tensorflow 2.4.0
*   Tensorflow-gpu 2.4.0
*   Keras, Numpy, Matplotlib, Opencv, h5py, Scipy, Pillow

---

### Only Install these in Local Computer for VS Code, Jupyter, or PyCharm etc.

### Don't need to install on clouds like Kaggle and Google Colab etc.

`!pip install tensorflow==2.4.0`

`!pip install tensorflow-gpu==2.4.0`

`!pip install keras==2.4.3 numpy==1.19.3 pillow==7.0.0 scipy==1.4.1 h5py==2.10.0 matplotlib==3.3.2 opencv-python keras-resnet==0.2.0`


### Now installing Image AI

`!pip install imageai --upgrade`

It is important to create Some Directories. Thses include
- Input Directory
- Output Directory
- Model Directory where downloaded files for model remains

###creating some directories / folder s
`!cd /content/`
`!mkdir /content/Input/`
`!mkdir /content/Output/`
`!mkdir /content/Model`

##Nature of this Project

We will give an input image as a file path to Image ai and will try to detect different features in an automation

- The input image is stored in drive as /content/stock-photo-bangkok-july-busy-traffic-condition-on-rachadaphisek-rd-heading-to-downtown-bangkok-in-the-449153470.jpg which is a copyright of Shutterstock
Image will look like (as an input)

![stock-photo-bangkok-july-busy-traffic-condition-on-rachadaphisek-rd-heading-to-downtown-bangkok-in-the-449153470](https://user-images.githubusercontent.com/87094714/177655482-3888475d-98f1-4e7c-95f8-112c7fb2908e.jpg)


After inserting/Uploading This Image to `./input/ `Folder
Next Step is to Download yolov-3 tiny-h5 model in `./model` Folder

### Downloading the Model
`%cd /content/Model`
`!wget https://github.com/OlafenwaMoses/ImageAI/releases/download/1.0/yolo-tiny.h5`

Begining of the Project

### Invoking detection from imageai and importing ObjectDetection and then importing os
`from imageai.Detection import ObjectDetection`
`import os`

Getting Current Working Directory by
- os.getcwd() method

`execution_path = os.getcwd()`

`getcwd` stands for "`get current working directory`"
 `os.getcwd()` returns the absolute path of the current working directory where Python is running as a string `str` and stores them in `execution_path`
 
`detector = ObjectDetection()`

`ObjectDetection()` class provides you function to perform object detection on any image or set of images as `director`

`detector.setModelTypeAsTinyYOLOv3()`

`.setModelTypeAsTinyYOLOv3()` , This function sets the model type of the object detection instance you created to the TinyYOLOv3 model, which means you will be performing your object detection tasks using the pre-trained “TinyYOLOv3” model you downloaded from the links above.
Courtesy: [ImageAI Documentation](https://imageai.readthedocs.io/en/latest/detection/index.html)

It is important to specify paths as variables, so to avoid errors

`model_path = "/content/Model/yolo-tiny.h5"`
`input_path = "/content/Input/input.jpg"`
`output_path = "/content/Output/output.jpg"`

Setting the Model Path...

`.setModelPath()` , This function accepts a string which must be the path to the model file you downloaded and must corresponds to the model type you set for your object detection instance. 
Courtesy: [ImageAI Documentation](https://imageai.readthedocs.io/en/latest/detection/index.html)

`detector.setModelPath(model_path)`

`loadModel() `, This function loads the model from the path you specified in the function call above into your object detection instance. 
Courtesy: [ImageAI Documentation](https://imageai.readthedocs.io/en/latest/detection/index.html)

`detector.loadModel()`

`.detectObjectsFromImage()` , This is the function that performs object detection task after the model as loaded. It can be called many times to detect objects in any number of images. 
Courtesy: [ImageAI Documentation](https://imageai.readthedocs.io/en/latest/detection/index.html)

`detections = detector.detectObjectsFromImage(input_image=input_path, output_image_path=output_path, minimum_percentage_probability=30)`

`for eachObject in detections:
    print(eachObject["name"] , " : ", eachObject["percentage_probability"], " : ", eachObject["box_points"] )
    print("--------------------------------")`
