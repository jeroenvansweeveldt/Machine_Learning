# Machine_Learning
Repository for the machine learning exam

This repository contains the dataset and classifier to predict depression.

The dataset is based on the survey of Bangladeshi citizens to assess the depression level of each participant, using the Burns Depression Checklist (BDC). It contains 30 predictor variables and 1 target variable, the latter being the label of whether or not the person was deemed suffering from depression based on the BDC checklist. The categories, as desribed in the dataset's corresponding paper (https://www.sciencedirect.com/science/article/pii/S2666518221000310), are as follows:

AGERNG: Age range (in years) of the participant
GENDER: Gender of the participant
EDU: Educational qualification of the participant
PROF: The profession of the participant
MARSTS: Marital status of the participant
RESDPL: Type of the residing place of the participant
LIVWTH: It depicts whether the participant lives with his family or not
ENVSAT: Whether the participant is satisfied with his living environment or not
POSSAT: Whether the participant is satisfied with his current position/ academic achievements
FINSTR: Whether or not the participant has any financial stress
DEBT: Whether the participant has any debt or not
PHYEX: The frequency of taking physical exercises of the participant
SMOKE: Whether the participant smokes or not
DRINK: Whether the participant drinks alcohol or not
ILLNESS: Whether the participant is suffering from any serious illness or not
PREMED: Whether the participant takes any prescribed medication or not
EATDIS: Predictor Whether the participant is suffering from eating disorders like overeating/loss of appetite or not
AVGSLP: Average hours that the participant sleeps at night
INSOM: Whether or not the participant suffers from insomnia
TSSN: Average hours that the participant spends in social network (in a day)
WRKPRE: Current work or study pressure of the participant
ANXI: Whether the participant recently feels anxiety for something or not
DEPRI: Whether or not the participant has recently felt that he/she has been
deprived of something that he/she deserves
ABUSED: Whether the participant has recently felt abused (physically, sexually, emotionally) or not
CHEAT: Whether or not the participant has felt cheated by someone recently
THREAT: Whether or not the participant has faced any life-threatening event recently
SUICIDE: Whether the participant has any suicidal thought recently or not
INFER: Whether the participant recently suffers from inferiority complex or not
CONFLICT Whether or not the participant has recently engaged himself in any kind of conflicts with his friends or family
LOST Whether or not the participant has recently lost someone close to him
DEPRESSED It is the target variable that portrays whether the participant is depressed or not

The goal of this assignment was to run at least one classical machine learning classifier and at least one neural classifier to predict whether or not the person suffered from depression. Due to personal misjudgments leading to fatal time constraints, this task largely failed: a classical model was built, but its error analysis is incomplete, and a neural classifier is entirely absent. The classifier that was built was based on the methodology used in the paper. The reason for this being twofold: a)it contained techniques not covered in classes, such as feature selection and boosting methods, and b)so I could compare my results to those in the paper to get an estimation of my abilities.
