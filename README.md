Decision Trees and Random Forests

In this assignment, we are going to work with a real-world dataset. The Adult dataset (Blake and Merz, 1998)Links to an external site. was extracted from the 1994 Census database. The dataset is available as a CSV (Comma-Separated Values) file, and we will use pandas to read it.

The prediction task is to determine whether a person makes over 50K a year. What makes this dataset interesting is: out of 48842 samples, it has about 24% positive (income > 50K) and 76% negative (income <= 50K) samples; some of the features have missing values (marked by "?"), and there are six continuous and eight categorical features. These observations make it a good candidate for a Decision Tree-based approach to classification. 

We will use a preprocessed version of the original dataset for the set of tasks. Two features (fnlwgt and education_num) were removed, and the dataset has been partitioned into training and testing sets. You can read more about fnlwgt from hereLinks to an external site..
Download the data files census-data_v1.zip
Software 

You will be using Decision Tree and Random Forest implementations of the Python-based Machine Learning library scikit-learn. 

    https://scikit-learn.org/stable/modules/tree.html#classificationLinks to an external site.
    https://scikit-learn.org/stable/modules/ensemble.html#random-forestsLinks to an external site. 

 
Classification Tasks
Task 1: (5 points) Data Exploration 
Handle missing values

The scikit-learn implementation of Decision Trees does not support missing values. You can drop the rows with missing values. 
Task 2: (10 points) More preprocessing

A limitation of scikit-learn's DecisionTreeClassifier and RandomTreeClassifier is that they do not accept non-numeric values. That is, the categorical features cannot be used as-is. One way to overcome this is to transform the feature space, making one binary-valued feature out of each value of the categorical features while keeping the numeric features intact. You can use scikit-learn's OneHotEncoder for this. 

When transforming the original data records, numeric (i.e., continuous) features remain unchanged. Each binary-valued feature that replaces the categorical features is set to 1 or 0 depending on whether the original categorical feature takes the relevant value. 

Finally, randomly assign the data points to the training set (70%) and validation set (30%). Use the last two digits of your student ID as the seed for the random assignment. 

Tip: It would be helpful to save the output of the first two tasks to a text or a CSV file. You can write a DataFrame into a CSV fileLinks to an external site..
Task 3 (10 points) Tune Decision Tree Classifier

If we use all the features from the training set, we can call the resulting tree a full-depth Decision Tree. Unfortunately, such full-depth trees are prone to overfitting. One way to address this is via pruning; scikit-learn uses a post-pruning strategy that is not straightforward. Instead, use two parameters available in the DecisionTreeClassifier that you can tune: max_depth, which limits the depth of the decision tree, and min_samples_leaf Which requires that every leaf has at least this many data points. Generate two plots where on the X-axis you vary one of the parameters (see below), and on the Y-axis, you show classification accuracy. Each plot should have two lines on it, one for accuracy on training_set and another for accuracy on validation_set. Save your best choices of parameters. 

    max_depth = [1, 2, 3, ..., 30]
    min_samples_leaf = [1, 2, 3, ..., 50] 

Here are two sample outputs of this step:
max_depth_sample.png 	min_samples_sample.png

 
Task 4 (10 points) Tune Random Forest Classifier.

One of the parameters to tune the Random Forest Classifier is the number of trees in the ensemble (n_estimators in scikit-learn). As before, generate two plots with classification accuracy (Y-axis) of training_set and validation_set vs. (X-axis):

    n_estimators = [1, 2, 3, ..., 50], with all other parameters set to default.
    n_estimators = [1, 2, 3, ..., 50], with max_depth and min_samples_leaf chosen using your best results from Task 3. 

 
Task 5 (10 points) Evaluate your model using test data

Train your best configuration of DecisionTreeClassifier and RandomForestClassifier (both) on the entire training data, and report their performance on the test dataset using the following metrics:

    Accuracy
    Confusion MatrixLinks to an external site. 
    PrecisionLinks to an external site. and RecallLinks to an external site.  

Task 6 (3 points) Reflection

Share your experience of working on this assignment. What was the most exciting part of it? What was the most challenging one? What did you learn from completing the assignment? 
Submission  

Please submit your work as an IPython notebook. Make sure to keep all the outputs in the notebook. Additionally, you can also include a PDF of the notebook showing the results and plots.   
