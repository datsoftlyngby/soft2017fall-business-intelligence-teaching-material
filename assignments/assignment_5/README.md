# Assignment 5: Linear machine learning
This assignment introduces you to machine learning. Machine learning is cool
because we can predict the future. Actually machine learning is just a fancy
word for how machines can use old data to predict new data. The simplest
predictions are linear and uses the formula you probably know from your
high-school math:

    y = ax + b

To predict the outcome of a linear model you need to know the ``a`` and ``b``,
so you can 'predict' the ``y`` value, when you input an ``x`` value.

## How to hand in
The hand-in (on Moodle) should be a link to a GitHub **release** containing a
**single** file with the code and written text for the assignment parts
  - This can either be a ``.ipynb``, ``.py``, ``.pdf`` or ``.md`` file
  - The file must be clearly identifiable. Please name it accordingly.
    (for instance ``report.pdf`` or ``assignment5.ipynb``)

## Part 1
For this part we would like to predict how long a user has to be active
on Hackernews to achieve 1000 points. In this experiment our input variable is
time and our output variable is points. X (time) and Y (points).

The data can be found in json format in the file [``users.json``](https://github.com/datsoftlyngby/soft2017fall-business-intelligence-teaching-material/tree/master/assignments/assignment_5/users.json) under the
``assignment_5`` folder here: [https://github.com/datsoftlyngby/soft2017fall-business-intelligence-teaching-material/tree/master/assignments](https://github.com/datsoftlyngby/soft2017fall-business-intelligence-teaching-material/tree/master/assignments).

Before you start we need to make sure that we separate the data for training
and testing. So split the dataset in a training part and a testing part with
80% training data and 20% testing data.

Now train your model on the training data using a linear regression model.
Plot the training data in a scatter plot along with the linear regression you found to have the best fit.

Report the ``a`` and ``b`` values and write four lines about what ``a``
and ``b`` represents and what the difference is between ``a`` and ``b``.

## Part 2
Now that we have our model, we would like to find out how robust it is.
Calculate the mean absolute error (MAE) for the:

1. Training data (the same data you created the model with)
2. Testing data (the data that was _not_ used when creating the model)

Write two lines:
What do the numbers tell us? And why are the numbers different?

## Part 3
Another way to measure error is to use the mean squared error (MSE).
Calculate the MSE for the following scenarios:

1. Training data (the same data you created the model with)
2. Testing data (the data that was _not_ used when creating the model)

Write two lines:
What do the numbers tell us? Why are they different from the MAE numbers?

## Part 4
A very common metric is the Pearson's ``r`` value. Calculate the ``r`` value
for the following scenarios:

1. Training data (the same data you created the model with)
2. Testing data (the data that was _not_ used when creating the model)

Write two lines:
What do the numbers tell us? Why are they different from the MAE and MSE
numbers?

## Part 5
Now imagine you are a new Hackernews user with the only goal in life to reach
1000 points.

Write four lines: Does your model tell you anything about what it takes to get
1000 points? If so, what does it take?

Write two lines: How accurate is that prediction? And how can it be made more
accurate?
