# STYF-Stop-Touching-Your-Face
A real-time YOLOv3 object detection model for detecting face touches. 

<img src="./images/results.png" alt="drawing" width="400"/>

### Abstract
The World Health Organisation (WHO) proposes many preventive techniques to stay safe from the ongoing coron- avirus pandemic, especially to avoid touching our faces in order to decrease the probability of contracting the virus. However, touching one’s face is a very involuntary and habitual action. We propose a ’Stop Touching Your Face’ YOLOv3 object detection model which can detect unhygienic face touches and warn the user when the hand reaches fairly close to one's face. The model is trained on a manually curated dataset of ’Face-Hands’ images using data augmentation and transfer learning. We achieve an accuracy of 89% on this custom dataset. Our application is able to generalise well to people with different facial features with an average confidence score of 74%. 

We use this tensorflow [implementation of YOLO](https://github.com/AntonMu/TrainYourOwnYOLO) to train our model. You can find our trained model weights here: [link to YOLO weights](https://iiitaphyd-my.sharepoint.com/:u:/g/personal/abhinav_g_students_iiit_ac_in/EQxCNL8XP9RMqNJHQJhPl2oBXn8b9CkaLpX-PJAYnjGYfQ?e=bgxivt)

### The Pipeline:
- We first curated a custom 'Face-Hands' dataset, comprising of around 140 images - with and without my hand touching it. Data augmentation was performed as well, by randomising the brightness of the images.
- We apply transfer learning and fine-tune a YOLOv3 model for this dataset, using the pre-trained weights from ImageNet. We only predict those bounding boxes with the highest confidence scores to avoid multiple detections. 
- We then check for any overlap between the 'face' and 'hand' bounding boxes and if it's present, we play a sound file that screams 'stop touching your face!'.
- And since YOLOv3 is real-time, our python script captures images from the webcam's live feed and we feed it to our model for inference! 
The network is thus able to successfully detect if the user touches his or her face through a live camera feed, and shoots a warning at the user!  
