[[Table of Contents W4]]


==*One thing to note, the ApEn algorithm considers each point similar to itself due to how the logarithmic function operates to avoid $ln(0)$. This produces some bias towards regularity.*==

## ApEn from paper
Generally speaking, given a time-series of length _N_, ApEn(_m_, _r_, _N_) is approximately equal to the negative average natural logarithm of the conditional probability that two subseries of length _m_ that are similar (within a tolerance given by ±_r_ times the standard deviation of the time-series) remain similar for subseries of length _m_ + 1. ApEn generates a unit-less number from 0 to 2: an ApEn value equal to zero corresponds to a time-series that is perfectly regular (e.g. a periodic signal), whereas an ApEn value equal to 2 is produced by random time-series (e.g. Gaussian noise). Importantly, the ApEn algorithm counts each subseries as matching itself. As a consequence, the ApEn algorithm inherently produces a bias towards regularity.

### ==wikipedia way==
(From [Wikipedia](https://en.wikipedia.org/wiki/Approximate_entropy))

Algorithm:

==First==, form a time series of the data
$$
u(1),u(2),u(3),...,u(N)
$$
These are $N$ number of raw data values equally spaced in time.

==Second==, fix $m$, a positive integer, and $r$, a positive real number. The value $m$ represents the length of each compared run of data, or *window*, and $r$ specifies a *filtering level*.

==Third==, form a sequence of vectors,
$$
x(1),x(2),...,x(N-m+1)
$$
within $\large R^{m}$, a real $m$-dimensional space defined by $x(i)=[u(i),u(i+1),...u(i+m-1)]$

==Fourth==, use the sequence $x(1),x(2),...,x(N-m+1)$ to construct each $i$ where
$$\large i \: , \:1 \leq i \leq (N-m+1)$$

$$\large
C^{m}_{i}(r)=\frac{(number\:of\:x(j)\:such\:that\:d[x(i),x(j)]\le r)}{(N-m+1)}
$$
In which $\large d[x,x^*]$ is defined as:
$$\large
d[x,x^{*}]=max_{a}|u(a)-u^{*}(a)|
$$

The $u(a)$ are the $m$ scalar components of $X$. $d$ represents the distance between the vectors $x(i)$ and $x(j)$, given by the maximum difference in their respective scalar components. $j$ takes all values, even the values of $i=j$.

==Fifth==, define this equation

$$\large
\Phi^{m}(r)=(N-m+1)^{-1}\sum_{i=1}^{N-m+1}log(C^{m}_{i}(r))
$$

==Sixth==, define Approximate Entropy ($ApEn$) as
$$
ApEn = \Phi^{m}(r)-\Phi^{m+1}(r)
$$


### ==A Slightly Different Approach==
From [Physionet](https://archive.physionet.org/physiotools/ApEn/) they have the $ApEn$ Equation set as:
$$
ApEn(S_{N},m,r)=ln \Bigg[\frac{C_{m}(r)}{C_{m+1}(r)}\Bigg]
$$

which is slightly different from the wikipedia approach.
In this approach they take the $C_{m}(r)$ value as an average of the number of points that fall within the $r$ value specified.

The example they give shows it well. Basically you do an average of however many there are that are *similar* to each other, and total all that up. ==In this case however, you see whether or not their greatest distance is more than $r$ distance away from one another==. This is different from the other way since no matter the value, if it is large and still $r$ close enough it can be counted as similar. However this seems the same as the other way in a weird way. If it is, then they are not similar enough to be counted. If they are less than or equal to $r$ distance from one another, then they are considered similar.

So you take however many there are that are similar, put that over $(N-m+1)$, adn that is the specific $C_{ij}(r)$ value. Then you see what else is similar, and take however many are similar to the next one. Put that again over $(N-m+1)$. Usually there are similarities and you just see however many are similar like that. Then, average them all by multiplying by however many there are that are similar for each $C_{ij}(r)$, and taking the average by adding them up and dividing by $(N-m+1)$

Then you repeat for an increased value of $m+1$ and take the $ln$ of the fraction as shown above.

Complex but honestly more doable than the other way.

## ==For the Code==

From the Research paper on ApEn and SampEn on COP data, they state that for clinical data ==$m$ should be set to either 4 or 5, $r$ is to be set between .25 and .35 times the standard deviation of the data, and $N$ should be equal to or greater than 1000.==

<u>ANOVA</u> is the Analysis of Variance. The paper uses the [Greenhouse-Geisser correction](https://en.wikipedia.org/wiki/Greenhouse–Geisser_correction#:~:text=The%20Greenhouse–Geisser%20correction,and%20Seymour%20Geisser%20in%201959.&text=.,-If%20sphericity%20is) during the procedure to correct p-values calculated.

## SampEn from paper

In order to counteract this shortcoming, the SampEn algorithm does not count self-matches. SampEn(_m_, _r_, _N_) is the negative natural logarithm of the conditional probability that two subseries similar for _m_ points remain similar for _m_ + 1, where self-matches are not included in calculating the probability. In addition to eliminating self-matches, it has been shown that SampEn is largely independent of the data length and shows more consistent behaviours than ApEn.