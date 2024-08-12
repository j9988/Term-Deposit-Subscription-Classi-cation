# Term-Deposit-Subscription-Classification

### Dataset
Data Source: https://archive.ics.uci.edu/dataset/222/bank+marketing
Dataset Description: Dataset was collected from a Portuguese bank’s contact centre during 17 campaigns conducted between May 2008 and November 2010. The dataset contains 45211 instances with 17 attributes.

### Problem Framing
Given the attributes of client interactions during direct marketing campaigns, classify whether a client will subscribe to a bank term deposit. This is a supervised learning problem using binary classification methods.

### Experiment Setup
#### Experiment Set 1: Comparing Machine Learning Algorithms
| Machine Learning Algorithm         | Best Hyperparameter Tuning                                                                                                     | Weighted F1 Score (Test Set) |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|------------------------------|
| Dummy Classifier (Baseline)        | strategy="uniform"                                                                                                             | 58%                          |
| K-Nearest Neighbors (KNN)          | 'weights'    : 'uniform'  'algorithm'  : 'auto' 'metric'     : 'manhattan' 'n_neighbors': 23                                   | 86%                          |
| Decision Tree  (random_state=0)    | 'criterion'        : 'entropy' 'max_depth'        : 7 'min_samples_split': 30 'min_samples_leaf' : 2 'max_features'     : None | 88%                          |
| Gaussian NB                        | 'var_smoothing': 1.0                                                                                                           | 83%                          |
| Bernoulli NB                       | 'binarize'   : 0.1 'alpha'      : 0.0 'force_alpha': True 'fit_prior'  : True                                                  | 86%                          |
