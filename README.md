# Bird Species Image Classification Model

## Overview

### Goal
The goal of this study is to build an image classification model to classify bird images into species.

### Data
Data set of 20 bird species. 3208 training images, 100 test images(5 images per species) and 100 validation images(5 images per species. This is a very high quality dataset where there is only one bird in each image and the bird typically takes up at least 50% of the pixels in the image. As a result even a moderately complex model will achieve training and test accuracies in the mid 90% range.  

Note: all images are original and not created by augmentation  

All images are 224 X 224 X 3 color images in jpg format. Data set includes a train set, test set and validation set. Each set contains 475 sub directories, one for each bird species. The data structure is convenient if you use the Keras ImageDataGenerator.flow_from_directory to create the train, test and valid data generators. The data set also include a file birds.csv. This cvs file contains 5 columns. The filepaths column contains the relative file path to an image file. The labels column contains the bird species class name associated with the image file. The scientific label column contains the latin scientific name for the image. The data set column denotes which dataset (train, test or valid) the filepath resides in. The class_id column contains the class index value associated with the image file's class.  

NOTE: The test and validation images in the data set were hand selected to be the "best" images so your model will probably get the highest accuracy score using those data sets versus creating your own test and validation sets. However the latter case is more accurate in terms of model performance on unseen images.  

Images were gather from internet searches by species name. Once the image files for a species was downloaded they were checked for duplicate images using a python duplicate image detector program I developed. All duplicate images detected were deleted in order to prevent their being images common between the training, test and validation sets.  

After that the images were cropped so that the bird in most cases occupies at least 50% of the pixel in the image. Then the images were resized to 224 X 224 X3 in jpg format. The cropping ensures that when processed by a CNN their is adequate information in the images to create a highly accurate classifier. Even a moderately robust model should achieve training, validation and test accuracies in the high 90% range. Because of the large size of the dataset I recommend if you try to train a model use and image size of 150 X 150 X 3 in order to reduce training time. All files were also numbered sequential starting from one for each species. So test images are named 1.jpg to 5.jpg. Similarly for validation images. Training images are also numbered sequentially with "zeros" padding. For example 001.jpg, 002.jpg ….010.jpg, 011.jpg …..099.jpg, 100jpg, 102.jpg etc. The zero's padding preserves the file order when used with python file functions and Keras flow from directory.  

The training set is not balanced, having a varying number of files per species. However each species has at least 130 training image files.  
One significant shortcoming in the data set is the ratio of male species images to female species images. About 80% of the images are of the male and 20% of the female. Males typical are far more diversely colored while the females of a species are typically bland. Consequently male and female images may look entirely different .Almost all test and validation images are taken from the male of the species. Consequently the classifier may not perform as well on female specie images.  

Source: https://www.kaggle.com/datasets/umairshahpirzada/birds-20-species-image-classification/data  

### Methodology
ImageDataGenerator was used for preprocessing and augmenting the data. Convolutional Neural Networks (CNNs) was used to analyse the augmented and preprocessed data and to build the classification model.
