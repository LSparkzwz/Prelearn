## First approach: 
The first approach is straightforward, the binary classifiers are trained with a dataset where each row corresponds to a pair of word document embeddings and a variable that's 1 if the second document embedding is a prerequisite of the first one and 0 otherwise.  
The validation scores are then calculated by comparing the results given by the classifier with the ground truth.  

In this approach different datasets and different classifiers have been tested.


### How the dataset is obtained:
