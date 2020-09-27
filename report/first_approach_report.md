## First approach: 
The first approach is straightforward, the binary classifiers are trained with a dataset where each row corresponds to a pair of word document embeddings and a variable that's 1 if the second document embedding is a prerequisite of the first one and 0 otherwise.  
The validation scores are then calculated by comparing the results given by the classifier with the ground truth.  

In this approach different classifiers and different datasets in which document embeddings have been created differently have been tested. Also two languages have been tested: Italian and English.

### How the datasets have been created: 

Each dataset has a different structure, therefore they all get first transformed into datasets with the same structure so that document embeddings can be created without compatibility problems:

#### Prelearn dataset:
<details><summary>Click here to expand</summary>
The starting dataset has been requested from here: https://sites.google.com/view/prelearn20/data?authuser=0 . <br>
This dataset consist of pairs of target and prerequisite concepts (A, B), labelled as follows: <br> <br>
<lu>
<li> 1 if B is a prerequisite of A; </li>
<li> 0 in all other cases. </li>
</lu> <br>
Furthermore, the dataset offered by Prelearn is split in different files for each subject: geometry, physics, data mining and precalculus. <br>
These files have been combined in order to obtain a single bigger dataset. <br> <br>

Since the prerequisite concepts (A,B) right now consist of just titles (ex. "Light"), these titles have been replaced by their respective Wikipedia pages through the use of [Wikipedia-API](https://pypi.org/project/Wikipedia-API/). So now the dataset has the following structure: <br> 
<lu>
<li> Title of A + Wikipedia page of A, Title of B + Wikipedia page of B, 0 or 1. </li>
</lu>
</details>

#### CrowdComp dataset:
<details><summary>Click here to expand</summary>
The starting dataset has been downloaded from here: https://github.com/harrylclc/RefD-dataset . <br>
Each row of this dataset represents a vote that expresses the relationship between two concepts A and B. <br><br>
<lu>
<li> A is prerequisite of B. </li>
<li> B is prerequisite of A. </li>
<li> other (there's no prerequisite). </li>
</lu><br>
Each pair A, B can have multiple votes given by different people, for example two people say there's no prerequisite while a third one says A is prerequisite of B. <br>

This dataset has been transformed so that it follows the A,B,0/1 Prelearn structure, where 0/1 is given according to the answer that relationship that received most votes. <br>

Since the prerequisite concepts (A,B) right now consist of just titles (ex. "Light"), these titles have been replaced by their respective Wikipedia pages through the use of [Wikipedia-API](https://pypi.org/project/Wikipedia-API/). So now the dataset has the following structure: <br> 

<lu>
<li> Title of A + Wikipedia page of A, Title of B + Wikipedia page of B, 0 or 1. </li>
</lu>
</details> 

#### Course dataset: 

<details><summary>Click here to expand</summary>
The starting dataset has been downloaded from here: https://github.com/harrylclc/RefD-dataset . <br>

This dataset already follows the A,B,0/1 Prelearn structure on a conceptual level, it just needed a translation on the implementation level.  <br>

Since the prerequisite concepts (A,B) right now consist of just titles (ex. "Light"), these titles have been replaced by their respective Wikipedia pages through the use of [Wikipedia-API](https://pypi.org/project/Wikipedia-API/). So now the dataset has the following structure: <br> 

<lu>
<li> Title of A + Wikipedia page of A, Title of B + Wikipedia page of B, 0 or 1. </li>
</lu>

</details>

#### Udacity + edX dataset: 

<details><summary>Click here to expand</summary>
The starting dataset has been requested from here: http://ai-lab-03.dia.uniroma3.it/datasets/lm2016/ . <br>

This dataset already follows the A,B,0/1 Prelearn structure on a conceptual level, it just needed a translation on the implementation level.  <br>

This dataset doesn't use Wikipedia pages, instead it use files containing the subtitles from Udacity and edX courses. So each title A and B gets replaced with its respective subtitle file so that the dataset follows the following structure:<br> 

<lu>
<li> Udacity/edX subtitles of A, Udacity/edX subtitles of B, 0 or 1. </li>
</lu>

</details>

#### Burst dataset: 

<details><summary>Click here to expand</summary>

The starting dataset has been downloaded from here: 
https://github.com/Teldh/PRET/tree/master/app/datasets . <br>

This dataset follows a vote structure similar to the CrowdComp dataset, this has been translated to the A,B,0/1 Prelearn structure.  <br>

This dataset doesn't use Wikipedia pages, instead it use a single text file containing a text in which every term from the prerequisite dataset appears. Since we don't have real pages for each term here we take the 15 words that appear before each term and the 15 words that appear after each term in order to determinate its context (if a word appears n times n(15+15) words are taken in order to build the context). After doing so the dataset obtains the following structure:<br> 

<lu>
<li> Context of term A, Context of term A, 0 or 1. </li>
</lu>

 
 
</details> 

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


### How to run (English version): 

* Choose what dataset you'd like to test by clicking its option:
<details><summary>Prelearn dataset</summary>
<p>
<ul>
<li> Request the starting dataset here: https://docs.google.com/forms/d/e/1FAIpQLSdz4q7H7Savij_HGV2YDwZrBP5KUIWU4vRfkcHAnsdKJ4xvxw/viewform . </li>
<li> From terminal run: <code>cat data_mining-pairs_train.csv geometry-pairs_train.csv physics-pairs_train.csv precalculus-pairs_train.csv > train.csv</code> </li>
<li> Rename <code>ITA_prereq-pages.xml</code> to <code>dataset.xml</code> </li>
<li> Upload <code>train.csv</code> and <code>dataset.xml</code> to the root of "My Drive" of your Google Drive. </li>
<li> Run every cell in <a href="https://github.com/LSparkzwz/Prelearn/blob/master/init_en.ipynb">init_en.ipynb</a>. </li>
 <li> Run every cell in <a href="https://github.com/LSparkzwz/Prelearn/blob/master/dataset_init/prelearn/dataset_init_en.ipynb">dataset_init_en.ipynb</a>. </li>
<li> Pick one type of word embedding you'd like to try from the following list, and run every cell inside its respective ipnyb: <ul> 
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_sum.ipynb">Sum of word embeddings.</a> </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_average.ipynb">Averaged word embeddings.</a> </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_word_frequency.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_word_frequency.ipynb">Average</a> of word embeddings weighted by term frequency. </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_biased_AB.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_biased_AB.ipynb">Average</a> of word embeddings in which words that appear inside the title of B are given a weight equal to 10% of their document (A or B) length. </li>
  <li> (<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_biased_A.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_biased_A.ipynb">Average</a>) Same as above but the weight is only given to words inside the document A, while B stays the same as what you'd obtain with just a sum or average. </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_B_weight.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_B_weight.ipynb">Average</a> of word embeddings in which the B document embedding has been multipled by a weight equal to 20, A instead stays the same as what you'd obtain with just a sum or average. </li> 
</ul> </li>
<li> Run every cell inside <a href="https://github.com/LSparkzwz/Prelearn/blob/master/classifiers.ipynb">classifiers.ipynb</a>.
</ul> 
 </p>
 </details>
 <details><summary>CrowdComp dataset</summary>
<p>
<ul>
<li> Download the dataset as zip from: https://github.com/harrylclc/RefD-dataset . </li>
<li> Extract the zip: you should have a folder called <code>RefD-dataset-master</code> </li>
<li> Upload <code>RefD-dataset-master</code> to the root of "My Drive" of your Google Drive. </li>
<li> Run every cell in <a href="https://github.com/LSparkzwz/Prelearn/blob/master/init_en.ipynb">init_en.ipynb</a>. </li>
<li> Run every cell in <a href="https://github.com/LSparkzwz/Prelearn/blob/master/dataset_init/crowdComp/dataset_init_en.ipynb">dataset_init_en.ipynb</a>. </li>
<li> Pick one type of word embedding you'd like to try from the following list, and run every cell inside its respective ipnyb: <ul> 
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_sum.ipynb">Sum of word embeddings.</a> </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_average.ipynb">Averaged word embeddings.</a> </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_word_frequency.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_word_frequency.ipynb">Average</a> of word embeddings weighted by term frequency. </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_biased_AB.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_biased_AB.ipynb">Average</a> of word embeddings in which words that appear inside the title of B are given a weight equal to 10% of their document (A or B) length. </li>
  <li> (<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_biased_A.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_biased_A.ipynb">Average</a>) Same as above but the weight is only given to words inside the document A, while B stays the same as what you'd obtain with just a sum or average. </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_B_weight.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_B_weight.ipynb">Average</a> of word embeddings in which the B document embedding has been multipled by a weight equal to 20, A instead stays the same as what you'd obtain with just a sum or average. </li> 
</ul> </li>
<li> Run every cell inside <a href="https://github.com/LSparkzwz/Prelearn/blob/master/classifiers.ipynb">classifiers.ipynb</a>.
</ul> 
 </p>
 </details>
<details><summary>Course dataset</summary>
<p>
<ul>
<li> Download the dataset as zip from: https://github.com/harrylclc/RefD-dataset . </li>
<li> Extract the zip: you should have a folder called <code>RefD-dataset-master</code> </li>
<li> Upload <code>RefD-dataset-master</code> to the root of "My Drive" of your Google Drive. </li>
<li> Run every cell in <a href="https://github.com/LSparkzwz/Prelearn/blob/master/init_en.ipynb">init_en.ipynb</a>. </li>
<li> Run every cell in <a href="https://github.com/LSparkzwz/Prelearn/blob/master/dataset_init/course/dataset_init_en.ipynb">dataset_init_en.ipynb</a>. </li>
<li> Pick one type of word embedding you'd like to try from the following list, and run every cell inside its respective ipnyb: <ul> 
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_sum.ipynb">Sum of word embeddings.</a> </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_average.ipynb">Averaged word embeddings.</a> </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_word_frequency.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_word_frequency.ipynb">Average</a> of word embeddings weighted by term frequency. </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_biased_AB.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_biased_AB.ipynb">Average</a> of word embeddings in which words that appear inside the title of B are given a weight equal to 10% of their document (A or B) length. </li>
  <li> (<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_biased_A.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_biased_A.ipynb">Average</a>) Same as above but the weight is only given to words inside the document A, while B stays the same as what you'd obtain with just a sum or average. </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_B_weight.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_B_weight.ipynb">Average</a> of word embeddings in which the B document embedding has been multipled by a weight equal to 20, A instead stays the same as what you'd obtain with just a sum or average. </li> 
</ul> </li>
<li> Run every cell inside <a href="https://github.com/LSparkzwz/Prelearn/blob/master/classifiers.ipynb">classifiers.ipynb</a>.
</ul> 
</p>
</details>
<details><summary>Udacity + edX dataset</summary>
<p>
<ul>
<li> Request the dataset (you need the subtitles too, not just the prerequisites!) as zip from: http://ai-lab-03.dia.uniroma3.it/datasets/lm2016/ . </li>
<li> Extract the zip: you should have a folder called <code>edX-Udacity-dataset</code> </li>
<li> Upload <code>edX-Udacity-dataset</code> to the root of "My Drive" of your Google Drive. </li>
<li> Run every cell in <a href="https://github.com/LSparkzwz/Prelearn/blob/master/init_en.ipynb">init_en.ipynb</a>. </li>
<li> Run every cell in <a href="https://github.com/LSparkzwz/Prelearn/blob/master/dataset_init/udacity%20edx/dataset_init_en.ipynb">dataset_init_en.ipynb</a>. </li>
<li> Pick one type of word embedding you'd like to try from the following list, and run every cell inside its respective ipnyb: <ul> 
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_sum.ipynb">Sum of word embeddings.</a> </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_average.ipynb">Averaged word embeddings.</a> </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_word_frequency.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_word_frequency.ipynb">Average</a> of word embeddings weighted by term frequency. </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_biased_AB.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_biased_AB.ipynb">Average</a> of word embeddings in which words that appear inside the title of B are given a weight equal to 10% of their document (A or B) length. </li>
  <li> (<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_biased_A.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_biased_A.ipynb">Average</a>) Same as above but the weight is only given to words inside the document A, while B stays the same as what you'd obtain with just a sum or average. </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_B_weight.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_B_weight.ipynb">Average</a> of word embeddings in which the B document embedding has been multipled by a weight equal to 20, A instead stays the same as what you'd obtain with just a sum or average. </li> 
</ul> </li>
<li> Run every cell inside <a href="https://github.com/LSparkzwz/Prelearn/blob/master/classifiers.ipynb">classifiers.ipynb</a>.
</ul> 
</p>
</details>
<details><summary>Burst dataset</summary>
<p>
<ul>
<li> Download the dataset as zip from: https://github.com/Teldh/PRET. </li>
<li> Extract the zip: you should have a folder called <code>PRET-master</code> </li>
<li> Open the <code>PRET-master</code> folder: you should find a folder called <code>app</code> inside. </li>
<li> Open the <code>app</code> folder: you should find a folder called <code>datasets</code> inside. </li>
<li> Upload <code>datasets</code> to the root of "My Drive" of your Google Drive. </li>
<li> Run every cell in <a href="https://github.com/LSparkzwz/Prelearn/blob/master/init_en.ipynb">init_en.ipynb</a>. </li>
<li> Run every cell in <a href="https://github.com/LSparkzwz/Prelearn/blob/master/dataset_init/burst/dataset_init_en.ipynb">dataset_init_en.ipynb</a>. </li>
<li> Pick one type of word embedding you'd like to try from the following list, and run every cell inside its respective ipnyb: <ul> 
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_sum.ipynb">Sum of word embeddings.</a> </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_average.ipynb">Averaged word embeddings.</a> </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_word_frequency.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_word_frequency.ipynb">Average</a> of word embeddings weighted by term frequency. </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_biased_AB.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_biased_AB.ipynb">Average</a> of word embeddings in which words that appear inside the title of B are given a weight equal to 10% of their document (A or B) length. </li>
  <li> (<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_biased_A.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_biased_A.ipynb">Average</a>) Same as above but the weight is only given to words inside the document A, while B stays the same as what you'd obtain with just a sum or average. </li>
  <li> <a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/sum/we_B_weight.ipynb">Sum</a>/<a href="https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/english/average/we_B_weight.ipynb">Average</a> of word embeddings in which the B document embedding has been multipled by a weight equal to 20, A instead stays the same as what you'd obtain with just a sum or average. </li> 
</ul> </li>
<li> Run every cell inside <a href="https://github.com/LSparkzwz/Prelearn/blob/master/classifiers.ipynb">classifiers.ipynb</a>.
</ul> 
</p>
</details>


### How to run (Italian version)(Only avaialable dataset is Prelearn): 
* Request the starting dataset here: https://docs.google.com/forms/d/e/1FAIpQLSdz4q7H7Savij_HGV2YDwZrBP5KUIWU4vRfkcHAnsdKJ4xvxw/viewform .
* From terminal run: `cat data_mining-pairs_train.csv geometry-pairs_train.csv physics-pairs_train.csv precalculus-pairs_train.csv > train.csv`
* Rename `ITA_prereq-pages.xml` to `dataset.xml`
* Upload `train.csv` and `dataset.xml` to the root of "My Drive" of your Google Drive.
* Run every cell in [init_it.ipynb](https://github.com/LSparkzwz/Prelearn/blob/master/init_it.ipynb).
* Run every cell in [dataset_init_it.ipynb](https://github.com/LSparkzwz/Prelearn/blob/master/dataset_init/prelearn/dataset_init_it.ipynb).
* Pick one type of word embedding you'd like to try from the following list, and run every cell inside its respective ipnyb:
  * [Sum of word embeddings.](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/sum/we_sum.ipynb)
  * [Averaged word embeddings.](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/average/we_average.ipynb) 
  * [Sum](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/sum/we_word_frequency.ipynb)/[Average](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/average/we_word_frequency.ipynb) of word embeddings weighted by term frequency. 
  * [Sum](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/sum/we_biased_AB.ipynb)/[Average](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/average/we_biased_AB.ipynb) of word embeddings in which words that appear inside the title of B are given a weight equal to 10% of their document (A or B) length.
  * ([Sum](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/sum/we_biased_A.ipynb)/[Average](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/average/we_biased_A.ipynb)) Same as above but the weight is only given to words inside the document A, while B stays the same as what you'd obtain with just a sum or average.
  * [Sum](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/sum/we_B_weight.ipynb)/[Average](https://github.com/LSparkzwz/Prelearn/blob/master/embeddings/italian/average/we_B_weight.ipynb) of word embeddings in which the B document embedding has been multipled by a weight equal to 20, A instead stays the same as what you'd obtain with just a sum or average.  
* Run every cell inside [classifiers.ipynb](https://github.com/LSparkzwz/Prelearn/blob/master/classifiers.ipynb).
