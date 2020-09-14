
# Pneumonia X-ray Image Classification with Convolutional Neural Networks

# Prerequisites
Runs on latest version of Python, using Google Colab, Keras. 

# Overview

* Problem: Build a model that can classify whether a given patient has pneumonia, given a chest x-ray image.
* Audience: Medical business, imaging labs. 
* Business Questions: How can a successful model help save medical professionals time, money and promote better accuracy in patient diagnosis. 

## Content
The dataset is organized into 2 folders (train, test) and contains subfolders for each image category (Pneumonia/Normal). There are 5,385 X-Ray images (JPEG) and 2 categories (Pneumonia/Normal).

Chest X-ray images (anterior-posterior) were selected from retrospective cohorts of pediatric patients of one to five years old from Guangzhou Women and Children’s Medical Center, Guangzhou. All chest X-ray imaging was performed as part of patients’ routine clinical care.

For the analysis of chest x-ray images, all chest radiographs were initially screened for quality control by removing all low quality or unreadable scans. The diagnoses for the images were then graded by two expert physicians before being cleared for training the AI system. In order to account for any grading errors, the evaluation set was also checked by a third expert.

(Content info and dataset provided by Paul Mooney on Kaggle: https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia?)

# Select Colab directory and unzip virtually in colab.
The beginning section will help those who want to or need to run Keras and Tensorflow in Colab. I was forced to run my notebooks in the cloud using Colab because my OS was too old and wouldn't run the necesary versions of Keras. Working with Colab is very fast with image loading, as long as you set it up correctly. If not, it will be slower than a notebook on your own machine. This blog post was used to help load in your entire zip file and virtually unzip your image files in one move in colab as opposed to how Colab normally would load in each image individually: https://medium.com/datadriveninvestor/speed-up-your-image-training-on-google-colab-dc95ea1491cf

# Best Model
A CNN model with Adam optimizer proved to have the highest performance with little overfitting and a classification recall of 97%. A grid search was used to find the best parameters for this model. Training accuracy 95%. Test accuracy at 90% and loss at 50%. Pneumonia recall - 97%, F1 score 92.

train acc: 0.9546123147010803 test acc: 0.9006410241127014

Classification Report:

![classreport](https://github.com/alexanderbeat/pneumonia-xray-cnn-classification/blob/master/images/classreportadammodel.png)



Confusion Matrix and accuracy/loss plots:


![png](https://github.com/alexanderbeat/pneumonia-xray-cnn-classification/blob/master/images/output_66_1.png)



![png](https://github.com/alexanderbeat/pneumonia-xray-cnn-classification/blob/master/images/output_66_2.png)


# Feature Map Images from Hidden Layers
This will help show you what's happening with the images after each layer of the model network and how the patterns are developed.

![map]()



## Conclusion Summary

Based on this final Adam model without dropout, it seems that the process was able to classify 97% of all pneumonia patients in the test set. More tuning for the future to try and get more of the patients properly classified. 

With a high precision of 88% as well, the model is not only capturing a majority of the pneumonia case, but also being precise in diagnosis. Same goes for normal patients with a precision of 94%. 

CNN models are best for this type of work over dense layered networks. It uses such small images while still being able to break down the images using feature maps to search for patterns and accurately obtain results. Adjusting the model to work with higher res images could possibly increase accuracy performance with only a slight time increase.

Using this model adds technical advantages to aid in doctor review. It functions faster and better with image processing than a normal dense neural network. This will greatly increase processing time and cutting costs in the medical field and will allow labor hours to be redirected towards other pressing matters and care for more patients. It's recommended to use the model to scan lab images before doctor’s manual review. This will save on labor hours. Expenses can be allocated, diagnosis accuracy will go up, catching pneumonia earlier. Business reputation will go up. Patients will recognize the better care and work from the company. Using this model will also help to prevent human error. 
