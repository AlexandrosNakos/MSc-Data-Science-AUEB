# Image Feature Extraction via PCA and kPCA

*Numerical Optimization and Large Scale Linear Algebra*  
*MSc in Data Science, Department of Informatics*  
*Athens University of Economics and Business*

## *Introduction*

- In this project, we replicate the example 3.2.2 of the following paper

> ***[Kernel Principal Component Analysis and its Applications in Face Recognition and Active Shape Models](https://github.com/AlexandrosNakos/MSc-Data-Science-AUEB/blob/main/Numerical%20Optimization%20and%20Large%20Scale%20Linear%20Algebra/Image%20Feature%20Extraction/Documents/Paper%20Doc.pdf)***  
> *Quan Wang, Rensselaer Polytechnic Institute, 110 Eighth Street, Troy, NY 12180 USA*  
> *arXiv:1207.3538 \[cs.CV\], 2012*

- We use images from the Yale Face Database B
- It contains 5760 single light source gray-level images of 10 subjects, each seen under 576 viewing conditions
- We take 51 images of the first subject and 51 images of the third subject as the training data
- We then take 13 images of each of them as test data
- Then all the images are aligned, and each image has $168 \times 192$ pixels
- We use the $168 \times 192$ pixels intensities as the original features for each image
- Therefore, the original feature vector is $32256$-dimensional

## *Project Overview*

- We use standard PCA and Gaussian kernel PCA
- We extract the 9 most significant features from the training data and record the eigenvectors
- For standard PCA, only the eigenvectors are needed to extract features from testing data
- For Gaussian kPCA, both eigenvectors and training data are needed to extract features from the testing data
- In addition, for kernel PCA, we use a Gaussian kernel with $\sigma = 22546$
- For classification of the images, we use the simplest linear classifier
