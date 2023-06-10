# TEXT_CLASSIFICATION


PROBLEM STATEMENT
With the rapid advancement of Internet technology, online shopping has become a popular
method of purchasing and consuming goods. User satisfaction can be improved by analyzing the
sentiment of a huge number of user reviews on e-commerce sites.
Given a mobile product review, this study aims to classify whether the message of the review is
positive or negative and to predict the number of customers satisfied with the product.


NEED FOR THE STUDY
Customer satisfaction is now a critical component of a successful product and/or service firm.
Customers&#39; decisions can be influenced by reviews, and the organization&#39;s credibility can be
enhanced. Many firms currently employ consumer sentiment analysis to improve client
experiences and hence increase profitability. Customer reviews have the power to build trust and
motivate others to interact with the company. In the end, enhanced customer interaction leads to
increased earnings for firms. The key to providing exceptional customer experiences is to
understand how customers feel about your product. When it comes to acquiring items and
services, the term &quot;what other people think&quot; is crucial.


DATA COLLECTION:
For this project, we have collected the data by web scraping. We were interested in only the
mobile product reviews from amazon. In total 4 mobile products were chosen, 3 of them were
used as training dataset and the 4th one was used for testing, for validation. Each page in amazon
has only 10 reviews, so we had to run the loop until we had got enough rows. We use Splash to
render the page for us and get the raw HTML which can be parsed and we can extract the
information with BeautifulSoup.

Training data: There are 3 mobile products-Redmi Note 11,Samsung Galaxy M32 and OPPO
A31. We had 3 different csv files and combined all of them. The dataset contains 4 variables-
product name, title of the review, body of the review and the rating of the product.
Dimensions of the training dataset:(9658, 4)
Test Data: We took the mobile phone- Samsung Galaxy A12 for our test data. Similar to the
training data, the test data has product name, title, body and rating as the columns.
Dimensions of the test dataset:(334, 4)


DATA PREPROCESSING
We cleaned the training and test datasets separately for efficient analysis. We just kept the
rating and body columns of the dataset, and deleted the rest of them.
We checked for the null values, and since there were only 299 null values, we dropped them
from the training data.
Then we move to the text cleaning part because we had the body column. We just kept
alphabets and numbers in the text.
TEXT CLEANING:
Lowercase Format: Getting lower case for the reviews in the column ‘body’.It is easier to
process the text data when it is in lowercase format.
Removal of Punctuation marks: Punctuation marks divide the text into sentences, phrases
or different paragraphs, which further affects text processing and so should be removed. We
removed punctuation marks from the text like “.?!”.
Removal of Special Characters: Removing Special characters decreases the noise in the
data.
Removal of Stop Words: In human language, stop words are present in abundance. We
remove stop words because they don’t contain much of the information and we can focus on
important information of the text.
Tokenization: It basically splits the raw text into words called tokens. This will help in
better understanding of the context and simplifies the model building phase of NLP.


FEATURE ENGINEERING

Sentiment Column: The rating column was used to create a sentiment column where 1
corresponds to positive review and 0 corresponds to negative review. For rating greater than
3, we labeled it as 1 and for the rest values we gave the label 0.
Data Augmentation: We have used the Word2Vec model for converting the text into vector
forms. Before building the model, we need to balance the imbalance data we have, because
we had more 1s compared to 0s. Data Augmentation techniques use the existing data to
generate additional, synthetic data. We use this to make the model generalize better. Data
Augmentation is performed on the training data and then we obtain a new train set. We have
used the Synonym replacement operation of the Easy Data Augmentation method for this
dataset. Here, we choose n words randomly. After finding the synonyms of those words, we
also need to preprocess them and then we replace these words with one of their synonyms
randomly.

Word2Vec Model: This algorithm uses a neural network model to understand word
association in a large text corpus. It basically produces a vector space, and each unique word
in the corpus is assigned a vector in the space. When two different words having similar
context are passed as inputs, then the Word2Vec algorithm should produce similar outputs.
In order to have similar outputs, the computed vectors for those words also need to be
similar. The main aim of Word2Vec is to learn similar vectors for words having similar
context. Patterns such as “Man is to Woman as Brother is to Sister” can be generated by
performing algebraic operations on the vector representations of the words such that the
vector representation of “Brother” - ”Man” + ”Woman” produces a result which is closest to
the vector representation of “Sister” in the model.


CONCLUSION:The aim of this study was to see if the word2vec technique, which creates word embeddings,
could be used to classify sentiment. From the results obtained, we can infer that our model
performed best when we used Support Vector Machine Algorithm and Multi-Layer Perceptron
Classifier with an accuracy yielding 80% followed by Logistic Regression which yielded an
accuracy of 78%. Random Forest algorithm yielded an accuracy of 77%. These results were
obtained after the synonym replacement data augmentation technique was used. Before using
this technique, the accuracy came to 60% for SVM and 55% for Logistic Regression because the
model was highly biased due to the huge imbalance in the data. The
