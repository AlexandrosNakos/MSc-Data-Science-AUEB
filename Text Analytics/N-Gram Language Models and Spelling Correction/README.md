# Spelling Correction

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

-  At first we generated the dataset corpus and vocabulary by substituting all out-of-vocabulary words with a the token "UNK"
-  We splited the data into training, development and test sets
-  Then we created the unigram, bigram and trigram language models
-  After that we calculated the model cross-entropy and perplexity
-  We tuned alpha to find the optimal cross-entropy
-  Finally, we implemented the context aware spelling corrector with the utilization of a beam-search decoder

## *Data*

- Utilizing **The Penn Treebank** dataset for this exercise.
- The dataset comprises diverse text genres such as news articles, fiction, and academic writings, amounting to over 4.5 million words.
- Annotated with part-of-speech tags, syntactic structures, and named entities, enhancing its utility for natural language processing tasks.
- Noteworthy inclusion of detailed sentence structures, providing valuable phrase structure trees crucial for tasks involving syntax and grammar.
- The Penn Treebank is widely recognized in research, significantly influencing the development of natural language processing algorithms and serving as a benchmark dataset for model evaluations in various linguistic domains.
