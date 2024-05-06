# Predicting depression: a machine learning exercise
## Objective
This exercise was done at the end of our machine learning classes to get my bearings in the subject matter. The goal was to find out which factors machine learning models deem the most decisive in predicting whether a person will develop depression. Although the dataset contains textual data, typical techniques seen in the future course _natural language processing_ such as text vectorisation were not applied here, as we hadn't learnt about that yet at the point of doing this exercise.

Due to the sizeable number of predictor variables, two different feature elimination methods, _SelectKBest_ and _RFE_, were used to prune the least interesting variables from the dataset.

There was a notable imbalance between the target labels. Using _SMOTE_, the minority labels were upsampled to match the majority labels in the training sets.

Next, a classical decision tree-based method called _Adaboost_ was used to make predictions. Why a tree-based algorithm? Because these are convenient for retrieving information about which variable or feature had the most weight in the prediction of depression.

Finally, I ran a feedforward neural network using the _Keras/Tensorflow_ framework, to familiarise myself with the technology, and to compare its perfomance against Adaboost. The workflow of this exercise was based on the research paper [An in-depth analysis of machine learning approaches to predict depression](https://www.sciencedirect.com/science/article/pii/S2666518221000310).

## Structure
The repository is structured as follows:
* A map **data** containing the base dataset **depression.csv**, two datasets preprocessed with different techniques of feature elimination, and two plot images of Adaboost's feature importance for each preprocessed dataset.
* A Jupyter notebook with the preprocessing of the data.
* A Jupyter notebook for training the classical model Adaboost on both preprocessed datasets.
* A Jupyter notebook for training the feedforward neural network. 

## Data
The dataset is based on the survey of Bangladeshi citizens to assess the depression level of each participant, using the **Burns Depression Checklist (BDC)**. It contains 30 predictor variables and 1 target variable, the latter being the label of whether or not the person was deemed suffering from depression based on the BDC checklist. The categories, as desribed in the dataset's corresponding paper, are as follows:
* **AGERNG:** Age range (in years) of the participant.
* **GENDER:** Participant's gender.
* **EDU:** Educational level of the participant.
* **PROF:** Participant's profession.
* **MARSTS:** Participant's marital status.
* **RESDPL:** Type (town, village, city) of the residing place of the participant.
* **LIVWTH:** Whether the participant lives with or without their family.
* **ENVSAT:** Whether the participant is satisfied with their living environment or not.
* **POSSAT:** Whether the participant is satisfied with their current position/academic achievements.
* **FINSTR:** Whether or not the participant experiences any financial stress.
* **DEBT:** Whether the participant has any debt.
* **PHYEX:** The participant's frequency of taking physical exercise.
* **SMOKE:** Whether the participant smokes.
* **DRINK:** Wether the participant drinks alcohol.
* **ILLNESS:** Whether the participant is suffering from any serious illnesses.
* **PREMED:** Whether the participant takes any prescribed medication.
* **EATDIS:** Whether the participant is suffering from eating disorders like overeating/loss of appetite.
* **AVGSLP:** Average hours that the participant sleeps at night.
* **INSOM:** Whether the participant suffers from insomnia.
* **TSSN:** Average hours of time spent on social network in a day.
* **WRKPRE:** Current work or study pressure of the participant.
* **ANXI:** Whether the participant recently suffered from anxiety.
* **DEPRI:** Whether the participant has recently felt they had been deprived of something they deserve.
* **ABUSED:** Whether the participant has recently felt abused (physically, sexually, emotionally).
* **CHEAT:** Whether the participant has recently felt cheated by someone.
* **THREAT:** Whether the participant has recently faced any life-threatening event.
* **SUICIDE:** Whether the participant recently suffered suicidal ideation.
* **INFER:** Whether the participant recently suffered from an inferiority complex.
* **CONFLICT:** Whether the participant has recently engaged themselves in any kind of conflict with their friends or family.
* **LOST:** Whether the participant has recently lost someone close to them.
* **DEPRESSED:** Target variable - whether the participant is depressed or not.

## Results
### Disclaimer
The information the algorithms return about the most predictive features for developing depression should **not** be taken at face value. Reliable results can be returned only, and only, through the analysis performed by qualified professionals within the relevant field (psychologists and psychiatrists).

### Model performance
Given the imbalance in target lables - 41 labelled as not depressed and 80 labelled as depressed - in the test set, I will report the f1 macro average scores of each model:


| Adaboost (SelectKBest)| Adaboost (RFE) | FFN (SelectKBest)  |  FFN (RFE) |
| :---: | :---: | :---: | :---: |
| 0.86  | 0.89 | 0.88  | 0.87 |

It is notable that the classical tree-based algorithm performed better than both neural networks. Likely, this has to do with how the data was encoded before fed to the models; the RFE dataset included ordinally encoded predictor variables, which in the error analysis are shown to seemingly have a strong influence in whether a target variable is predicted correctly.

Moreover, despite using a similar workflow in terms of feature selection and oversampling, the same Adaboost classifier in my exercise did not reach the level of accuracy it did in the research paper. Possibly this is due to how the textual data was handled during preprocessing (one-hot encoding/ordinal encoding versus text vectorisation).

### Most important features

These predictor variables were considered the most important in the dataset with SelectKBest selected features:
![feature_importance_skbest](https://github.com/jeroenvansweeveldt/predicting_depression-machine_learning_exercise/assets/98675155/6298da21-5453-4614-970e-8a0f5c8911b6)

These predictor variables were considered the most important in the dataset with RFE selected features:
![feature_importance_rfe](https://github.com/jeroenvansweeveldt/predicting_depression-machine_learning_exercise/assets/98675155/4c0678ce-5e54-4d4d-ad63-19cc48d54171)

As you can see, there is fairly little consistency in which feature is most predictive of developing depression. One standout feature, however, that consistently remains at a high position, is whether the participant is happy with their living environment or not (ENVSAT).
