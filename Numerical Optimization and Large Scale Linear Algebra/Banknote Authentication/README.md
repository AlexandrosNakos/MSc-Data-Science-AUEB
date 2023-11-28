# Banknote Authentication via Least Squares

*Numerical Optimization and Large Scale Linear Algebra*  
*MSc in Data Science, Department of Informatics*  
*Athens University of Economics and Business*

## *Project Overview*

- The scope of this project was to predict whether a given banknote is authentic given a number of measures
- We used the least squares procedure to create a classifier
- We classified our items based on the following assumption:
    - *"If the prediction value > 0.5, then we classify the item as 1, otherwise as 0"*
- Next, we computed the confusion matrix
- We checked the number of FN and FP to see if there was a serious imbalance
- Then we tried to find a value of $\alpha$ which balances the two numbers
- For the optimal value of $\alpha$, we computed, again, the confusion matrix and the error rate for both sets

## *Data*

- The data were provided in the context of the course content
- However, they are also available in the [UCI Machine Learning Repository](https://archive-beta.ics.uci.edu/ml/datasets/banknote+authentication)
- The data were extracted from images that were taken from genuine and forged banknote-like specimens
- For digitization, an industrial camera usually used for print inspection was used
- The final images had $400 \times 400$ pixels
- Wavelet Transform tool were used to extract features from images
- The dataset contains banknote image features such as variance, skewness, curtosis and entropy

## *Conclusion*

- We observed an improvement betweeen the balance of the False Positive and False Negative rates
- This also leads to a better performing classifier, which is evident from the both error rates
