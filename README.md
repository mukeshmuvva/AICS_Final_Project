# Subverting Your Machine Learning SPAM Filter

# Introduction
This Project talks about using statistical machine learning which were trying to build securities in large scale systems. This project shows how an adversary can exploit statistical machine learning. what kind of attacks can be done on a statistical machine learning model. what kind of defenses we should use to prevent attacks like this.

Bayesian filters were used mostly to detect spam messages. These filters categorize all the messages into two categories
1) SPAM
2) HAM

# How do Bayesian SPAM filters work?
These filters work mostly using conditional probability. when training the model, the models were trained on a large dataset which consists of many emails which were already categorized into SPAM or HAM. The algorithm will store all the words seen in the emails into two categories, a SPAM category and a HAM category. When an email comes to the model, it would try to calculate the probability of email being considered into HAM or SPAM by using both the word matrices of HAM and SPAM. This probability would be compared to a threshold model for classification.

# Dataset
I have used Enron-Dataset. This Dataset consists of 33716 records. This Dataset consists of emails both labelled as SPAM or HAM. There are 16545 SPAM Emails, 17171 HAM emails. There are two features in this DataSet.
1) Message
2) Class

The Message has email content. The Class is a variable which categorizes the SPAM and HAM emails.

# Data Preprocessing
1) Read the text
2) Load it into a Pandas Data Frame
3) Convert Data Frame into Pickle Object
4) The Data should be saved in pickle file just to save yourself from not processing of huge data again and again.
5) Using a GPU is recommended.
# Data Cleaning
1) Remove all Punctuation
2) Remove all urls
3) Remove numbers and newlines
4) Convert all strings to lower case
5) I have used regular expressions to do this task.
# Data Preparation
1) Split the message string into individual words.
2) Stem each word from the message
3) Remove english stop words
4) Split the text by white spaces, and link the different forms of the same word to each other.
5) Some words such as "the" or "is" appear in all emails and don't have much content to them. These words are not going to help the algorithm to distinguish SPAM from HAM
# Building Model
1) Vectorize words and split data into trian/test sets
2) Transform the words into a tf-idx matrix using the  sklearn Tf-Idx transformation.
3) Use stratify parameter will make a split so that the proportion of values in the sample.
4) Trian a naive bayes Classifier
5) Evaluate the performance with the accuracy score.

# Evaluations of simple Naive Bayes Model
|  Metric          |  Value                          |
| ---------------  | ------------------------------  |
| Accuracy         | 0.98                            |
| Confusion Matrix | array([[3262,54],[47,3381]])    |
| F1 Score         | 0.982585890                     |
| Recall Score     | 0.96289382656                   |

# Dictionary Attack
1) A list of Emails which were Spam emails, labelled as HAM
2) These Emails were trained into the model.
3) The model is subverted now, because the update model has drastically changed values for SPAM and HAM words
4) The model would Classify SPAM emails as HAM now.

# Focused Attack
1) A sample email was taken which was HAM
2) The training Data Set was injected with SPAM emails which were in the shape of above Sample email. 
3) All the keywords from the sample email was taken and Many Spam emails were created.
4) After training this particular range of HAM emails were classified as SPAM.
# Defenses implemented in this Project
1) Reject on Negative impact defense
2) Dynamic Threshold Defense
Both of these defenses were implemented to not to subvert a Naive Bayes Based Machine Learning algorithm.

# Results
1) Reject on Negative impact defense is more better than threshold based defense
2) The dictionary attack and focused attacks were more minimized with Reject on Negative Impact defense.
3) The focused attack was more difficult to implement because of the patterms needs to be generated for misclassification.

| #                    | Reject on Negative Impact                | Threshold                                |
|----------------      |   -------------------------------------- |   ----------------------------------     |
| Accuracy             | 96%                                      | 92%                                      |
| Confusion Matrix     | array([[3362,54],[47,3281]])             | array([[2962,54],[47,3681]])             |
| F1 Score             | 94%                                      | 90%                                      |
| Recall Score         | 89%                                      | 85%                                      |

# Conclusion
1) I suggest to have an Implementation of Reject of Negative defense to your ML spam filter
2) This helps in preventing a subversion
3) Training needs to be done Meticulously
