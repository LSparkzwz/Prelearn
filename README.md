### Meaning of the table columns:

#### Averaged word embeddings:
The document embeddings have been created by averaging the word embeddings.

#### (Avg)Biased: both weight 10% of doc length:
The document embeddings have been created by averaging the word embeddings while giving a weight equal to 10% of the document's length to words inside the documents A and B that also appear in the title of B.

##### Intuition:
If I find in the documents A and B the words that make up the title in the document B, then there's a good chance that B is a prerequisite of A.  

##### Examples of intuition:  
The wikipedia page of "Light" is a prerequisite of the wikipedia page of "Total internal reflection".  
The wikipedia page talking about "Total internal reflection" mentions the word "light" many times.  
"Magnet" is a prerequisite of "Magnetic field".   
The word "magnet" appears various times in the "Magnetic field" page.  

The weight given to the word is 10% length of the document A or B respectively.  
The bigger the document the bigger the weight.  
This is to prevent small documents from being too dependant on the word and for the word to be irrelevant in big documents.  

After the weight has been given to each word, the documents become an averaged word embeding just like before.


#### (Avg)Biased: only A weight 10% of doc length:
The document embeddings have been created by averaging the word embeddings while giving a weight equal to 10% of the document's length to words inside the document A  that also appear in the title of B.

##### Intuition:
The same as the previous point, but this time weight are given only to words found in the document A, not the ones in B
(If I find in A the words that make up the title in B, then there's a good chance that B is a prerequisite of A).  

#### (Avg)B doc embedding * weight(20):
The averaged word embedding of the document B get multiplied by 20 in order to see if this difference between the two embeddings (A and B) helps the classifiers somehow.


|  ![Fasttext](https://fasttext.cc/docs/en/pretrained-vectors.html)  | Averaged word embeddings        | (Avg)Biased: both weight 10% of doc length  | (Avg)Biased: only A weight 10% of doc length | (Avg)B doc embedding * weight(20) 
| ------------- |-------------| -----------------| ----|---- | 
| Logistic Regression  |Accuracy:0.824725 <br> Precision:0.857143 <br> Recall:0.028302 <br> F1:0.054795| Accuracy:0.890771 <br> Precision:0.832000 <br> Recall:0.490566 <br> F1:0.617211 | Accuracy:0.825572 <br> Precision:0.750000 <br> Recall:0.042453 <br> F1:0.080357 | Accuracy:0.902625 <br> Precision:0.801242 <br> Recall:0.608491 <br> F1:0.691689 
| Linear SVM <br> C = 500     | Accuracy:0.921253 <br> Precision:0.805128 <br> Recall:0.740566 <br> F1:0.771499| Accuracy:0.898391 <br> Precision:0.693277 <br> Recall:0.778302 <br> F1:0.733333 |Accuracy:0.912786 <br> Precision:0.755869 <br> Recall:0.759434 <br> F1:0.757647 | Accuracy:0.909399 <br> Precision:0.737557 <br> Recall:0.768868 <br> F1:0.752887 
| RBF SVM <br> C = 500 <br> gamma = 10  |  Accuracy:0.933108 <br> Precision:0.818182 <br> Recall:0.806604 <br> F1:0.812352| Accuracy:0.899238 <br> Precision:0.746032 <br> Recall:0.665094 <br> F1:0.703242 | Accuracy:0.902625 <br> Precision:0.746193 <br> Recall:0.693396 <br> F1:0.718826 | Accuracy:0.919560 <br> Precision:0.800000 <br> Recall:0.735849 <br> F1:0.766585 
| Random Forest |  Accuracy:0.929721 <br> Precision:0.877193 <br> Recall:0.707547 <br> F1:0.783290| Accuracy:0.922947 <br> Precision:0.823529 <br> Recall:0.726415 <br> F1:0.771930 | Accuracy:0.928874 <br> Precision:0.844086 <br> Recall:0.740566 <br> F1:0.788945 | Accuracy:0.935648 <br> Precision:0.909639 <br> Recall:0.712264 <br> F1:0.798942 

### Meaning of the table columns:

#### Sum of word embeddings:
The document embeddings have been created by simply summing the word embeddings.

#### (Sum)Biased: both weight 10% of doc length:
Just like "(Avg)Biased: both weight 10% of doc length" except word embeddings have been summed.

#### (Sum)Biased: only A weight 10% of doc length:
Just like "(Avg)Biased: only A weight 10% of doc length" except word embeddings have been summed.

#### (Sum)B doc embedding * weight(20):
Just like "(Avg)B doc embedding * weight(20)" except word embeddings have been summed.

|  ![Fasttext](https://fasttext.cc/docs/en/pretrained-vectors.html)  | Sum of word embeddings  
| ------------- |-------------| 
| Logistic Regression  | Accuracy:0.907705 <br> Precision:0.746411 <br> Recall:0.735849 <br> F1:0.741093 
| Linear SVM <br> C = 500     | Accuracy:0.851820 <br> Precision:0.672897 <br> Recall:0.339623 <br> F1:0.451411 
| RBF SVM <br> C = 500 <br> gamma = 10 | Accuracy:0.835732 <br> Precision:0.950000 <br> Recall:0.089623 <br> F1:0.163793 
| Random Forest | Accuracy:0.933108 <br> Precision:0.875706 <br> Recall:0.731132 <br> F1:0.796915

#### How to run:
Execute the first four cells inside Prelearn.ipynb.

Run cell 5 or 6 depending of the test you want to run:  
#### Averaged word embeddings  
Run cell 5 without any change in the code.  
#### Biased: both weight 10% of doc length  
Uncomment the two 'weight = len(B) * word_percent' lines found in the cell 6 of Prelearn.ipynb.  
Run cell 6.  
#### Biased: only A weight 10% of doc length
Run cell 6 without any change in the code.  
#### B doc embedding * weight(20)
Change 'weight_B = 1' to 'weight_B = 20' inside cell 5 of of Prelearn.ipynb.  
Run cell 5.

After you run either cell 5 or 6, run cell 7,8,9,10 to get the results from each of the four classifiers.



