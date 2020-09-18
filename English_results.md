|  ![Fasttext](https://fasttext.cc/docs/en/pretrained-vectors.html)  | Sum of word embeddings | (Sum)Word frequency | (Sum)Biased: both weight 10% of doc length | (Sum)Biased: only A weight 10% of doc length | (Sum)B doc embedding * weight(20) 
| ------------- |-------------| -----------------| ----|---- | ---- | 
| Logistic Regression  | Accuracy:0.911939 <br> Precision:0.752336 <br> Recall:0.759434 <br> F1:0.755869 | Accuracy:0.917019 <br> Precision:0.806452 <br> Recall:0.707547 <br> F1:0.753769
| Linear SVM <br> C = 500     | Accuracy:0.884843 <br> Precision:0.787879 <br> Recall:0.490566 <br> F1:0.604651 | Accuracy:0.857748 <br> Precision:0.600917 <br> Recall:0.617925 <br> F1:0.609302
| RBF SVM <br> C = 500 <br> gamma = 10  | Accuracy:0.835732 <br> Precision:0.950000 <br> Recall:0.089623 <br> F1:0.163793 | Accuracy:0.835732 <br> Precision:0.950000 <br> Recall:0.089623 <br> F1:0.163793
| Random Forest | Accuracy:0.930567 <br> Precision:0.891566 <br> Recall:0.698113 <br> F1:0.783069 | Accuracy:0.922100 <br> Precision:0.861446 <br> Recall:0.674528 <br> F1:0.756614
