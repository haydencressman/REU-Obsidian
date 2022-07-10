[[Table of Contents W3]]

## <u>Testing and Training

==This info is from the videos made by Dr. Valles.==
The data needs a weight for the deciding algorithm to choose an outcome.
The weight can be decided from the following equations:
$$\huge w_{j}:= w_{j}+\Delta w_{j}$$
where $\Large \Delta w_{j}$ is considered the change in weight for the software to learn. The calculation for $\Large \Delta w_{j}$ is shown below.
$$\huge \Delta w_{j} = \eta (y^{i}-y`^{i})x_{j}^{i}$$

Where $\Large \eta$ is considered the 'learning rate' and is a constant the user decides. $\Large y^i$ is the True Output and $\Large y`^i$ is the Predicted output. $\Large x_{j}^{i}$ is the input. This equation allows you to update the weights based on the predictions.

Each weight is assigned to an input value and this would allow you to change each weight $\Large w_i$ for each input $\Large x_i$.

## <u>Standardization of features

Standardization is defined as:

$$\large x'_{j}=\frac{x_{j}-\mu_{j}}{\sigma_{j}}$$

where the mean, which is averaged around 0 is $\large \mu_{j}$ and the standard deviation is $\large \sigma_{j}$
<u>Stochastic gradient descent</u> is a thing, but since our data sets are 'small' this may not be necessary.

The sum of errors squared can be calculated the following ways,
$$Total\:Sum\:of\:Squares\:= \sum_{i=1}^{n}(y_i-\bar{y})^2 $$
for this case the $y_{i}$ is the true iterated value from the dataset, and $\bar{y}$ is the mean of all the data being iterated through. 

$$Sum\:of\:Squares\:Regression\:= \sum_{i=1}^{n}(\hat{y}_{i}-\bar{y})^2$$
where this equation is based off of a linear regression line. The values $\hat{y}_i$ is for the predicted value at a given $x$ that falls on the best-fit line, and $\bar{y}$ is the value of the mean of the data.

==The sum of square error== is shown below, which is primarily the equation you need:
$$\Large
Sum\:of\:Square\:Error\:=
\sum_{i=1}^{n}(y_{i}-\hat{y}_{i})^2
$$

This is essentially a combination of the previous equations, ==here again $y_{i}$ is the actual data point and $\hat{y}_i$ is the value on the linear regression line.==
I assume these values can be used by whatever algorithm you use to find the error based on the actual value and the predicted one.

## <u>sklearn library and numpy library

By using `import sklearn` in python you can import different datasets to help with the machine learning aspect, as well as other helpful functions.
The API on the website can be found [here](https://scikit-learn.org/stable/modules/classes.html) and the user guide is [here](https://scikit-learn.org/stable/user_guide.html).

By using `import numpy` we can use numpy functions which, like `import math`, are extremely useful. The numpy API can be seen [here](https://numpy.org/doc/stable/reference/index.html#reference).