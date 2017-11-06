---
layout      : post
title       : "Distributed K-Means"
excerpt     : "Indiana University Bloomington"
project     : true
tab 		: sd
git         : https://github.com/rohitnair987/Distributed-K-Means
startDate   : October 2016
endDate     : December 2016
tag:
- Java
- Distributed Systems
- Hadoop
comments    : false
---

K-Means is an NP-Hard problem, so we can’t find the optimal solution to every problem. Our aim in general is to find the sweet spot between accuracy and efficiency using the resources that we have at our disposal.

An unsupervised clustering algorithm, with tunable parameters - K-Means Mini Batch. We tweak the standard algorithm and perform it in batches in a parallel environment using Indiana University’s HARP API. Our approach is specifically for document clustering, which can be used in search engines and in document organization.  

### Steps: 
* We calculate the number of files in which each word occurs
* The parent node specifies which document ids each node will be working on
* Mapper step: We do this in parallel: each node calculates a local Hashmap<word, count>.
* Reduce step: The parent node aggregates this and writes to a file (let’s call it Global map of word frequencies).
* We also write a word to id mapping wordToIndexMap<word, index> which will be used by nodes to identify the index of each word that they encounter.


### Algorithm skeleton:
* Read f files per node in parallel. (This is the mapper stage)
* Load global hash table containing words and corresponding frequencies obtained during initial processing step.
* Load global hash table containing words and corresponding indexes obtained during initial processing step.
* Broadcast both the global hashmaps
* For each word in each document calculate TF and IDF and obtain TF*IDF
* Write the table in files where each tuple contains current document id, TF*IDF for all the words in all documents. The words that are not there in in the current document will have TF*IDF = 0.
* N nodes will write this tabular data into f files.


<br />
### Team:
* Rohit Nair
* Abhijit Karanjkar