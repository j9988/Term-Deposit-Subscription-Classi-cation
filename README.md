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

#### Experiment Set 2: Selecting features
| Method            | features                                                                                                                 | f1 weighted | accuracy | Precision weighted | Recall weighted |
|-------------------|--------------------------------------------------------------------------------------------------------------------------|-------------|----------|--------------------|-----------------|
| SFS - Forward     | ['age', 'job', 'marital', 'education',   'duration', 'pdays', 'previous', 'poutcome']                                    | 89.04       | 90.01    | 88.73              | 90.01           |
| SFS - Backward    | ['age', 'education', 'balance', 'duration',   'pdays', 'previous', 'poutcome']                                           | 89.02       | 89.96    | 88.69              | 89.96           |
| Info gain + ANOVA | ['poutcome', 'duration', 'campaign',   'pdays', 'previous']                                                              | 88.94       | 89.99    | 88.64              | 89.99           |
| Chi2 + ANOVA      | ['job', 'marital', 'education', 'housing',   'loan', 'contact', 'poutcome', 'duration', 'campaign', 'pdays', 'previous'] | 88.03       | 89.40    | 87.68              | 89.40           |

#### Experiment Set 3: Ensemble learning
| Method    | F1-Score on Best Model in Experiment Set 1 | F1-Score on Best Model in Experiment Set 2 |
|-----------|--------------------------------------------|--------------------------------------------|
| Bagging   | 88.46                                      | 88.96                                      |
| AdaBoost  | 86.97                                      | 86.35                                      |
| Stacking  | 88.09                                      | 88.68                                      |

#### Experiment Set 4: Varying training sample size
Best model:
| Varying Training sample size | Best Performing Models     | Accuracy (Validation) | F1 Score (Validation) | Accuracy (Testing) | F1 Score (Testing) |
|------------------------------|----------------------------|-----------------------|-----------------------|--------------------|--------------------|
| 90%                          | Decision Tree (8 Features) | 90.41                 | 89.69                 | 89.72              | 89.09              |
| 100%                         | Decision Tree (8 Features) | 90.58                 | 89.54                 | 90.01              | 89.04              |
| 100%                         | Bagging                    | 90.71                 | 89.73                 | 89.88              | 88.93              |

### Overall Conclusion
