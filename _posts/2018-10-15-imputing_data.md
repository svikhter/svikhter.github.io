---
layout: post
title: Imputing Data

  I spent most of my prior career working in descriptive analytics. On that side of the analytical word we transform, aggregate, extract, load, and visualize the data, and provide business with historical insight. We then present data in the format easily understandable by the business audience, such as reports and dashboards.

  Our goal is to help business community review trends and metrics, so they could make informed business decisions. We also clean and normalize data, make sure is follows referential integrity, and perform other data preparation tasks.  There is one thing we usually never do. We don’t modify data by imputing estimated values if the data is missing.  

  Imputation is the process of replacing missing data with some substituted values.  It is normal to impute data on predictive analytics side, but when you make a transition from descriptive analytics, it could come as a shock. This is exactly what happened to me as I worked on my first machine learning project. I had to convince myself that it is ok to modify your source data. It can take some time to change your mindset.

  Python scikit-learn module assumes the dataset has no missing data. My housing dataset had 0 values in the most important feature - square footage.  I imputed it using mean values and the group by operation. I calculated mean and manipulated with dataframes. Then later I discovered different ways to do it, with numpy and sklearn.  

  These are some examples from stackoverflow.com. In these examples, the mean age was imputed in Titanic dataset.

  Numpy:

  import numpy as np
  mean_ages = titanic.groupby(['Sex', 'Pclass'])['Age'].transform(lambda x: np.nanmean(x))
  titanic['ImputedAge'] = mean_ages

  Sklearn:  

  from sklearn.preprocessing import Imputer
  imr = Imputer(missing_values='NaN', strategy='mean', axis=0)
  train_df[['Age','Fare']] = imr.fit_transform(train_df[['Age','Fare']])


  There is a general rule that we should impute as little as possible. Here I completely agree.
