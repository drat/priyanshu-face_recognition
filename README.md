# Warung Data Inception V3
Real-time face recognition, age, emotion, gender classification using CNN, tensorflow and openCV.

this can be used to identify and know the emotions, age , gender of a person. It uses your WebCamera and then identifies your characteristics in Real Time.

# ReTraining the Network - Emotion Classifier using inception v_3

This step will consist of several sub steps:

- We need to first create a directory named images. In this directory, create five or six sub directories with names like
  Happy, Sad, Angry, Calm and Neutral. You can add more than this.
  
- Now download respective images from the Internet and put it in a separate folder in some other directory. E.g., Download happy images and put it in happy directory(some other location). Remember not to put these downloaded images in directories we created in earlier step, instead put in some other directory anywhere in your pc.
  
 - Now open the "face-crop.py" program.
  - And replace the directory= "location where you have downloaded the photograph"
    For example: ```directory = "C:/Users/user/Downloads/Happy/"```
  
  - Also replace the f_directory="correosponding sub-categories inside the images folder in our repo"
      For example: ```f_directory = "C:/Users/user/priyanshu-face_recognition/images/Happy/"```
  
- Now run the "face-crop.py" program until you fill all the sub-directories inside the images directory wih their 
  respective images. Ensure you put atleast 50-100 images in each subdirectory.
 
 #### Though I have already put the different categories of emotions inside the images directory, but if you want to add more emotions you can use the above steps or use the dataset as it is. It will still give you the result.
  
- Once you have only cleaned images, you are ready to retrain the network. For this purpose I'm using inception_v3 Model
  which is quite accurate. To run the training, hit the got to the parent folder and open 
  CMD/Terminal here and hit the following:

```
  python retrain.py --output_graph=retrained_graph.pb --output_labels=retrained_labels.txt --architecture=inception_v3 --image_dir=images
```
- This may take a while depending on your processor and the files named retrained_graph.pb and retrained_labels.txt would be added to your directory.

That's it for this Step.

## Using Age/Gender classification and then integrating Everything Up

### Currently Supported Models

  - Gil Levi and Tal Hassner, Age and Gender Classification Using Convolutional Neural Networks, IEEE Workshop on Analysis 
    and Modeling of Faces and Gestures (AMFG), at the IEEE Conf. on Computer Vision and Pattern Recognition (CVPR), Boston, 
    June 2015_

    - http://www.openu.ac.il/home/hassner/projects/cnn_agegender/
    - https://github.com/GilLevi/AgeGenderDeepLearning

  - Inception v3 with fine-tuning
    - This will start with an inception v3 checkpoint, and fine-tune for either age or gender detection 


There are several ways to use a pre-existing checkpoint to do age or gender classification. By default, the code will 
simply assume that the image you provided has a face in it, and will run that image through a multi-pass classification 
using the corners and center.

##### Download the pre-trained age checkpoint for inception from here:

https://drive.google.com/drive/folders/0B8N1oYmGLVGWbDZ4Y21GLWxtV1E

##### Download the pre-trained gender checkpoint for inception from here:

https://drive.google.com/drive/folders/0B8N1oYmGLVGWemZQd3JMOEZvdGs

- After downloading both the files, unzip them into the inception directory.

### There are different functionalities that are provided in this code:

```api_main.py``` This file is basically an API which uses images/videos uploaded from your computer and performs the processing and returns the results in json format.

```streaming_main.py``` This file is used for giving the results for live streaming where opencv is used for accessing the local camera. It'll open a new window of OpenCV and then identifies your Name, Gender, Age and the emotions.

```url_main.py``` This file is used for processing the stream/image/video from url.


- Open the file you want to execute. Inside the file specify complete path for model_dir_age and model_dir_gender.

For example: ```tf.app.flags.DEFINE_string('model_dir_age', 'C:/Users/user/priyanshu-face_recognition/inception/22801', 'Model directory (where training data for AGE lives)')```

```tf.app.flags.DEFINE_string('model_dir_gender', 'C:/Users/user/priyanshu-face_recognition/inception/21936', 'Model directory (where training data for GENDER lives)')```

##### Finally, you just need to execute it from command line and it will give us the desired results.
 
 For example run the "streaming_main.py" program by typing the following in CMD/Terminal:
 ```
 python streaming_main.py
 ```

It'll open a new window of OpenCV and then identifies your Name, Gender, Age and the emotions.

![known](https://u.imageresize.org/v2/c3a6f5bd-e8ea-4d0c-a0c5-a98276a53d93.jpeg)

## Sources

##### Thanks to dpressel (https://github.com/dpressel/rude-carnie)

