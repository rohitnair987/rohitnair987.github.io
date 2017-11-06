---
layout      : post
title       : "Food Identification and Classification"
excerpt     : "Indiana University Bloomington"
project     : true
tab 		: cv
git         : https://github.com/rohitnair987/Food-Recognition
folder      : food-identification
startDate   : Jan 2016
endDate     : May 2016
tag:
- C
- OpenCV
- Computer Vision
comments    : false
---

•	EigenFood
•	HaarLike
•	BagofWords
•	DeepFeatures


### Eigenfoods: 
We apply the concept of EigenFaces to our food products dataset. 
Below are the steps involved in the classifier:
*	Normalization: subtract average vector from each image 
*	Covariance: normalized class vector matrix * its transpose (instead of doing transpose * vector otherwise it’ll be huge  1200x1200 for image vector size of 1200)
*	Eigendecomposition: 
*	Using the symmetric_eigen function of CImg to calculate eigenvectors and eigenvalues from the covariance matrix. Verified eigenvectors * its transpose giving an identity matrix. Eigenvalues decrease very slowly, the last one being of the order 10-1 to 10-2 on an average, sometimes going down to 10-6
*	Using the SVD function of CImg to calculate eigenvectors and eigenvalues from the covariance matrix. Verified eigenvectors * its transpose giving an identity matrix(missing some ones though). Eigenvalues decrease very slowly, the last one being of the order 10-1 to 10-2 on an average
*	PCA Dimensionality Reduction: selecting k eigenvectors which have the highest eigenvalues from the previous result (we’ve used 10 eigenvectors with the top 10 highest eigenvalues)

### Haar-like features.
This method is a simplified version of the Viola Jones object detection framework.  Each image is divided up into adjacent rectangles, and the pixel values within each rectangle are summed.  Each feature is the difference in value of several of these rectangles.  The size of the rectangles, the number of rectangles used in the calculation and their relative position can vary.  Many combinations can be used together, and in our work we did experiment with different sizes and placements of these rectangles.

### Bag-of-words
This method begins with the extraction of SIFT descriptors from each image. The entire collection of SIFT vectors returned from all the test images should be submitted to a k-means clustering, the result of which will be a set of k vectors represent the center of each cluster.  The next step is for each image to assign each of its SIFT vectors to a cluster, based on the smallest calculated distance to any of the cluster centers.  The feature vector representing each image is an array of k values, the occurrence count of that images SIFT descriptors within each of the k clusters.

### Deep features
The idea behind implementing convolutional neural networks in this way is to take a pre-trained network and use the output of one of a deep but not final layer as features for input to another classifier, we’re using the 12th layer from the OverFeat package to extract features from our images, followed by learning from our DeepFeatures class and classifying with svm.
#### Steps in Implementation:
*	Store folder names of all the food products in an array, which is used later to calculate the category number required to be passed to the svm classifier
*	For each image in each food product, run overfeat and store the result in a separate file. This is the part which takes around 20 minutes



## Team
* Rohit Nair
* Karthik Sreenivas
* Scott McCaulay