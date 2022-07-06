[[Table of Contents W5]]

## preliminary

Goes on to talk about both [[Usage of ApEn and SampEn#ApEn from paper|ApEn]] and [[Usage of ApEn and SampEn#SampEn from paper|SampEn]] and build upon those for the Multi-Scale Entropy Algorithms.
Essentially *multi-scale* in this case refers to the multiple time-scales used during calculations. Again, basically the difference between ApEn and SampEn is the self comparison vector being counted towards the total entropy in a system. Eliminating this in SampEn resolves any unwanted bias towards stability.

Multi-Scale Entropy (MSE) builds on the formulae and theory of Sample Entropy. It integrates a course graining procedure which shows the point-to-point fluctuations over a range of time scales.

### Equation

For MSE the base equation is given as thus:

$$\Large
y^{t}_{j}=\frac{1}{\tau}\sum_{i=(j-1)\tau+1}^{j\:\tau}x_{i},1\le y_{j} \le \frac{N}{\tau} 
$$
In this instance, $\Large \tau$ is the timescale of interest, $y_j$ is a data point on the newly constructed time series, $x_{i}$ is a data point in the original time series and $N$ is the length of the original time series.

Once the range of time scales of interest is found, the area under the SampEn vs. Time Scale Curve, known as the *complexity index* $C_{1}$ can be calculated by:

$$\large
C_{1}=\sum\limits_{i=1}^{N}S_{E}(i)
$$

Where $S_{E}$ is the $S_{E}$ value at timescale $i$ and $N$ is the total number of timescales. 

## Some Findings
The first article of week 5 found that the complexity between ASD and TD groups differed in that the complexity index for individuals with ASD were lower than that of their TD counterparts in the mediolateral direction mainly, with some in the anteroposterior. The sway areas were also ginormous for individuals with ASD.

The researchers do not know exactly why the anteroposterior direction has about the same amount of control and why the difference is mainly in the mediolateral direction.

Essentially in layman's terms the side to side posterity control is lower in people with ASD than it is in people with TD and the front to back sway is around the same, with the only difference being found under extreme conditions (eyes closes and compliant surface). 