# Enhancing News Categorization via BERT Research

## Introduction
With the advent of the internet, millions of articles, videos, music, news posts, and other forms of data are stored in hundreds of thousands of databases daily. However, a vast majority of this data is unlabeled and uncategorized, making it incredibly difficult for people to access the vast offerings of the internet. While humans can categorize most of this information in minutes, the sheer volume makes it nearly impossible for humans alone to manage.

In recent years, there has been a revolution in deep learning and NLP techniques for analyzing text data. From RNNs to GPT-3 to transformers, numerous models are now available that can successfully label a corpus of text. One area of interest is improving text classification by changing how we present text data to models. Instead of merely tokenizing words or using simple equations like TF-IDF, we can use deep learning models to transform text into embeddings—learned representations of text that better capture context. This investigation aims to evaluate the improvement in text classification using word and sentence embeddings derived from the BERT model.

## Dataset

### 20 Newsgroups Dataset
The dataset used for this model is the 20 Newsgroups dataset created by Ken Lang. It contains 18,846 articles split into twenty distinct newsgroup categories, which can be grouped into six main categories: Computers, Recreation, Religion, For Sale, Science, and Politics. The articles vary in length, from short posts of a few sentences to longer pieces of up to 30-40 sentences.

## Preprocessing
A significant portion of the processing time is spent on the lengthy preprocessing required to prepare the word and sentence embeddings. First, each article is converted into individual sentences and words using Spacy’s pipeline. Each sentence is then tokenized into individual words, with special tokens added, converting the tokens to their corresponding BERT IDs, and truncating or padding them to ensure uniform length.

Using the pre-trained BERT model, we insert the BERT IDs and attention mask vectors for each sentence, outputting the hidden states of the model's 12 hidden layers. For word embeddings, the last four hidden layers are summed together. These embeddings are then averaged by sentence to produce sentence embeddings.

## Model
The model employs a Recurrent Neural Network (RNN) layer as its foundation, with slight variations between the sentence and word models. The BERT sentence model takes a specific input shape to capture the necessary contextual information. The output passes through two ReLU layers, reducing the values to twenty nodes using a softmax function for classification.

### Softmax Function
The loss function comprises two cross-entropy functions to optimize different aspects of prediction. One focuses on predicting the correct general category, while the other penalizes the model for failing to accurately classify specific newsgroup topics.

## Results and Future Work
The model achieved a 94% accuracy for general categories. However, when attempting to classify more specific topics, results were less satisfactory. Training on 18,000 news articles took over two days, which is significantly longer than traditional machine learning algorithms like Naive Bayes, which can achieve similar accuracy in a fraction of the time. Nevertheless, the model showed better accuracy on external datasets, suggesting avenues for further research.

## Conclusion
This project demonstrates the potential of using BERT for news categorization, highlighting both its strengths and areas for improvement. Further research could explore optimizations in preprocessing, model architecture, and training efficiency.
