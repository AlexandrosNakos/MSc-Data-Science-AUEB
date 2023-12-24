# Text Classification w. MLPs

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
- We displayed baseline results using two classifiers
- Specifically, we used a dummy classifier and the best classifier from [text_classification_with_basic_models](https://github.com/AlexandrosNakos/MSc-Data-Science-AUEB/blob/main/Text%20Analytics/Text%20Classification%20with%20Basic%20Models/Twitter%20Sentiment%20Analysis.ipynb)
- Subsequently, we fine-tuned the hyperparameters of the MLP (Multi-Layer Perceptron) model by employing `KerasClassifier` along with `RandomizedSearchCV`.
- Our focus during tuning was on optimizing the number of neurons and the dropout rate in the MLP architecture.
- The training process of the MLP model utilized the `ModelCheckpoint` callback, ensuring the preservation of the best weights for each node.
- Following the training phase, we created visualizations illustrating the accuracy and loss trends on the training data across various epochs.
- The MLP model's performance was rigorously evaluated using the *test* set.
- Concluding the evaluation, we generated a visual representation of the *confusion matrix*.

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

### MLP Hyperparameter Tuning

- Proceeding further, we entered the phase of optimizing certain hyperparameters of the MLP (Multi-Layer Perceptron) model with the aid of the *development* set.
- The parameters that underwent tuning were the *number of neurons* and the *dropout rate*.
- To perform this optimization, we implemented a `RandomizedSearchCV` procedure, coupled with a $5$-fold stratified cross-validation strategy.
- Post-tuning, we conducted an evaluation of the scores derived from the cross-validation process, utilizing the *F1-Score* metric.

### Classification Results

- Concluding the process, the ultimate step involved training the MLP (Multi-Layer Perceptron) model with the hyperparameters that resulted from the tuning phase.
- Furthermore, the `ModelCheckpoint` callback was incorporated to save the optimal weights for the nodes during training.
- Subsequently, graphical representations in the form of curves, illustrating the accuracy and loss on the training data over epochs, were generated.
- An assessment of the MLP model's performance was executed using the *test* set.
- Finally, the *confusion matrix* was visualized, providing insights into the model's classification results.
