# Speaker-and-Gender-Determination-in-London-EastEnders-NLP
Natural Language Processing Project to determine the Gender and identify the speakers from the texts of conersations 

This project was done on Google Colab, so please change the destination path of the test	 and train data to the appropriate location( Maybe remove the ‘/’ before the path). The oath is defined under the heading MAIN. 
 
There are 2 folders in the submission.  
The folder ‘working’ contains code working upto but not including the inclusion of POS Tagging. The folder ‘final’ contains the final version of the project. 
 
The files project.py and project.ipynb contain the combined code for determining both the Gender and the speaker.  
The files gender.py and gender.ipynb contain code for determining only the gender of the speaker. 
 
 
Objective: 
This project aims to identify the gender of the person speaking, as well as the name of the person. These two tasks are performed separately. 
 
Approach Used: 
 
NLTK, Sklearn, and gensim are the libraries that have been used for this project. 
 
 
For multilabel classification, the labels used were ‘male’ and ‘female’ in the case of gender determination, and the names of the speakers in the case of determining the speaker. The CSV was read and parsed to give text and it’s label which was then added to the rawData. For PreProcessing, all punctuation was removed and the words were tokenized. Every character was converted to lowercase. Stop words were removed. Lemmatisation was also performed. A dictionary was made where the keys are the tokens, and the values are the weight of the tokens. Initially, the weight assigned to each token was equal to 1.0 / length of the token list. Bigram tokens were also used.  
 
 
POS Tagging was used for tokens. The library nltk.data.load('grammars/large_grammars/atis.cfg'	)  was used as the	 
grammar for generating tree structures. But there are words present in the training and test data that are not present in the grammar, which in turn gave errors. Consequently only POS tagging was implemented and trees were not generated for whole sentences. 
The tags of each word were accounted for in the feature engineering section. Whenever the POS-tag of a token was the same as the tag of the same token previously, then the score of that token was increase by 1.0/len(tokens). If the tag was different, then the score was decreased by the same amount. This had the effect of slightly increasing the resulting scores as shown below.  
 
Word2Vec was used with the gensim library. The list of words in the training and testing dataset were fed into the Word2Vec function. For every token in the sentence, the average of all the values of its vector was calculated, and added to the score of the token in the global dictionary. 
 
 
 
