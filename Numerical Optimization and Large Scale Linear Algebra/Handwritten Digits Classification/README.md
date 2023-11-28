# Handwritten Digits Classification via SVD

*Numerical Optimization and Large Scale Linear Algebra*  
*MSc in Data Science, Department of Informatics*  
*Athens University of Economics and Business*

## *Introduction*

- Handwritten digit recognition is the ability of a machine to recognize the human handwritten digits
- Handwritten digits can be found in many sources such as images, papers, touch screens etc.
- The machine should be able to recognize and classify them into predefined classes (0-9)
- Digit recognition has many applications like number plate recognition, bank check processing etc.

## *Project Overview*

- Our aim in this project is to construct an algorithm for classification of handwritten digits
- We use the training set to compute the SVD of each class (0-9) matrix
- Then, we create a least squares classifier which will use the relative residual vector as a measure
- In particular, the residuals will be calculated using the following formula:
$$ \frac {\lVert (I-U_{k}U_{k}^{T})z \rVert_{2}}{\lVert z \rVert_{2}} $$
- We use the first few (5-20) singular vectors as basis
- Then, we classify test digits according to how well they can be represented in terms of the respective bases
- Once we classify the digits, we check if all digits are equally easy or difficult to classify
- We take a look at some of the difficult ones to see if they were, indeed, badly written
- Finally we check whether it really pays off to use fewer basis vectors in one or two of the classes

## *Data*

- The data are a subset of the US Postal Service Database
- They were provided in the context of the course content
- The file `data.xslx` contains both training and test data
- The sheet `"azip"` (`"testzip"`) holds the training (test) images as an array of dimension $256\times107$
- The images are vectors of dimension $256$, that have been constructed from $16\times16$ images
- The sheet `"dzip"` (`"dtest"`) holds the digits (numbers) as a vector of dimension $1\times1707$
