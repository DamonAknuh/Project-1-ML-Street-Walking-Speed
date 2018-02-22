# Project-1-ML-Street-Walking-Speed

## Project Objective

The objective of this project is too detect a person walking in a video and measure/track the walking speed.  I will use python, OpenCV, and Tensorflows Object_detection as the main building blocks of the project. Python will act as the main programming language of my code. The Tensorflow API will provide a convenient object detection in which I will need to train a human model for the program to track. OpenCV will be used mostly for displaying and working with the image formats, reading images from the screen, displaying, passing data, etc... 

## Learning Goals:
I have a few learning goals I hope to accomplish by the end of the project.

* Familiarity with Working with Tensorflow Object Detection Code
* Training and building new object detection models
* Familiarity with OpenCV computer vision systems
* Familiarity with Python programming


## Tutorials:

Tensorflow starting Guide:
https://www.tensorflow.org/get_started/get_started_for_beginners

Sentdex Youtube Python/MachineLearning/Tensorflow Video Tutorials
https://www.youtube.com/user/sentdex/videos

OpenCV object Tracking:
https://www.learnopencv.com/object-tracking-using-opencv-cpp-python/

## Stages:

Here is a list of the completed stages of the project, as I think there will be a lot of tinkering with the final version to improve accuracy and speed.

- [X] 1 Object Detectiong Proof of concept
- [X] 2 Training the "Target Acquired Model"
- [X] 3 Configuring the Model to security Feed
- [X] 4 Walking speed calculations
- [X] 5 Walking speed code implementation

#### 1). Object Detection Proof of concept.

 One of the first stages of this project is a simple proof of concept to get me introduced to building object detection models. The point of this stage is too gain experience building a model first and iron out issues before committing computation time to the project-model. I decided to build a model for recognizing the middle finger sign. I did this for a number of reasons the first being that there is a plethora of pictures for training, and secondly because I thought it would be very interesting to see working. 

  I then set about gathering images for training the model. In the end I found about 105 total images for the model training, and 10 additional images for validation.  Training models should have ideally more than 100 images, and so I was in the low end for training data. After gathering the training data and before training you must label the middle finger in all the images and generate the tf.records. Training ~10000 steps with my CPU and around ~12hours. I stopped the model training process at an average total lost of 1.2. After training the model all that is left is configuring it with some tensorflow code (object_detection_tutorial.py) to detect objects from the webcam instead of image files. Then you have a full fledge middle finger detecting program right in your computer
 
 ![img-4891](https://user-images.githubusercontent.com/36031736/36290636-e6001000-12f8-11e8-9004-892dac6521c6.jpg)
 Middle Finger Detector program. Can see the highlighted detected object and threshold value for the programs confidence in the detected object. 

    
 This model was far from perfect. It had a lot of trouble recognizing every gesture that was made on the screen, and seemed quite finnicky in the recognition. It also would not recognize the gesture at a lateral angle even with its training data. For the next model I will use a larger pool of training data, and a longer training time in order to hopefully build a more accurate model. Also configuring a GPU for the training process will greatly reduce the overall time of each step.
 

#### 2). Training the "Target Acquired Model"

 After the proof of concept I felt I was ready to build the model that will be later attached to security camera feed to measure walking speed. I went out and gathered approximately 260 images to be used for the training. I also tried very hard to configure my gpu to accept training the model, but ultimately gave up and resigned myself to my cpu as the errors in the terminal mounted. 
 
![setup2](https://user-images.githubusercontent.com/36031736/36138225-15b276b0-10cb-11e8-8ae7-2acd0d7707e5.png)
This picture shows the training process at around ~25,000 steps. With an average total loss hovering at around 2.3.


![total loss](https://user-images.githubusercontent.com/36031736/36138060-83028080-10ca-11e8-876c-57f5affb4693.png)
This picture shows the graph of the total loss of the model over time at around 4,000 steps. An ideal model will have a loss under 1. Unfortunately I do not think this model will get close to 1.
 
 
![modelverified](https://user-images.githubusercontent.com/36031736/36290640-ec6d3f30-12f8-11e8-92e7-8729d9262ff7.png)
This is the final model configured. It detects people walking and labels them with green boxes and a "Target Acquired Text"
    

    
#### 3). Configuring the Model to security Feed

In this stage I have to configure the tensorflow API to capture continuos screen images of my desktop instead of previously just my video camera. I utilized pyautogui with the help of a few tutorials (Links below) to accomplish this task. Creating a continuous capture of a region of my screen. Too have the object detection run on the footage, all I have to do is drag the footage in the browser to the region of my screen being captured. 

Unfortunately pyautogui is not a very fast software. So the process of screenshotting the image and turning it into something that both TensorFlow and OpenCV can work takes a lot of time. This is a big problem as I will either need to slow down the footage or find a better screen capturing software. In my other project Google_game this comes up a lot.


![setup](https://user-images.githubusercontent.com/36031736/36137783-4fc789a0-10c9-11e8-814a-bd863d1f96e9.png)
This is a picture illustrating the camera setup. The left window is a live feed from http://www.opentopia.com/webcam/16031,
the right window shows the object detection being ran on the left window region.  


![verified2](https://user-images.githubusercontent.com/36031736/36290642-eecb8304-12f8-11e8-94e1-0cf806d82ce9.png)
This is a further example showing the model running on the security feed setup. 


tutorial links:
https://www.pyimagesearch.com/2018/01/01/taking-screenshots-with-opencv-and-python/
http://pyautogui.readthedocs.io/en/latest/screenshot.html

#### 4). Walking speed calculations
This is going to be the hardest of the part of the project. Calculating the speed of the object is an easy enough task just when considering a 2 demension object moving accross the screen for a set time. In this project it is going to be very far than 2 demension. 

For example if you have one person walking down the street you have to factor in the perspective of the camera. As the person walks farther and farther the distance that he travels in person is the same but from a 2d demensional point of view he is moving less and less. 

One of the main challengs going forward to measure the speed of a walking person in real time will be to make sure that we factor in the cameras perspective when doing the distance measurements. Simply, as a man walks further he should not be going slower because of the cameras perspective.
#### 5). Walking Speed Code Implementation


##### Psuedocode:
```
for each detection    
  if target_acquired detected  
    if confidence >= 60%  
       calculate middle point x and y of detection  
       if same object is around the same point as last time  
         calculate distorted mapped distance of old and new  
         calculate calibarated distance by K constant  
         calculate speed  
         display speed  
       store the mid points of the detection 
```
![screenshotspeed1](https://user-images.githubusercontent.com/36031736/36472496-9838f4a6-1724-11e8-91e2-f000e20d2f7a.png)
This image showcases the out-put text on the screen and the avg speed finding function

![screenshotwalking2](https://user-images.githubusercontent.com/36031736/36472498-9afb74ca-1724-11e8-9950-34f69ae24cb9.png)
This image showcases the same, but you can see between the two images the avg speed has gone down, and the 

## Conclusion:

This project is now fully able to detect and track the speed of a person walking accross the computer screen. The speed tracking gives a pretty close value to the avg walking speed of 2.8 kmph. Additionally, the calibration method that I used to account for the camera perspective could use additional tickering beyond the scope of the project I set out to make. Factors like depth of scope, lens distortion, and truncation can all lead to problems in my final working code. In the future I will probably return to this project to tinker and rework the calibration to provide further accuracy in the model. 
    
