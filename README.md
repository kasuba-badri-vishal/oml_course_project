# oml_course_project
Oversmoothing in Transformers for Text Classification

Complete Project Repository : [link](https://github.com/DhruvKudale/oversmoothing-based-subset-selection)

# Team Details

| Name                  | ID       |
|-----------------------|----------|
| Dhruv Kudale          | 22M2116  |
| Badri Vishal Kasuba   | 22M2119  |
| Kishan Maharaj        | 22M2122  |

## Installation

1. ```pip install -r requirements.txt```
2. For execution of submodular functions, need to install submodlib library from here - [link](https://github.com/decile-team/submodlib)


## Methodology

We propose a novel approach to enhance text classification by proposing two modifications in existing architectures: instance selection and controlled oversmoothing. Firstly, we recognize the importance of instance selection, understanding that not all vector embeddings generated by pre-trained encoders are equally relevant to the classification task at hand; for instance, there are frequent occurrences of noisy data points when the data is from social media or other unregulated sources. Instead of relying on the entire dataset for training, we aim to identify a subset of instances that are most informative and relevant for the classifier. This selective approach is crucial for optimizing both model performance and efficiency, especially when dealing with large datasets where redundant or irrelevant instances may introduce noise and hinder classification accuracy. Using such large datasets with high noise can be costly, especially when the architecture under consideration is very large, causing high computational and environmental costs. Secondly, we determine instance scores using controlled oversmoothing. Controlled oversmoothing plays a pivotal role in our approach to instance selection for text classification. Oversmoothing occurs when classifiers excessively generalize the representations of input instances, causing them to converge towards a single vector and thereby reducing the model's ability to differentiate between classes accurately. By inducing controlled levels of oversmoothing beforehand for every vector embedding, we can regulate the selection of informative instances. By incorporating controlled oversmoothing into our instance selection process, we can assign scores to individual instances based on their relevance and informativeness for the classification task. Instances that exhibit higher levels of similarity after oversmoothing may be deemed less informative and thus assigned lower scores, whereas instances that maintain distinct representations may receive higher scores. ***By balancing the trade-off between generalization and distinctiveness in the embeddings, we can identify subsets of data that are most conducive to training effective text classification models***


### Execution Steps

The Documented notebooks along with ordered way of execution is present in Notebooks folder

Embeddings are stored in the ```notebooks/embeddings/``` folder which are the embeddings of datasets used created through MPNet transformer model


### Results

#### Results on Rotten Tomatoes

| Model               | Precision | Recall | F1 Score | Accuracy |
|---------------------|-----------|--------|----------|----------|
| SVM                 | 0.76      | 0.83   | 0.79     | 0.76     |
| Logistic Classifier | 0.77      | 0.81   | 0.79     | 0.76     |
| Naive Bayes         | 0.76      | 0.82   | 0.78     | 0.76     |
| BERT                | 0.83      | 0.83   | 0.83     | 0.83     |
| Random + FFN        | 0.84      | 0.84   | 0.84     | 0.84     |
| Fac Loc + FFN       | 0.85      | 0.85   | 0.85     | 0.85     |
| Ours (75%)          | 0.85      | 0.85   | 0.85     | 0.85     |

#### Results on OLID Dataset

| Model               | Precision | Recall | F1 Score | Macro F1 |
|---------------------|-----------|--------|----------|----------|
| SVM                 | 0.76      | 0.78   | 0.76     | 0.69     |
| BiLSTM              | 0.82      | 0.82   | 0.81     | 0.75     |
| CNN                 | 0.82      | 0.82   | 0.81     | 0.80     |
| Random + FFN        | 0.79      | 0.80   | 0.80     | 0.74     |
| Fac Loc + FFN       | 0.80      | 0.81   | 0.80     | 0.75     |
| Ours (75%)          | 0.81      | 0.82   | 0.80     | 0.75     |



