[[Table of Contents W4]]

## Preface

Two algorithms presented, ==Approximate Entropy and Sample Entropy.== These determine the regularity found within a data set and help with classification based on patterns.

Approximate Entropy --> (ApEn)
Sample Entropy --> (SampEn)

A mathematical measurement of the level of randomness of a dataset is required, denoted by ==information theory or IT==. From these measurements of randomness therein lies the background of Approximate Entropy (ApEn) which is ==chaos theory==.

ApEn is biased, and in order to 'un-bias' it, SampEn was introduced.

## Statistics
Information theory was devised to analyze messages sent through a noisy channel and understanding how to reconstruct the message with low probability of error. 

In the probabilistic case: (*straight from the source material*)

if $X$ can take the values $(x_{1},...,x_{n})$ and $p(x)$ is the probability associated with those values given $(x\Subset X)$ entropy is given by the following equation -
$$\Large
H(X) = - \sum_{x\subset X}p(x)log_2(p(x))
$$

Logarithm with a base of 2 is usually chosen however any other base can be chosen. The average or expected information of an even is determined by -
$$
E\large[log(\frac{1}{p(X)})]
$$

## Basics of Information Theory (IT)
Information is the *decrease* in ambiguity regarding a phenomenon and an increment to our knowledge when observing a specific event. Mathematically, information is proportional to the inverse of the probability function of the event, $\large log_{2}\frac{1}{p_i}$.

==Entropy is denoted as $\large(H_{X})$==. It measures the amount of uncertainty associated with a variable $X$ when only its distribution is known. It measures the amount of information we hope to learn from an outcome (observations), and we can understand it as a measure of uniformity. ==The more uniform the distribution, the higher the uncertainty and the higher the entropy.== Entropy is a function of the probability distribution $\{p_{1},p_{2},...\}$ and not the values of the variables $\{x_{1},x_{2},...\}$

Information theory and the concept of entropy provide a mathematical way of determining the information contained in a message.

Randomness and entropy go hand in hand. When randomness $p = 1/2$, entropy is at it's maximum value $H=1$. Entropy can be obtained from randomness via the following equation and also seen on this graph:
$$
\large H(X) = -plog_{2}(p)-(1-p)log_{2}(1-p)
$$
![[randomnessgraph.png|600]]

## Equation Diving

With more than one random variable we have a new set of equations to factor. Therefore,

let $p(X,Y)$ be the joint probability distribution of two discrete rando variables whose possible realizations are $\{x_{1},x_{2},...x_{k}\}$ for $X$ and $\{y_{1},y_{2},...y_{j}\}$ for $Y$.
So, we let 
$P(X = x_{k})=p_{k}$, 
$P(Y=y_{j})=q_{j}$,
$P(x=x_{k},Y=y_{j})=w_{kj}$
$P(X|Y)=P(X=x_{k}|Y=y_{j})=p_{k|j}$
$P(Y|X)=P(Y=y_{j}|Y=x_{k})=q_{j|k}$

The ==conditional entropy $H(X|Y)$== is the total amount of information contained in the variable $X$ given that $Y$ assumes a specific value:
$$
\large H(X|Y) = \sum_{k,\:j}w_{k\:j}log(\frac{q_{j}}{w_{kj}})
$$

The ==joint entropy== of $X$ and $Y$ is given by:

$$
\large H(X,Y) = \sum_{k,\:j}w_{kj}log(\frac{1}{w_{kj}})
$$

Using the chain rule we can relate the two via:

$$
\large H(X,Y) = H(Y) + H(X|Y) = H(X) + H(X|Y)
$$

