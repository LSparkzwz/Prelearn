<details><summary>Prelearn results</summary>
|  ![Fasttext](https://fasttext.cc/docs/en/pretrained-vectors.html)  | Averaged word embeddings | (Avg)Word frequency   | (Avg)Biased: both weight 10% of doc length  | (Avg)Biased: only A weight 10% of doc length | (Avg)B doc embedding * weight(20) 
| ------------- |-------------| -----------------| ----|---- | ---- | 
| Logistic Regression  | Accuracy:0.851820 <br> Precision:0.849057 <br> Recall:0.212264 <br> F1:0.339623 | Accuracy:0.820491 <br> Precision:0.000000 <br> Recall:0.000000 <br> F1:0.000000 | Accuracy:0.902625 <br> Precision:0.774011 <br> Recall:0.646226 <br> F1:0.704370 | Accuracy:0.849280 <br> Precision:0.702381 <br> Recall:0.278302 <br> F1:0.398649 | Accuracy:0.905165 <br> Precision:0.804878 <br> Recall:0.622642 <br> F1:0.702128
| Linear SVM <br> C = 500 | Accuracy:0.922100 <br> Precision:0.815789 <br> Recall:0.731132 <br> F1:0.771144 | Accuracy:0.845893 <br> Precision:0.812500 <br> Recall:0.183962 <br> F1:0.300000 | Accuracy:0.899238 <br> Precision:0.683794 <br> Recall:0.816038 <br> F1:0.744086 | Accuracy:0.906012 <br> Precision:0.720524 <br> Recall:0.778302 <br> F1:0.748299 | Accuracy:0.924640 <br> Precision:0.855491 <br> Recall:0.698113 <br> F1:0.768831
| RBF SVM <br> C = 500 <br> gamma = 10  | Accuracy:0.910246 <br> Precision:0.773196 <br> Recall:0.707547 <br> F1:0.738916 | Accuracy:0.869602 <br> Precision:0.822222 <br> Recall:0.349057 <br> F1:0.490066 | Accuracy:0.878916 <br> Precision:0.810811 <br> Recall:0.424528 <br> F1:0.557276 | Accuracy:0.887384 <br> Precision:0.811024 <br> Recall:0.485849 <br> F1:0.607670 | Accuracy:0.906859 <br> Precision:0.814815 <br> Recall:0.622642 <br> F1:0.705882
| Random Forest | Accuracy:0.925487 <br> Precision:0.892405 <br> Recall:0.665094 <br> F1:0.762162 | Accuracy:0.921253 <br> Precision:0.878981 <br> Recall:0.650943 <br> F1:0.747967 | Accuracy:0.920406 <br> Precision:0.797980 <br> Recall:0.745283 <br> F1:0.770732 | Accuracy:0.916173 <br> Precision:0.786802 <br> Recall:0.731132 <br> F1:0.757946 | Accuracy:0.927180 <br> Precision:0.893750 <br> Recall:0.674528 <br> F1:0.768817
</details>
  
### Meaning of the table columns:

#### Averaged word embeddings:
The document embeddings have been created by averaging the word embeddings.

#### (Avg)Word frequency:
The document embeddings have been created by averaging the word embeddings while giving each word embedding a weight equal to their term frequency inside their respective document.

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


|  ![Fasttext](https://fasttext.cc/docs/en/pretrained-vectors.html)  | Sum of word embeddings | (Sum)Word frequency | (Sum)Biased: both weight 10% of doc length | (Sum)Biased: only A weight 10% of doc length | (Sum)B doc embedding * weight(20) 
| ------------- |-------------| -----------------| ----|---- | ---- | 
| Logistic Regression  | Accuracy:0.911939 <br> Precision:0.752336 <br> Recall:0.759434 <br> F1:0.755869 | Accuracy:0.917019 <br> Precision:0.806452 <br> Recall:0.707547 <br> F1:0.753769 | Accuracy:0.902625 <br> Precision:0.715556 <br> Recall:0.759434 <br> F1:0.736842 | Accuracy:0.894157 <br> Precision:0.682008 <br> Recall:0.768868 <br> F1:0.722838 | Accuracy:0.923793 <br> Precision:0.801980 <br> Recall:0.764151 <br> F1:0.782609
| Linear SVM <br> C = 500     | Accuracy:0.884843 <br> Precision:0.787879 <br> Recall:0.490566 <br> F1:0.604651 | Accuracy:0.857748 <br> Precision:0.600917 <br> Recall:0.617925 <br> F1:0.609302 | Accuracy:0.840813 <br> Precision:0.544776 <br> Recall:0.688679 <br> F1:0.608333 | Accuracy:0.868755 <br> Precision:0.647668 <br> Recall:0.589623 <br> F1:0.617284 | Accuracy:0.892464 <br> Precision:0.692308 <br> Recall:0.721698 <br> F1:0.706697
| RBF SVM <br> C = 500 <br> gamma = 10  | Accuracy:0.835732 <br> Precision:0.950000 <br> Recall:0.089623 <br> F1:0.163793 | Accuracy:0.835732 <br> Precision:0.950000 <br> Recall:0.089623 <br> F1:0.163793 | Accuracy:0.835732 <br> Precision:0.950000 <br> Recall:0.089623 <br> F1:0.163793 | Accuracy:0.835732 <br> Precision:0.950000 <br> Recall:0.089623 <br> F1:0.163793 | Accuracy:0.835732 <br> Precision:0.950000 <br> Recall:0.089623 <br> F1:0.163793
| Random Forest | Accuracy:0.930567 <br> Precision:0.891566 <br> Recall:0.698113 <br> F1:0.783069 | Accuracy:0.922100 <br> Precision:0.861446 <br> Recall:0.674528 <br> F1:0.756614 | Accuracy:0.915326 <br> Precision:0.791667 <br> Recall:0.716981 <br> F1:0.752475 | Accuracy:0.915326 <br> Precision:0.791667 <br> Recall:0.716981 <br> F1:0.752475 | Accuracy:0.922100 <br> Precision:0.870370 <br> Recall:0.665094 <br> F1:0.754011

### Meaning of the table columns:

#### Sum of word embeddings:
The document embeddings have been created by simply summing the word embeddings.

#### (Sum)Word frequency:
Just like "(Avg)Word frequency" except word embeddings have been summed.

#### (Sum)Biased: both weight 10% of doc length:
Just like "(Avg)Biased: both weight 10% of doc length" except word embeddings have been summed.

#### (Sum)Biased: only A weight 10% of doc length:
Just like "(Avg)Biased: only A weight 10% of doc length" except word embeddings have been summed.

#### (Sum)B doc embedding * weight(20):
Just like "(Avg)B doc embedding * weight(20)" except word embeddings have been summed.



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




