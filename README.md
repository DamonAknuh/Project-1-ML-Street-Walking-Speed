# Project-1-ML-Street-Walking-Speed

## Project Objective

The objective of this project is to measure track and record the speed of a human walking accross a security cameras feed. I hope to use this data to compare walking speeds of people from cities accross the world. I will use python, OpenCV, and tensorflow-Object_detection to accomplish this. 

## Learning Goals:
I have a few learning goals I hope to accomplish by the end of the project.

* Familiarity with Tensorflow-Object_Detection
* Familiarity with OpenCV computer vision systems
* Intoduction to Python programming
* Introduction to Data science
* Visualizing and Organizing data
##Tutorials:

Tensorflow starting Guide:
https://www.tensorflow.org/get_started/get_started_for_beginners
Sentdex Youtube Python/MachineLearning/Tensorflow Video Tutorials
https://www.youtube.com/user/sentdex/videos

## Stages:

Here is a list of the completed stages of the project, as I think there will be a lot of tinkering with the final version to improve accuracy and speed.

- [X] 1 Object Detectiong Proof of concept
- [ ] 2 Training the "Target Acquired Model"
- [X] 3 Configuring the Model to security Feed
- [ ] 4 Speed Calculations
- [ ] 5 Data Gathering
- [ ] 6 Data Visualization

#### 1). Object Detection Proof of concept.

 One of the first stagres of this project is a simple proof of concept to get me introduced to tensorflow object detection software. I wanted to create and model an object to gain experience before fully diving into building this projects model.For my proof of concept model I wanted a model that would be somewhat easy to recognize, somewhat easy to find pictures for, and finally something that I could use everyday.

 For this purpose my chosen object is the vulgar middle finger gesture. I then set about gathering images for training the model. In the end I found about 105 total images for the final training model. Which was in the low end for the suggested range of 100-300 images. Training with my cpu took around ~12hours, and I stopped the model training process with an average total lost at 1.2. After configuring the model into the final setup, and hooking the model up to a live feed from my laptop camera I had a middle finger detector setup directly on my laptop. 
    
 This model was far from perfect. It had a lot of trouble recognizing every gesture that was made on the screen, and seem quite finnicky in the recognition. It also would not recognize the gesture at a lateral angle. For the next model I will use a larger pool of training data, and a longer training time in order to rectify errors seen with this model. Also possibly configuring a gpu to the training of the model could greatly inhance training time.

#### 2). Training the "Target Acquired Model"

 After the proof of concept I felt I was ready to build the model that will be later attached to security camera feed to measure walking speed. I went out and gathered approximately 260 images to be used for the training. I also tried very hard to configure my gpu to accept training the model, but ultimately gave up and resigned myself to my cpu as the errors in the terminal mounted. 
    
    
#### 3). Configuring the Model to security Feed

In this stage I have to configure the tensorflow API to capture continuos screen images of my desktop instead of previously just my video camera. I utilized pyautogui with the help of a few tutorials (Links below) to accomplish this task. Creating a continuous capture of a region of my screen. Too have the object detection run on the footage, all I have to do is drag the footage in the browser to the region of my screen being captured. 

tutorial links:
https://www.pyimagesearch.com/2018/01/01/taking-screenshots-with-opencv-and-python/
http://pyautogui.readthedocs.io/en/latest/screenshot.html

#### 4). Speed Calculations

#### 5). Data Gathering

#### 6). Data Visualization
    
    
