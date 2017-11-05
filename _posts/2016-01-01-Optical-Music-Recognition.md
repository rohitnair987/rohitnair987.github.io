---
layout      : post
title       : "Optical Music Recognition"
excerpt     : "Indiana University Bloomington"
project     : true
git         : https://github.com/rohitnair987/Optical-Music-Recognition
folder      : music-recognition
startDate   : Jan 2016
endDate     : May 2016
tag:
- C++ 
- Music
- Conputer Vision
comments    : false
---

<center><img src = "{{ site.url }}/assets/img/projects/music-recognition/music_notes.png"></center>

Given an image of a musical score(pure or noisy), we identified notes and staves

Convolution has been implemented using brute force convolution methodology with a 2D filter. In this method only one pass is used for convolution. The time complexity of the methodology is 𝑂(𝑛^2 * 𝑘^2) where n is the rows/columns of input image and k is the rows/columns of the square filter matrix

* Average Accuracy of up to 55% (random guessing was 4%)
* 1000 images - training and 300 images - testing
* Eigen vectors, Haar-like descriptors, Bag of words using Scale Invariant Feature Transform with SVMs to classify 25 categories of food items.


### Detecting the musical symbols.
Steps 1 - 2 are done for each and every template respectively:
* Convolute the input and template images using a separable kernel. Convolution is done to blur the image
so as to smear the transition between edges.
* Using a threshold of 200 for every pixel we converted the input image and each template to binary. Pixels
above 200 are set a value of 1 and pixels below are set a value of 0.
* Calculate hamming distance between input image and the template, the output is a matrix of hamming
distances for every pixel.
* Every value greater than product of confidence threshold (90 for Notehead and 0.95 for other symbols)
and the maximum pixel value in hamming distance matrix is considered as the topmost pixel of the
musical symbol. The surrounding pixels equal to the dimensions of the template are then marked with a
negative number. This is done to mark the symbol as detected so that it is not detected repeatedly.

### Detecting the pitch of Notehead:
* Line Detection: For each row, we average the values of 5 columns. If the average is below a confidence
threshold we assume that the row is a Staff line.
* Assigning pitch: A pitch value is assigned based on the position of the Notehead relative to the staff lines.
Also, special care is taken to differentiate the higher pitch tones from the low pitch ones.


## Team
* Rohit Nair
* Anand Saurabh Sharma
* Ghanshyam Malu