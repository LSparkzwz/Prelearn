## First approach: 
The first approach is straightforward, the binary classifiers are trained with a dataset where each row corresponds to a pair of word document embeddings and a variable that's 1 if the second document embedding is a prerequisite of the first one and 0 otherwise.  
The validation scores are then calculated by comparing the results given by the classifier with the ground truth.  

In this approach different classifiers and different datasets in which document embeddings have been created differently have been tested. Also two languages have been tested: Italian and English.

#### How the datasets have been created: 
The starting dataset has been requested from here: https://sites.google.com/view/prelearn20/data?authuser=0 . 
This dataset consist of pairs of target and prerequisite concepts (A, B), labelled as follows:  
* 1 if B is a prerequisite of A;  
* 0 in all other cases.

Furthermore, the dataset offered by Prelearn is split in different files for each subject: geometry, physics, data mining and precalculus. 
These files have been combined in order to obtain a single bigger dataset. 

Since the prerequisite concepts (A,B) right now consist of just titles (ex. "Light"), these titles have been replaced by their respective Wikipedia pages through the use of [Wikipedia-API](https://pypi.org/project/Wikipedia-API/). So now the dataset has the following structure:  
* Title of A + Wikipedia page of A, Title of B + Wikipedia page of B, 0 or 1. 

Each document now gets cleaned so it's easier to create word embeddings with them, this is done by using the [NLTK](https://www.nltk.org/) library. 
The cleaning process consists in: 
* Tokenization.
* Conversion to lower case. 
* Removal of punctuation. 
* Removal of stop words.  

Each concept A and B therefore gets transformed into an array of tokens. Each token gets then transformed into a word embedding which have been obtained using the respective Italian or English [FastText model](https://fasttext.cc/docs/en/pretrained-vectors.html). The word embeddings obtained have 300 dimensions.

After this each concept A and B gets transformed into a document embedding so that the structure becomes:  
* Document Embedding of A, Document Embedding of B, 0 or 1. 

The documents embeddings have been obtained in ten different ways, thus creating 10 different datasets: 
* Sum of word embeddings. 
* Averaged word embeddings. 
* Sum/Average of word embeddings weighted by term frequency. 
* Sum/Average of word embeddings in which words that appear inside the title of B are given a weight equal to 10% of their document (A or B) length.
* Same as above but the weight is only given to words inside the document A, while B stays the same as what you'd obtain with just a sum or average.
* Sum/Average of word embeddings in which the B document embedding has been multipled by a weight equal to 20, A instead stays the same as what you'd obtain with just a sum or average.  

The document embeddings obtained have 300 dimensions.  
Once the different datasets have been obtained the datasets gets split randomically into a 80/20 training set and validation set pair.  
Finally each binary classifier is trained by giving them the two document embeddings as X (which has 300 + 300 dimensions where each dimension equals to one dimension of the document embeddings) and their respective 0 or 1 as Y.

### Document Embeddings and results: 
Further explainations on the document embeddings and the validation results tested on different classifiers can be seen here: 
* [Italian Results](https://github.com/LSparkzwz/Prelearn/blob/master/results/italian_results.md)
* [English Results](https://github.com/LSparkzwz/Prelearn/blob/master/results/english_results.md)

### How to run (Italian version): 
* Request the starting dataset here: https://docs.google.com/forms/d/e/1FAIpQLSdz4q7H7Savij_HGV2YDwZrBP5KUIWU4vRfkcHAnsdKJ4xvxw/viewform .
* From terminal run: `cat data_mining-pairs_train.csv geometry-pairs_train.csv physics-pairs_train.csv precalculus-pairs_train.csv > train.csv`
* Rename `ITA_prereq-pages.xml` to `dataset.xml`
* Upload `train.csv` and `dataset.xml` to the root of "My Drive" of your Google Drive.
* Run every cell in [init_it.ipynb](https://github.com/LSparkzwz/Prelearn/blob/master/init_it.ipynb).
* Depending on the document embedding that you want to use, run every cell inside its respective ipnyb:
  * [Sum of word embeddings.](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/sum/we_sum.ipynb)
  * [Averaged word embeddings.](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/average/we_average.ipynb) 
  * [Sum](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/sum/we_word_frequency.ipynb)/[Average](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/average/we_word_frequency.ipynb) of word embeddings weighted by term frequency. 
  * [Sum](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/sum/we_biased_AB.ipynb)/[Average](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/average/we_biased_AB.ipynb) of word embeddings in which words that appear inside the title of B are given a weight equal to 10% of their document (A or B) length.
  * ([Sum](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/sum/we_biased_A.ipynb)/[Average](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/average/we_biased_A.ipynb)) Same as above but the weight is only given to words inside the document A, while B stays the same as what you'd obtain with just a sum or average.
  * [Sum](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/sum/we_B_weight.ipynb)/[Average](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/average/we_B_weight.ipynb) of word embeddings in which the B document embedding has been multipled by a weight equal to 20, A instead stays the same as what you'd obtain with just a sum or average.  
* Run every cell inside [classifiers.ipynb](https://github.com/LSparkzwz/Prelearn/blob/master/classifiers.ipynb).

### How to run (English version): 
* Request the starting dataset here: https://docs.google.com/forms/d/e/1FAIpQLSdz4q7H7Savij_HGV2YDwZrBP5KUIWU4vRfkcHAnsdKJ4xvxw/viewform .
* From terminal run: `cat data_mining-pairs_train.csv geometry-pairs_train.csv physics-pairs_train.csv precalculus-pairs_train.csv > train.csv`
* Rename `ITA_prereq-pages.xml` to `dataset.xml`
* Upload `train.csv` and `dataset.xml` to the root of "My Drive" of your Google Drive.
* Run every cell in [init_en.ipynb](https://github.com/LSparkzwz/Prelearn/blob/master/init_en.ipynb).
* Depending on the document embedding that you want to use, run every cell inside its respective ipnyb:
  * [Sum of word embeddings.](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_sum.ipynb)
  * [Averaged word embeddings.](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_average.ipynb) 
  * [Sum](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_word_frequency.ipynb)/[Average](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_word_frequency.ipynb) of word embeddings weighted by term frequency. 
  * [Sum](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_biased_AB.ipynb)/[Average](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_biased_AB.ipynb) of word embeddings in which words that appear inside the title of B are given a weight equal to 10% of their document (A or B) length.
  * ([Sum](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_biased_A.ipynb)/[Average](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_biased_A.ipynb)) Same as above but the weight is only given to words inside the document A, while B stays the same as what you'd obtain with just a sum or average.
  * [Sum](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_B_weight.ipynb)/[Average](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_B_weight.ipynb) of word embeddings in which the B document embedding has been multipled by a weight equal to 20, A instead stays the same as what you'd obtain with just a sum or average.  
* Run every cell inside [classifiers.ipynb](https://github.com/LSparkzwz/Prelearn/blob/master/classifiers.ipynb).
