## Challenge 2 : Cross Validation
In this exercise, we will dive into the whole machine learning development workflow.   
One very common mistake is to learn the parameters of a prediction function and testing it on the same data. What's wrong with that? We can’t fit the model to our training data and hope it would accurately work for the real data it has never seen before.

To prevent this from happening, there are several techniques: 
- we could remove a part of the training data and using it to get predictions from the model trained on rest of the data (= __Holdout Method__). But, by reducing the training data, we risk losing patterns in data set and increase the error. 
- __K-Fold cross validation__ will help us to solve this problem. In K Fold cross validation, we  split our data into k separated "folds". Then, the Holdout Method is repeated k times, such as each time, one of the k folds will be the test subset and the (k-1) other folds will be used together as the training set.

__Note__ that this method does not depend on the model. In this example, we will use it on a Linear Regression but you could use it on any methods you want (KNN, Logistic Regression,...).

This following image schematize this algorithm.
<img src="https://scikit-learn.org/stable/_images/grid_search_cross_validation.png" style="width:50%;">

The general workflow to apply the Cross Validation is always the same:
1. Instanciate the model from scikit-learn you want to use (LinearRegression for the today exercise);
2. Instanciate the KFold class with the parameters you want;
3. Use the cross_val_score() function to measure the performance of your model.

---

- Open the Anaconda Prompt, and navigate to this exercise folder:
```bash
cd # Gets back to the $HOME directory
cd Documents/GitHub/ml-week-challenges/03-Best-Practices/02-Cross-Validation
```

- Once you are located in the proper folder, run the following command:

```bash
jupyter notebook
```

To get started, open the `02-Cross-Validation.ipynb` notebook and follow the instructions !


---

:bulb: Don't forget to **push your code to GitHub**

1. Open GitHub Desktop
1. It should automatically detect that the `02-Cross-Validation.ipynb` file has changed. If not, ask a TA
1. Make sure this file is ticked, and write a _commit message_ in the bottom left form
1. Click on the "Commit to `master`" button at the bottom of the form
1. Click on the "Push `origin`" button at the top of the window