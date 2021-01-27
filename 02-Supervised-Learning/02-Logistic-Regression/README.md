## Challenge 2 : Logistic Regression
<img src="https://upload.wikimedia.org/wikipedia/commons/6/6d/Exam_pass_logistic_curve.jpeg" alt="Graph of a logistic regression curve showing probability of passing an exam versus hours studying - wikipedia" style="width:400px">
Graph of a logistic regression curve showing probability of passing an exam versus hours studying

### Introduction

In this exercice we are going to take a look at **Graduate Admissions** in relation to **CGPA** and **University Rating**.
We will use the **logistic regression** model to answer some questions.

**Dataset:** "Graduate_Admission.csv"

**Columns:**
**"CGPA"**, range [6.0, 10.0], Cumulative Grade Point Average
**"Rating"**, range [1, 5], 5 is the best university rating
**"Admited"**, range [0,1]

---

- Open the Anaconda Prompt, and navigate to this exercise folder:
```bash
cd # Gets back to the $HOME directory
cd Documents/GitHub/ml-week-challenges/02-Supervised-Learning/02-Logistic-Regression
```

- Once you are located in the proper folder, run the following command:

```bash
jupyter notebook
```

Click on the `02-Logistic-Regression.ipynb` file to open the notebook and follow the instructions !

---

### Exercise questions:

1. If your **CGPA is 7.8**, what is the **probability** that you will be accepted in an university with a **rating of 3**?
2. If your **CGPA is 8.5**, which is the **best university** you can apply to and have a probability of more than **50%** to be accepted?
3. What should be your CGPA in order to have a probabilty of **80%** to enter in the **best rated** univesity?
4. With the help of you model, can you plot the **probability** to be **admited** in an university **rated 4**, by **CGPA**?

---

:bulb: Don't forget to **push your code to GitHub** once you are done !

1. Open GitHub Desktop
1. It should automatically detect that the `02-Logistic-Regression.ipynb` file has changed. If not, ask a TA
1. Make sure this file is ticked, and write a _commit message_ in the bottom left form (For instance: `work on Logistic Regression`)
1. Click on the "Commit to `master`" button at the bottom of the form
1. Click on the "Push `origin`" button at the top of the window

