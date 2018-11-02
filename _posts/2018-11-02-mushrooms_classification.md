---
layout: post
title: Was the model too good to model?
---
![Image_portobello](images/potrobello.jpg)


The topic.

I picked the project based on my interest in food and restaurant business. Many local restaurants buy foraged mushrooms from local mushroom hunters. How do chefs or restaurant owners decide the mushroom is edible? I thought it might be interesting to see if we can classify mushrooms into edible and poisonous.

The data.

A respectful mushroom society provided a mushroom dataset which was available through UCI website. The set has 8,000+ observations and 20+ categorical nominal features, and is pretty balanced for binary classification. After running some summary statistics with PostgreSQL, I converted all the category values into dummy variables, which expanded the number of featured from 20+ to 100+.   

The metric.
I decided to use ROC AUC score, the area under ROC curve, which should be a good indicator of model performance. The higher number it scores (in the range of 0 to 1) the better performing model you have.

The model.
The first model I tried, Logistic Regression, returned cross-validation score of 1 - for every fold in 10-fold validation.  Does it mean the model was perfect? Actually, no, and the scores above .89 are usually rather alarming.

Turned out this dataset has a very big number of high predictors -  the variables which could perfectly separate the data into edible or poisonous class.  The variables had a very high correlation with the target variable, and the model could easily categorize the data as one class or another.  After playing with features, I removed many of them so I could try and test various models.

This sounds awkward, but I removed the features in order to LOWER the score,  so I could work on making the score HIGHER.

This worked, and I could pick my champion model: Decision Trees with Bagging applied.

The takeaway.

Multiple high predictors in the dataset could make you model to be too good… to model.

The topic I want to learn more about.



Working with feature elimination and selection made me become interested in the feature topic, and I will now explore it more deeply.

The proud moment.

I created Flask app for this project, where a user can select values from drop-down boxes. It runs the model and shows the prediction. Each drop-down represents an original feature, and upon selection, the selected value is assigned 1 and the remaining ones  in the drop-down box are assigned 0 (as in our dummy variables).



The warning.

Always check your mushrooms with a human expert. you don’t want to have that misclassified mushroom on your plate.


