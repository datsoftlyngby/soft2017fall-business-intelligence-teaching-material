# Assignment 8: Populations and deep learning

## Part 1: Accuracy and recall

### Part 1.1
Write two lines: what is the difference between accuracy and precision?

### Part 1.2
Write two lines: what is the difference between precision and recall?

### Part 1.3
Using ``sklearn.metrics.classification_report`` print the result from your
breast cancer classification from last week. Explain what is going on in at
least two lines of text.

## Part 2: Population and t-test
Using the data from ``brain_size.csv``, we would like to learn something
about the height of the people in the dataset and how it compares to the
danish and american population.

The data is taken from the scipy example at
http://www.scipy-lectures.org/packages/statistics/index.html#student-s-t-test-the-simplest-statistical-test

### Part 2.1
Write at least two lines about what a t-test can tell you and what the P-value
can be used for.

### Part 2.2
It turns out that the [average danish height is around 1.8 meters (71 inches)](https://en.wikipedia.org/wiki/List_of_average_human_height_worldwide).
Run a t-test using ``scipy.stats.ttest_1samp`` on the height of the people
in the dataset, assuming the mean height in the population is 71 inches.
Report the output and, using at least two lines of text, describe what the
numbers tells us.

### Part 2.3
Americans is generally a little lower than danes. It turns out they are [roughly
around 174 cm (68.4 inches) tall](https://ourworldindata.org/human-height/).
Run the same t-test as before, but assuming that the average height of the
population now is 68.4 inches.
Report the output and, using at laest two lines of text, describe what the
numbers tells us, and why they are different from the numbers from before.

## Part 3 (OPTIONAL): Training a perceptron network
Using the breast cancer dataset to predict whether a tumor is benign or
malignant, try to train a perceptron network (using
``sklearn.linear.Perceptron``) instead of your logistic model.

Don't forget to either split the dataset using a 80/20 training/testing split
or to use K-fold cross-validation (K is usually 10).

### Part 3.1
Write two lines about what is going on in the perceptron network.

### Part 3.2
Measure the accuracy of the model. Write two lines: is it better or worse than
your logistic regression model, and why is it better or worse?
