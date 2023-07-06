---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: A Data Set Of Skeletons Of Images From NIST Special Database 19 Of Handprinted Forms and Characters
---
## Introduction
In this article, some information is to be given about a data set to be used 
with the causal image models given in the articles <a href="#firstArticle">[1]</a>, 
<a href="#secondArticle">[2]</a>, <a href="#thirdArticle">[3]</a> and 
<a href="#fourthArticle">[4]</a>. The data set is created from the NIST special 
database 19. The information about and the download links for this database are 
given in <a href="#linkNIST">[5]</a>.

## The Creation of The Dataset
In the creation of the dataset, the image operations have been performed using 
the Python packages "opencv-python" and "scikit-image". The information and 
tutorials for "opencv-python" and "scikit-image" are given in <a href="#OpenCV">[6]</a> 
and in <a href="#scikit-image">[7]</a> respectively. The version of "opencv-python" 
used is 4.7.0.68. The version of "scikit-image" used is 0.19.3.

A sample image is first converted to greyscale. A thresholding is applied to the 
resulting image. "opencv-python" package is used in these operations. The skeleton 
of the thresholded image is obtained using "scikit-image". The skeletons with 
dimensions greater than $28 \times 28$ are resized to $28 \times 28$ dimensions. 
An adaptive thresholding is applied to the rescaled images to get the final 
skeletons.

## The Source Code
The source code for the Image class is given at the link <a href="#source1">[8]</a>. 
The code for creating the skeletons of the character "J" is at <a href="#source2">[9]</a>. 
The images of the character "J" from the NIST database are also given at the link 
<a href="#Jimages">[10]</a>. The $28 \times 28$ skeletons of most of these images 
are at <a href="#Jskeletons">[11]</a>.

## Conclusion
Some information has been given about a data set of image skeletons. The images 
are from the NIST special database 19 of handprinted forms and characters.

## References

<span id="firstArticle"> [1] [https://saffetgokcensen.github.io/blog/2022/09/13/directed-acyclic-graphs-from-an-equivalence-class-for-an-image](https://saffetgokcensen.github.io/blog/2022/09/13/directed-acyclic-graphs-from-an-equivalence-class-for-an-image)</span>

<span id="secondArticle"> [2] [https://saffetgokcensen.github.io/blog/2022/10/04/directed-acyclic-graphs-from-an-equivalence-class-for-an-image-2](https://saffetgokcensen.github.io/blog/2022/10/04/directed-acyclic-graphs-from-an-equivalence-class-for-an-image-2)</span>

<span id="thirdArticle"> [3] [https://saffetgokcensen.github.io/blog/2022/10/14/directed-acyclic-graphs-from-an-equivalence-class-for-an-image-3](https://saffetgokcensen.github.io/blog/2022/10/14/directed-acyclic-graphs-from-an-equivalence-class-for-an-image-3)</span>

<span id="fourthArticle"> [4] [https://saffetgokcensen.github.io/blog/2022/11/02/directed-acyclic-graphs-from-an-equivalence-class-for-an-image-4](https://saffetgokcensen.github.io/blog/2022/11/02/directed-acyclic-graphs-from-an-equivalence-class-for-an-image-4)</span>

<span id="linkNIST"> [5] [https://www.nist.gov/srd/nist-special-database-19](https://www.nist.gov/srd/nist-special-database-19)</span>

<span id="openCV"> [6] [https://docs.opencv.org/4.x/d6/d00/tutorial_py_root.html](https://docs.opencv.org/4.x/d6/d00/tutorial_py_root.html)</span>

<span id="scikit-image"> [7] [https://scikit-image.org/](https://scikit-image.org/)</span>

<span id="source1"> [8] [https://github.com/SaffetGokcenSen/skeleton_NIST_special_database_19/blob/main/Image.py](https://github.com/SaffetGokcenSen/skeleton_NIST_special_database_19/blob/main/Image.py)</span>

<span id="source2"> [9] [https://github.com/SaffetGokcenSen/skeleton_NIST_special_database_19/blob/main/4a_skeletons.py](https://github.com/SaffetGokcenSen/skeleton_NIST_special_database_19/blob/main/4a_skeletons.py)</span>

<span id="Jimages"> [10] [https://github.com/SaffetGokcenSen/skeleton_NIST_special_database_19/blob/main/train_4a.zip](https://github.com/SaffetGokcenSen/skeleton_NIST_special_database_19/blob/main/train_4a.zip)

<span id="Jskeletons"> [11] [https://github.com/SaffetGokcenSen/skeleton_NIST_special_database_19/blob/main/rescaled_skeleton_4a.zip](https://github.com/SaffetGokcenSen/skeleton_NIST_special_database_19/blob/main/rescaled_skeleton_4a.zip) 
