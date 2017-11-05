---
layout      : post
title       : "Food Identification and Classification"
excerpt     : "Indiana University Bloomington"
project     : true
git         : https://github.com/rohitnair987/Age-Estimation-using-Images-of-faces
folder      : food-identification
startDate   : Jan 2016
endDate     : May 2016
tag:
- Python
- OpenCV
- Machine Learning
comments    : false
---

<center><img src = "{{ site.url }}/assets/img/projects/age-gender/icon.jpg"></center>

Humans have the ability to automatically look at the face of the person and estimate the age. For a computer to be able to do this automatically, we require algorithms that extract appropriate features from the faces and use them to learn how they map to ages.

Here's a link to the poster that we presented <a href = "{{ site.url }}/assets/img/projects/age-gender/Poster.pdf">Poster</a>

* Achieved an Average Accuracy of 70%
* Preprocessed facial images, created models from the anthropometric facial features that we extracted, and estimated age range and gender, taking into consideration variances according to race, make-up, deformities etc.
* Neural Networks, Naive Bayes, K-Nearest Neighbors an ensemble of the 3.

### Anthropometric Model:
* Only useful to distinguish between minors and adults.
* Sensitive to head pose

### Assumptions:
* Only frontal face images
* Left and right mentioned throughout are from the perspective of the viewer

<center><img src = "{{ site.url }}/assets/img/projects/age-gender/1.png"></center>

Our primary task is to detect the points in the above screenshot. Once we do that, we need to find the 8 ratios and pass them to an SVM and classify into 2 broad age groups. 

### OpenCv Haar Cascade Classifier:
* We start off by resizing the images to make it uniform 
* We detect faces using the classifier haarcascade_frontalface_default.xml and for each face
* Detect eyes, nose and mouth using pre-trained classifiers.
* We applied Canny and GFTT to each eye’s bounding box to detect left, right, top and bottom of each eye
* However we couldn’t continue with this approach because this gave extremely noisy results. For example, it gave somewhat good results with a clean image, like below, but fails to detect one of the eyes of the old man in the section below:


<center><img src = "{{ site.url }}/assets/img/projects/age-gender/2.png"></center>

### DLib Library:
* We get the face landmark for each face in the image (represented by the edges in the below image) which returns a set of 68 points to represent the jaw, left-eye, right-eye and other features
* We find which point represents our desired corners which are needed to calculating the ratios. A sample of a couple of points detected are in the below image.
* We are able to find all the points of interest and calculate the ratios (which seem approximately correct for a normal face)



### References:
* http://dlib.net/
* http://www1.coe.neu.edu/~yunfu/papers/pricai10_t4.pdf
* http://ieeexplore.ieee.org/xpl/articleDetails.jsp?arnumber=4359348
* http://alereimondo.no-ip.org/OpenCV/34



## Team
* Rohit Nair
* Srivatsan Iyer