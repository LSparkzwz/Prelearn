|  ![Fasttext](https://fasttext.cc/docs/en/pretrained-vectors.html)  | Averaged word embeddings | (Avg)Word frequency   | (Avg)Biased: both weight 10% of doc length  | (Avg)Biased: only A weight 10% of doc length | (Avg)B doc embedding * weight(20) 
| ------------- |-------------| -----------------| ----|---- | ---- | 
| Logistic Regression  | Accuracy:0.911939 <br> Precision:0.752336 <br> Recall:0.759434 <br> F1:0.755869
| Linear SVM <br> C = 500     | Accuracy:0.884843 <br> Precision:0.787879 <br> Recall:0.490566 <br> F1:0.604651
| RBF SVM <br> C = 500 <br> gamma = 10  | Accuracy:0.835732 <br> Precision:0.950000 <br> Recall:0.089623 <br> F1:0.163793
| Random Forest | Accuracy:0.930567 <br> Precision:0.891566 <br> Recall:0.698113 <br> F1:0.783069
