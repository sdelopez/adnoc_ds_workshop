## Challenge 5 : Regularization

In this exercise, you will use polynomial regression and see the effect of regularization. You will use polynomial regression. It is exactly like linear regression, but with new features created as polynomials of the original feature. For instance, if your dataset looks like this:

```python
array([[3],
       [2],
       [2],
       [6]])
```
You can create a new feature which is just, for instance, the data raised at the power of two:

```python
array([[ 3,  9],
       [ 2,  4],
       [ 2,  4],
       [ 6, 36]])
```

These new features will interpreted as if they were independent. Then, you can use the linear regression algorithm as usual.


Here, we use polynomial regression to illustrate a case of overfitting. Add polynomials to your dataset is like adding new features, and adding new features is prone to overfitting. For this reason, the regularization technics that you will use here can be applied when you encounter overfitting in a real dataset.


- Open the Anaconda Prompt, and navigate to this exercise folder:
```bash
cd # Gets back to the $HOME directory
cd Documents/GitHub/ml-week-challenges/03-Best-Practices/05-Regularization
```

- Once you are located in the proper folder, run the following command:

```bash
jupyter notebook
```

To get started, open the `05-Regularization.ipynb` notebook and follow the instructions !


---

:bulb: Don't forget to **push your code to GitHub**

1. Open GitHub Desktop
1. It should automatically detect that the `05-Regularization.ipynb` file has changed. If not, ask a TA
1. Make sure this file is ticked, and write a _commit message_ in the bottom left form
1. Click on the "Commit to `master`" button at the bottom of the form
1. Click on the "Push `origin`" button at the top of the window

