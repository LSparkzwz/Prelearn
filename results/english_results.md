## Prelearn dataset results
<details><summary>Click to expand</summary>
<table>
    <tr>
        <td><b><a href="https://fasttext.cc/docs/en/pretrained-vectors.html">Fasttext</a></b></td>
        <td><b>Averaged word embeddings</b></td>
        <td><b>(Avg)Word frequency</b></td>
        <td><b>(Avg)Biased: both weight 10% of doc length</b></td>
        <td><b>(Avg)Biased: only A weight 10% of doc length</b></td>
        <td><b>(Avg)B doc embedding * weight(20)</b></td>
    </tr>
    <tr>
        <td><b>Logistic Regression</b></td>
        <td>Accuracy:0.851820 <br> Precision:0.849057 <br> Recall:0.212264 <br> F1:0.339623</td>
        <td>Accuracy:0.820491 <br> Precision:0.000000 <br> Recall:0.000000 <br> F1:0.000000</td>
        <td>Accuracy:0.902625 <br> Precision:0.774011 <br> Recall:0.646226 <br> F1:0.704370</td>
        <td>Accuracy:0.849280 <br> Precision:0.702381 <br> Recall:0.278302 <br> F1:0.398649</td>
        <td>Accuracy:0.905165 <br> Precision:0.804878 <br> Recall:0.622642 <br> F1:0.702128</td>
    </tr>
    <tr>
        <td><b>Linear SVM <br> C = 500</b></td>
        <td>Accuracy:0.922100 <br> Precision:0.815789 <br> Recall:0.731132 <br> F1:0.771144</td>
        <td>Accuracy:0.845893 <br> Precision:0.812500 <br> Recall:0.183962 <br> F1:0.300000</td>
        <td>Accuracy:0.899238 <br> Precision:0.683794 <br> Recall:0.816038 <br> F1:0.744086</td>
        <td>Accuracy:0.906012 <br> Precision:0.720524 <br> Recall:0.778302 <br> F1:0.748299</td>
        <td>Accuracy:0.924640 <br> Precision:0.855491 <br> Recall:0.698113 <br> F1:0.768831</td>
    </tr>
    <tr>
        <td><b>RBF SVM <br> C = 500 <br> gamma = 10</b></td>
        <td>Accuracy:0.910246 <br> Precision:0.773196 <br> Recall:0.707547 <br> F1:0.738916</td>
        <td>Accuracy:0.869602 <br> Precision:0.822222 <br> Recall:0.349057 <br> F1:0.490066</td>
        <td>Accuracy:0.878916 <br> Precision:0.810811 <br> Recall:0.424528 <br> F1:0.557276</td>
        <td>Accuracy:0.887384 <br> Precision:0.811024 <br> Recall:0.485849 <br> F1:0.607670</td>
        <td>Accuracy:0.906859 <br> Precision:0.814815 <br> Recall:0.622642 <br> F1:0.705882</td>
    </tr>
    <tr>
        <td><b>Random Forest</b></td>
        <td>Accuracy:0.925487 <br> Precision:0.892405 <br> Recall:0.665094 <br> F1:0.762162</td>
        <td>Accuracy:0.921253 <br> Precision:0.878981 <br> Recall:0.650943 <br> F1:0.747967</td>
        <td>Accuracy:0.920406 <br> Precision:0.797980 <br> Recall:0.745283 <br> F1:0.770732</td>
        <td>Accuracy:0.916173 <br> Precision:0.786802 <br> Recall:0.731132 <br> F1:0.757946</td>
        <td>Accuracy:0.927180 <br> Precision:0.893750 <br> Recall:0.674528 <br> F1:0.768817</td>
    </tr>
</table>
</details>

## CrowdComp dataset results
<details><summary>Click to expand</summary>
<table>
    <tr>
        <td><b><a href="https://fasttext.cc/docs/en/pretrained-vectors.html">Fasttext</a></b></td>
        <td><b>Averaged word embeddings</b></td>
        <td><b>(Avg)Word frequency</b></td>
        <td><b>(Avg)Biased: both weight 10% of doc length</b></td>
        <td><b>(Avg)Biased: only A weight 10% of doc length</b></td>
        <td><b>(Avg)B doc embedding * weight(20)</b></td>
    </tr>
    <tr>
        <td><b>Logistic Regression</b></td>
        <td>Accuracy:0.826 <br> Precision:0.0 <br> Recall:0.0 <br> F1:0.0</td>
        <td>Accuracy:0.826 <br> Precision:0.0 <br> Recall:0.0 <br> F1:0.0</td>
        <td>Accuracy:0.829 <br> Precision:0.6 <br> Recall:0.056 <br> F1:0.102</td>
        <td>Accuracy:0.827 <br> Precision:1.0 <br> Recall:0.009 <br> F1:0.018</td>
        <td>Accuracy:0.806 <br> Precision:0.227 <br> Recall:0.046 <br> F1:0.077</td>
    </tr>
    <tr>
        <td><b>Linear SVM <br> C = 500</b></td>
        <td>Accuracy:0.758 <br> Precision:0.267 <br> Recall:0.222 <br> F1:0.242</td>
        <td>Accuracy:0.817 <br> Precision:0.308 <br> Recall:0.037 <br> F1:0.066</td>
        <td>Accuracy:0.756 <br> Precision:0.283 <br> Recall:0.259 <br> F1:0.271</td>
        <td>Accuracy:0.758 <br> Precision:0.281 <br> Recall:0.25 <br> F1:0.265</td>
        <td>Accuracy:0.793 <br> Precision:0.333 <br> Recall:0.185 <br> F1:0.238</td>
    </tr>
    <tr>
        <td><b>RBF SVM <br> C = 500 <br> gamma = 10</b></td>
        <td>Accuracy:0.787 <br> Precision:0.333 <br> Recall:0.222 <br> F1:0.267</td>
        <td>Accuracy:0.824 <br> Precision:0.4 <br> Recall:0.019 <br> F1:0.035</td>
        <td>Accuracy:0.788 <br> Precision:0.323 <br> Recall:0.194 <br> F1:0.243</td>
        <td>Accuracy:0.787 <br> Precision:0.324 <br> Recall:0.204 <br> F1:0.25</td>
        <td>Accuracy:0.796 <br> Precision:0.235 <br> Recall:0.074 <br> F1:0.113</td>
    </tr>
    <tr>
        <td><b>Random Forest</b></td>
        <td>Accuracy:0.829 <br> Precision:0.536 <br> Recall:0.139 <br> F1:0.221</td>
        <td>Accuracy:0.83 <br> Precision:0.565 <br> Recall:0.12 <br> F1:0.198</td>
        <td>Accuracy:0.83 <br> Precision:0.565 <br> Recall:0.12 <br> F1:0.198</td>
        <td>Accuracy:0.83 <br> Precision:0.565 <br> Recall:0.12 <br> F1:0.198</td>
        <td>Accuracy:0.826 <br> Precision:0.5 <br> Recall:0.13 <br> F1:0.206</td>
    </tr>
</table>
</details> 

## Course dataset results
<details><summary>Click to expand</summary>
<table>
    <tr>
        <td><b><a href="https://fasttext.cc/docs/en/pretrained-vectors.html">Fasttext</a></b></td>
        <td><b>Averaged word embeddings</b></td>
        <td><b>(Avg)Word frequency</b></td>
        <td><b>(Avg)Biased: both weight 10% of doc length</b></td>
        <td><b>(Avg)Biased: only A weight 10% of doc length</b></td>
        <td><b>(Avg)B doc embedding * weight(20)</b></td>
    </tr>
    <tr>
        <td><b>Logistic Regression</b></td>
        <td>Accuracy:0.685185 <br> Precision:0.0 <br> Recall:0.0 <br> F1:0.0</td>
        <td>Accuracy:0.685185 <br> Precision:0.0 <br> Recall:0.0 <br> F1:0.0</td>
        <td>Accuracy:0.666667 <br> Precision:0.0 <br> Recall:0.0 <br> F1:0.0</td>
        <td>Accuracy:0.666667 <br> Precision:0.0 <br> Recall:0.0 <br> F1:0.0</td>
        <td>Accuracy:0.685185 <br> Precision:0.0 <br> Recall:0.0 <br> F1:0.0</td>
    </tr>
    <tr>
        <td><b>Linear SVM <br> C = 500</b></td>
        <td>Accuracy:0.703704 <br> Precision:1.0 <br> Recall:0.058824 <br> F1:0.111111</td>
        <td>Accuracy:0.685185 <br> Precision:0.0 <br> Recall:0.0 <br> F1:0.0</td>
        <td>Accuracy:0.759259 <br> Precision:0.833333 <br> Recall:0.294118 <br> F1:0.434783</td>
        <td>Accuracy:0.703704 <br> Precision:0.666667 <br> Recall:0.117647 <br> F1:0.2</td>
        <td>Accuracy:0.648148 <br> Precision:0.25 <br> Recall:0.058824 <br> F1:0.095238</td>
    </tr>
    <tr>
        <td><b>RBF SVM <br> C = 500 <br> gamma = 10</b></td>
        <td>Accuracy:0.685185 <br> Precision:0.5 <br> Recall:0.058824 <br> F1:0.105263</td>
        <td>Accuracy:0.685185 <br> Precision:0.0 <br> Recall:0.0 <br> F1:0.0</td>
        <td>Accuracy:0.703704 <br> Precision:1.0 <br> Recall:0.058824 <br> F1:0.111111</td>
        <td>Accuracy:0.666667 <br> Precision:0.333333 <br> Recall:0.058824 <br> F1:0.1</td>
        <td>Accuracy:0.703704 <br> Precision:1.0 <br> Recall:0.058824 <br> F1:0.111111</td>
    </tr>
    <tr>
        <td><b>Random Forest</b></td>
        <td>Accuracy:0.703704 <br> Precision:1.0 <br> Recall:0.058824 <br> F1:0.111111</td>
        <td>Accuracy:0.703704 <br> Precision:1.0 <br> Recall:0.058824 <br> F1:0.111111</td>
        <td>Accuracy:0.685185 <br> Precision:0.5 <br> Recall:0.058824 <br> F1:0.105263</td>
        <td>Accuracy:0.703704 <br> Precision:0.666667 <br> Recall:0.117647 <br> F1:0.2</td>
        <td>Accuracy:0.703704 <br> Precision:1.0 <br> Recall:0.058824 <br> F1:0.111111</td>
    </tr>
</table>
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

## Prelearn dataset results
<details><summary>Click to expand</summary>
<table>
    <tr>
        <td><b><a href="https://fasttext.cc/docs/en/pretrained-vectors.html">Fasttext</a></b></td>
        <td><b>Sum of word embeddings</b></td>
        <td><b>(Sum)Word frequency</b></td>
        <td><b>(Sum)Biased: both weight 10% of doc length</b></td>
        <td><b>(Sum)Biased: only A weight 10% of doc length</b></td>
        <td><b>(Sum)B doc embedding * weight(20)</b></td>
    </tr>
    <tr>
        <td><b>Logistic Regression</b></td>
        <td>Accuracy:0.911939 <br> Precision:0.752336 <br> Recall:0.759434 <br> F1:0.755869</td>
        <td>Accuracy:0.917019 <br> Precision:0.806452 <br> Recall:0.707547 <br> F1:0.753769</td>
        <td>Accuracy:0.902625 <br> Precision:0.715556 <br> Recall:0.759434 <br> F1:0.736842</td>
        <td>Accuracy:0.894157 <br> Precision:0.682008 <br> Recall:0.768868 <br> F1:0.722838</td>
        <td>Accuracy:0.923793 <br> Precision:0.801980 <br> Recall:0.764151 <br> F1:0.782609</td>
    </tr>
    <tr>
        <td><b>Linear SVM <br> C = 500</b></td>
        <td>Accuracy:0.884843 <br> Precision:0.787879 <br> Recall:0.490566 <br> F1:0.604651</td>
        <td>Accuracy:0.857748 <br> Precision:0.600917 <br> Recall:0.617925 <br> F1:0.609302</td>
        <td>Accuracy:0.840813 <br> Precision:0.544776 <br> Recall:0.688679 <br> F1:0.608333</td>
        <td>Accuracy:0.868755 <br> Precision:0.647668 <br> Recall:0.589623 <br> F1:0.617284</td>
        <td>Accuracy:0.892464 <br> Precision:0.692308 <br> Recall:0.721698 <br> F1:0.706697</td>
    </tr>
    <tr>
        <td><b>RBF SVM <br> C = 500 <br> gamma = 10</b></td>
        <td>Accuracy:0.835732 <br> Precision:0.950000 <br> Recall:0.089623 <br> F1:0.163793</td>
        <td>Accuracy:0.835732 <br> Precision:0.950000 <br> Recall:0.089623 <br> F1:0.163793</td>
        <td>Accuracy:0.835732 <br> Precision:0.950000 <br> Recall:0.089623 <br> F1:0.163793</td>
        <td>Accuracy:0.835732 <br> Precision:0.950000 <br> Recall:0.089623 <br> F1:0.163793</td>
        <td>Accuracy:0.835732 <br> Precision:0.950000 <br> Recall:0.089623 <br> F1:0.163793</td>
    </tr>
    <tr>
        <td><b>Random Forest</b></td>
        <td>Accuracy:0.930567 <br> Precision:0.891566 <br> Recall:0.698113 <br> F1:0.783069</td>
        <td>Accuracy:0.922100 <br> Precision:0.861446 <br> Recall:0.674528 <br> F1:0.756614</td>
        <td>Accuracy:0.915326 <br> Precision:0.791667 <br> Recall:0.716981 <br> F1:0.752475</td>
        <td>Accuracy:0.915326 <br> Precision:0.791667 <br> Recall:0.716981 <br> F1:0.752475</td>
        <td>Accuracy:0.922100 <br> Precision:0.870370 <br> Recall:0.665094 <br> F1:0.754011</td>
    </tr>
</table>
</details>

## CrowdComp dataset results
<details><summary>Click to expand</summary>
<table>
    <tr>
        <td><b><a href="https://fasttext.cc/docs/en/pretrained-vectors.html">Fasttext</a></b></td>
        <td><b>Sum of word embeddings</b></td>
        <td><b>(Sum)Word frequency</b></td>
        <td><b>(Sum)Biased: both weight 10% of doc length</b></td>
        <td><b>(Sum)Biased: only A weight 10% of doc length</b></td>
        <td><b>(Sum)B doc embedding * weight(20)</b></td>
    </tr>
    <tr>
        <td><b>Logistic Regression</b></td>
        <td>Accuracy:0.733 <br> Precision:0.282 <br> Recall:0.343 <br> F1:0.31</td>
        <td>Accuracy:0.817 <br> Precision:0.439 <br> Recall:0.167 <br> F1:0.242</td>
        <td>Accuracy:0.766 <br> Precision:0.32 <br> Recall:0.306 <br> F1:0.313</td>
        <td>Accuracy:0.714 <br> Precision:0.248 <br> Recall:0.315 <br> F1:0.278</td>
        <td>Accuracy:0.769 <br> Precision:0.316 <br> Recall:0.278 <br> F1:0.296</td>
    </tr>
    <tr>
        <td><b>Linear SVM <br> C = 500</b></td>
        <td>Accuracy:0.711 <br> Precision:0.248 <br> Recall:0.324 <br> F1:0.281</td>
        <td>Accuracy:0.733 <br> Precision:0.279 <br> Recall:0.333 <br> F1:0.304</td>
        <td>Accuracy:0.67 <br> Precision:0.221 <br> Recall:0.352 <br> F1:0.271</td>
        <td>Accuracy:0.74 <br> Precision:0.274 <br> Recall:0.296 <br> F1:0.284</td>
        <td>Accuracy:0.679 <br> Precision:0.206 <br> Recall:0.296 <br> F1:0.243</td>
    </tr>
    <tr>
        <td><b>RBF SVM <br> C = 500 <br> gamma = 10</b></td>
        <td>Accuracy:0.829 <br> Precision:0.75 <br> Recall:0.028 <br> F1:0.054</td>
        <td>Accuracy:0.822 <br> Precision:0.375 <br> Recall:0.028 <br> F1:0.052</td>
        <td>Accuracy:0.822 <br> Precision:0.333 <br> Recall:0.019 <br> F1:0.035</td>
        <td>Accuracy:0.827 <br> Precision:0.667 <br> Recall:0.019 <br> F1:0.036</td>
        <td>Accuracy:0.829 <br> Precision:0.75 <br> Recall:0.028 <br> F1:0.054</td>
    </tr>
    <tr>
        <td><b>Random Forest</b></td>
        <td>Accuracy:0.83 <br> Precision:0.571 <br> Recall:0.111 <br> F1:0.186</td>
        <td>Accuracy:0.827 <br> Precision:0.529 <br> Recall:0.083 <br> F1:0.144</td>
        <td>Accuracy:0.826 <br> Precision:0.5 <br> Recall:0.139 <br> F1:0.217</td>
        <td>Accuracy:0.83 <br> Precision:0.56 <br> Recall:0.13 <br> F1:0.211</td>
        <td>Accuracy:0.829 <br> Precision:0.545 <br> Recall:0.111 <br> F1:0.185</td>
    </tr>
</table>
</details> 

## Course dataset results
<details><summary>Click to expand</summary>
<table>
    <tr>
        <td><b><a href="https://fasttext.cc/docs/en/pretrained-vectors.html">Fasttext</a></b></td>
        <td><b>Sum of word embeddings</b></td>
        <td><b>(Sum)Word frequency</b></td>
        <td><b>(Sum)Biased: both weight 10% of doc length</b></td>
        <td><b>(Sum)Biased: only A weight 10% of doc length</b></td>
        <td><b>(Sum)B doc embedding * weight(20)</b></td>
    </tr>
    <tr>
        <td><b>Logistic Regression</b></td>
        <td>Accuracy:0.733 <br> Precision:0.282 <br> Recall:0.343 <br> F1:0.31</td>
        <td>Accuracy:0.817 <br> Precision:0.439 <br> Recall:0.167 <br> F1:0.242</td>
        <td>Accuracy:0.766 <br> Precision:0.32 <br> Recall:0.306 <br> F1:0.313</td>
        <td>Accuracy:0.714 <br> Precision:0.248 <br> Recall:0.315 <br> F1:0.278</td>
        <td>Accuracy:0.769 <br> Precision:0.316 <br> Recall:0.278 <br> F1:0.296</td>
    </tr>
    <tr>
        <td><b>Linear SVM <br> C = 500</b></td>
        <td>Accuracy:0.711 <br> Precision:0.248 <br> Recall:0.324 <br> F1:0.281</td>
        <td>Accuracy:0.733 <br> Precision:0.279 <br> Recall:0.333 <br> F1:0.304</td>
        <td>Accuracy:0.67 <br> Precision:0.221 <br> Recall:0.352 <br> F1:0.271</td>
        <td>Accuracy:0.74 <br> Precision:0.274 <br> Recall:0.296 <br> F1:0.284</td>
        <td>Accuracy:0.679 <br> Precision:0.206 <br> Recall:0.296 <br> F1:0.243</td>
    </tr>
    <tr>
        <td><b>RBF SVM <br> C = 500 <br> gamma = 10</b></td>
        <td>Accuracy:0.829 <br> Precision:0.75 <br> Recall:0.028 <br> F1:0.054</td>
        <td>Accuracy:0.822 <br> Precision:0.375 <br> Recall:0.028 <br> F1:0.052</td>
        <td>Accuracy:0.822 <br> Precision:0.333 <br> Recall:0.019 <br> F1:0.035</td>
        <td>Accuracy:0.827 <br> Precision:0.667 <br> Recall:0.019 <br> F1:0.036</td>
        <td>Accuracy:0.829 <br> Precision:0.75 <br> Recall:0.028 <br> F1:0.054</td>
    </tr>
    <tr>
        <td><b>Random Forest</b></td>
        <td>Accuracy:0.83 <br> Precision:0.571 <br> Recall:0.111 <br> F1:0.186</td>
        <td>Accuracy:0.827 <br> Precision:0.529 <br> Recall:0.083 <br> F1:0.144</td>
        <td>Accuracy:0.826 <br> Precision:0.5 <br> Recall:0.139 <br> F1:0.217</td>
        <td>Accuracy:0.83 <br> Precision:0.56 <br> Recall:0.13 <br> F1:0.211</td>
        <td>Accuracy:0.829 <br> Precision:0.545 <br> Recall:0.111 <br> F1:0.185</td>
    </tr>
</table>
</details>

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




