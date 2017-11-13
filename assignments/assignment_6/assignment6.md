# Assignment 6: Multivariate linear regression and logistic regression
In the last assignment you pretended to be a Hackernews user with the only
goal of reaching 1000 points. But our model was pretty limited. We only looked
at time as the input variable. Who knows, perhaps it depends on other things
as well?

Linear regression is great for predicting inputs and outputs. But the linear
model we discussed in the first lecture

    y = ax + b

only include a single input variable. What if we want to look at something else?
Like the number of posts a user made? Then the model could look like this:

    y = ax_1 + bx_2 + c

And what if we want to include one more thing? Like number of upvotes?

    y = ax_1 + bx_2 + cx_3 + d

And so on. Your model is still linear, but now it contains many variables. If
you think about it, each variable is the same as a dimension in space. So in
the model where time predicted points, you had a 2-dimensional plot. If you
include the number of posts you have a 3-dimensional.

## Part 1
Going back to the Hackernews data set from the last assignment, use the same
80/20 split in training and testing data to run a new, multivariate linear
analysis. In this model, include the number of posts as an addition to time.

Test the model on the testing data and report the MAE and RMSE. Write two
lines about the model quality compared to your model from last week.
Does number of posts help you predict the score?

## Part 2
In this part we will try to use k-fold cross validation with 10 folds. Select
the model you created with the best prediction quality so far (depending on your
results, either the model from your last assignment or from part 1).
Now create 10 training/testing data pairs and for each pair:

* Train your model using training data from the current fold
* Test your model on the test data from the current fold
* Report on MAE and RMSE from your model on the testing data from the current fold

Lastly, take the average of each metric for all the folds and report them.
Write four lines about what you found, and compare the averaged MAE and RMSE
numbers from your k-fold cross validation experiment, with the MAE and RMSE
you found from the old model with a 80/20 split. Is there a difference? Why or
why not?

## Part 3
In our previous examples we tried to predict a numerical variable, namely
points. Points can have values from 0 and upwards, in a continuous space.
But what if we work with things that aren't continuous? Like grades
(-3, 0, 2, 4, 7, 10, 12) or cars
(Nissan, Toyota, Tesla...) or perhaps genders (male, female, other)?

To do that we need logistic regression. Logistic regression allows us to predict
things that are not a continuous number, but instead divided into categories.
This putting things into categories is also referred to as classification.

We will be using a new dataset based on
[breast cancer patients](http://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Diagnostic%29) in Wisconsin,
USA, and our goal is to _predict whether cancer is benign or malign_. One or
the other.

### 3.1
Load the data from this ``.csv``:
[http://archive.ics.uci.edu/ml/machine-learning-databases/breast-cancer-wisconsin/wdbc.data](http://archive.ics.uci.edu/ml/machine-learning-databases/breast-cancer-wisconsin/wdbc.data).
Report the ``head`` of the table. Have a
look at the data before you get started with the analysis.
How big is your dataset? What are the different variables?

Write two lines about notable features of the data.

### 3.2
Our goal is to predict whether the patients have benign or malign cancer.
For this part you can choose the input variables, but use at least two:
which ones do you think have the most impact?

Using 10-fold cross-validation, train your logistic model using every variable
in the dataset (except the id and diagnosis variable) as input variables, and
the diagnosis variable as your output variable ``y``.

Report the accuracy of the model using ``sklearn.metrics.accuracy_score`` and
write two lines about how good you are able to predict whether a tumor is
benign or malignant.

## 4 (OPTIONAL)
Finally we would like to reduce the dimensionality of the data. Using
principal component analysis, build a model that retains 95% of the variance.
How many dimensions do you need to explain 95%?

Transform (project) the data using your PCA model into a new input variable.
Using a logistic regression model as before train it with your transformed data
and report the score of the model.

How good are you at predicting the cancer type with your new data?
Write one line reporting the accuracy and what that means.
