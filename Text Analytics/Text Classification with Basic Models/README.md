# Text Classification w. Basic Models

*Text Analytics*  
*MSc in Data Science, Department of Informatics*  
*Athens University of Economics and Business*

## *Introduction*

- **Natural language processing (NLP)** is a subfield of linguistics, computer science, and artificial intelligence
- NLP is concerned with the interactions between computers and human language
- Sentiment analysis is a NLP technique used to determine whether data is positive, negative or neutral
- It is performed on textual data to identify, extract, quantify, and study subjective information
- Furthermore, it helps businesses understand the social sentiment of their brand, product or service

## *Project Overview*

-  The primary objective of this project was to create a sentiment classifier tailored for tweets.
- To achieve this goal, we leveraged the [Sentiment Analysis: Emotion in Text Dataset](https://www.kaggle.com/competitions/tweet-sentiment-extraction/data) obtained from a Kaggle competition.
- Initial steps involved extracting descriptive statistics such as vocabulary size and review lengths.
- Subsequently, we conducted preprocessing of the reviews utilizing predominantly the `nltk` library.
- A development set, comprising ($20\\%$) of the data, was set aside for hyperparameter tuning.
- Employing text vectorization and dimensionality reduction techniques, we transformed the dataset.
- Model hyperparameters underwent tuning to enhance predictive performance.
- Beyond a baseline dummy classifier, various other classifiers were explored for predictions.
- Concluding the project, the models were trained, evaluated using diverse metrics, and learning curves were plotted for comprehensive analysis.

## *Data*

- This is a dataset for sentiment classification which contains 27K tweets for training and 3.5K tweets for testing
- The reviews are labelled positive, negative or neutral

## *Data Preprocessing*

- The first step we took was to clean the data
- Therefore, we applied the following preprocessing steps to the tweets
  - Remove non-word characters (special characters, punctuation).
  - Expand contractions.
  - Remove single characters surrounded by spaces.
  - Replace multiple spaces with a single space, ignoring case.
  - Convert to lowercase.
  - Tokenize into words.
  - Remove stopwords.
  - Lemmatize each word in the tweet.
  - Join the lemmatized words back to reconstruct the tweet.

### Text Vectorization

- The next step was to vectorize the tweets into term-document matrices using TF-IDF
- We extracted the vectors for both unigrams and bigrams and consider only the top $10000$ features
- Finally, we applied sublinear TF scaling, i.e., replaced TF with $1 + log(TF)$

### Dimensionality Reduction

- Subsequently, we conducted dimensionality reduction on the vectors obtained in the previous step.
- The objective was to decrease the number of features utilized by our models.
- Specifically, we employed the Truncated SVD transformer, well-suited for sparse matrices.
- To address time and resource constraints, we reduced the dimensionality to 2000 features.
- This reduction led to an explained variance ratio of 82% concerning our initial vectors.

## *Predictions*

### Hyperparameter Tuning

- In our prediction phase, we incorporated not only a baseline dummy classifier but also four additional classifiers.
- Specifically, we utilized `SGDClassifier`, `GaussianNB`, `KNeighborsClassifier`, and `LGBMClassifier`.
- However, our aim was to optimize the hyperparameters of these classifiers by leveraging the ***development*** set.
- To accomplish this, we established a grid encompassing various hyperparameters to be tested for each classifier.
- Employing a `RandomizedSearchCV` coupled with a 5-fold stratified cross-validation, we sought to find the best hyperparameter combinations.
- Ultimately, we assessed the cross-validation scores using the *F1-Score* metric.

### Classification Results

- To gauge and compare the performance of classifiers, we employed various metrics.
- Specifically, we utilized *Precision*, *Recall*, and *F1-Score*.
- Additionally, we calculated the macro-averaged values for the aforementioned metrics.
- As a final step, we visualized the *Confusion Matrix* for each classifier.

### Learning Curves

- Learning curves illustrate the training and validation scores across different quantities of training samples.
- This tool helps assess the impact of increasing training data on model performance.
- Additionally, learning curves can reveal whether the model is predominantly affected by variance or bias errors.
- In practice, plotting learning curves is a valuable technique for identifying potential overfitting or underfitting in a model.
