# Assignment 7: Text classification and geographical data
Last week we looked at dependent variables that does not fit into a linear,
continuous scale. Examples for this is gender or, say, weather types that is
defined by humans to fit into categories. Another example for this is emotions.
You can't be 5 happy. Or 3 sad. It doesn't really make sense. Instead you
try to get your numerical data to fit into something that resembles the category
'sad' or 'happy'.

Think back at our example for classifying cancers. Our input was not
categorical, it was numerical. So what happens in logistic regression is that
you find a clever way to sort the input into a small number of categories. The
problem is that we do not always know which categories to sort them into. Think
about emotions. How many emotions are there? 6? 10? In this assignment we will
work with clustering to discover how many categories we can find in our data.

## Part 1: Finding positive/negative posts
In the file ``hn_items.csv`` you'll find the very first ~12000 posts in
the Hackernews platform. Run all the text of all the posts through the Vader
NLTK sentiment analysis algorithm, to extract information about the sentiment
of the text. For each sentiment score, you will find a ``pos`` and ``neg``
entry, telling you how positive or negative each post is.

Report the 5 most positive and the 5 most negative texts.

## Part 2: Classifying post emotions
Convert the Vader sentiment into a two-dimensional vector showing how positive
and negative a text is (positive on the first axis and negative on the second).

Using 10-fold cross-validation, use K-means clustering to find clusters in the
posts. Report the accuracy of the testing data in each fold using
either the score of your model or ``sklearn.metrics.accuracy_score``.

## Part 3: Housing price heatmap
Imagine you're on the lookout for a new house or apartment somewhere in the
Copenhagen area.

Before you can start your analysis you have to load the ``boliga_zealand.csv``
from the ``boliga.zip`` file. This file contains entries of houses/apartments
being sold in Denmark, scraped from Boliga. But only the ones with a postal
code that is <= 4000. That limits the dataset to housing within the Copenhagen
area.

Your first job is to create a heatmap that shows the geographical price
distribution. To do this you need to extract a triple from the dataset of
``(x, y, price)``.

Write four lines: Where do you think it's best to live if you want something
cheap **and** central? Why?

## Part 4: Housing price model
You're looking for a new house or apartment, so the heatmap only helps you
with the initial analysis. What you need to look for is the perfect
combination of distance to the center of Copenhagen (Nørreport station)
and price.

To do this, create a linear model that tries to predict the price of the place,
given the distance to Nørreport Station and the number of square meters in the
apartment.

You're not really sure whether there are any ordering effects in your data, so
to cover your bases, you will have to employ 10-fold cross validation.

For all 10 folds: report the coefficients, intercept, MAE, MSE and Pearson's r
score.

Finally: write 5 lines on what these metrics tells us. Can the model help us
intuit about how to shop for housing?

## Part 5 (OPTIONAL): Optimising the housing price model
For this analysis we only looked at two factors. The dataset contains many many
more. What about time? Prices change over time, so does time influence your
choice? Or what about number of rooms? Or year of construction?

Create a model that includes some of these concepts. Use 10-fold
cross validation to report the coefficients, intercept, MAE, MSE and
Pearson's r score.

Write two lines: Did the model improve compared to the previous model?
Why/why not?
