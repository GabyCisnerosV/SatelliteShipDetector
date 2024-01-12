# SatelliteShipDetector
Identifying ships in satellite images using CNN (U-Net).

## Overview
The main purpose of this project was to predict segmentation masks of ships of various sizes in satellite images.

This was done in collaboration with BAE Systems as one of the projects done to obtain my MSc in Data Science.

It is a Kaggle challenge, which can be found here:\
https://www.kaggle.com/c/airbus-ship-detection/overview

## Project's Code
Everything is located in one notebook in Google Colab:\
https://colab.research.google.com/drive/12ThYmXw1ntccm0GdYQueSMTxeAwO0ZCn?usp=drive_link

This notebook has the following structure:\
I. Importing Data\
II. Exploratory analysis\
III. Dealing with imbalanced data\
IV. Spliting into training, validation and testing\
V. Resampling images\
VI. Building the model\
VII. Evaluation and Testing

## Dataset Description
A.	Set of satellite images for training: This set contains 192 566 images. These images have a resolution of 768x768 pixels, and they are in RGB color format. It is relevant to mention that they can have 0 to 15 ships per image.

B.	Set of satellite images for testing: The test set includes 15 606 images with the same 768x768 resolution and RGB color.
  
C.	CSV file with ship masks from training images: The CSV file contains 231 723 rows, and each row represents a ship (mask) present in an image. This means that for a single image we can have multiple rows available depending on the number of ships displayed in the image. 

## Results
After performing the hyperparametric tuning of the model, and testing the model, we got a binary accouray of 92.37% and an IoU of 26.98% (there is on average a 26.98% of overlap between the predicted and the real ship masks). Given how small the ships are in relation to the image, this is a good result.

When examining the ship predictions visually, we saw that the model did an excellent job of predicting images that are in the water with no land nearby. These predictions are accurate even when there are waves in the water and when having multiple ships in the image. On the other hand, when ships are close to land, the model’s predictions made vary a lot from picture to picture. 

## Conclusions
After going through the procedure and analyzing the results, we concluded that U-Net is a valuable tool for evaluating this and other image segmentation scenarios where the detected objects represent a reduced number of pixels than the background. However, the fundamental issue that must be addressed to make more accurate predictions is the data and pixel imbalance. Hyperparameter tuning is critical as we can go from predicting no ships at all to predicting objects like land, ports, or clouds as ships.
