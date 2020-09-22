Please read about the [first approach](https://github.com/LSparkzwz/Prelearn/blob/master/report/first_approach_report.md) first.

## Second approach: 
This approach takes into consideration the fact that the dataset given by [Prelearn](https://sites.google.com/view/prelearn20/data?authuser=0) is split into four different subjects: geometry, physics, data mining and precalculus. The intuition is that maybe it's easier to optmize the output of the binary classifiers if the training data belongs to just one subject. Therefore in this approach two classifiers are used, a multiclass classifier to understand the subject of the two documents and a binary classifier (for each subject) to understand if there's a prerequisite.
![Second approach](https://i.imgur.com/piyGjTl.png)  

### This second approach has only been tested on the Italian language with document embeddings obtained from the averaging of word embeddings.

#### How the datasets have been created: 
For this method five datasets are needed: one to classify the subjects and one for each of the four subjects to understand the prerequisite.  
The four prerequisite datasets have been obtained like in the first approach, except they remain split from each other instead of being combined into a single bigger dataset.  
The subjects dataset has also been obtained in a similar fashion (cleaning of the documents and creation of the document embeddings) to the first approach, except that instead of having the output as 0 or 1, this time the output can be geometry, physics, data mining and precalculus. 

### Results: 
You can check the results [here](https://github.com/LSparkzwz/Prelearn/blob/master/results/second_approach_results.md).  
Keep in mind that the scores of the binary classification don't take into consideration the scores of the subject classificator.  
For example the true accuracy score for the classification of geometry documents would be 92% of 95% which equals to 87.4%, this is because some of the geometry documents never reach the geometry classifier since roughly 5% of them gets lost during the subject classification.

### Considerations: 
While the results of this approach seem to be worse than the ones in the first when taking into consideration that 5% of the documents get classified with the wrong subject.
I still think this is a better approach than the first one because it should be easier to increase the scores of each classifier by optimizing their respective document embeddings, since a focused optimization for each subject should give better results than a more general approach that can't take into consideration the peculiarities of each subject, for example the types of formulas utilized in geometry may vary from the ones used in data mining in such a way it's better to treat them differently when creating the document embeddings. This would be even more noticeable if there were to be a non-scientific subject that doesn't have any formulas in the first place. 

### How to run: 
* Request the starting dataset here: https://docs.google.com/forms/d/e/1FAIpQLSdz4q7H7Savij_HGV2YDwZrBP5KUIWU4vRfkcHAnsdKJ4xvxw/viewform .
* From terminal run: `sed -e 's/$/data-mining/' -i data_mining-pairs_train.csv`.
* From terminal run: `sed -e 's/$/physics/' -i physics-pairs_train.csv`.
* From terminal run: `sed -e 's/$/geometry/' -i geometry-pairs_train.csv`.
* From terminal run: `sed -e 's/$/precalculus/' -i precalculus-pairs_train.csv`.
* From terminal run: `cat data_mining-pairs_train.csv geometry-pairs_train.csv physics-pairs_train.csv precalculus-pairs_train.csv > m_dataset.csv`.
* Rename `ITA_prereq-pages.xml` to `dataset.xml`
* Upload `m_dataset.csv` and `dataset.xml` to the root of "My Drive" of your Google Drive.
* Run every cell in [second_approach.ipynb](https://github.com/LSparkzwz/Prelearn/blob/master/second_approach.ipynb).
