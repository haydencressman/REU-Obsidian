[[Table of Contents W5]]

##  Some Websites
Someone on the [math stackexchange](https://math.stackexchange.com/questions/911792/3-sigma-ellipse-why-axis-length-scales-with-square-root-of-eigenvalues-of-covar) has felt my pain and heeded my call when I needed it most, yet he also turned up nary a thing. I follow in his footsteps on my quest to understand why this is happening.

Yeah I really have no idea and neither does math stack exchange.

## ==Equation used==
The saint known as ==Nras== on math.stackexchange.com has graciously bestowed upon my wrinkled mind the basic equation used. No real derivation, but we can see where the python scripts come from.

Basically, let distributions $1$ and $2$ be centered at $\mu_{1}$ and $\mu_{2}$ respectively and then let:
$$\large
A = \sigma^{2}_{2},\; B=-\rho\sigma_{1}\sigma_{2},\; C=\sigma_{1}^{2},\; D=(1-\rho^{2})\sigma_{1}^{2}\sigma_{2}^{2}
$$
So 4 variables. Basically $A$ and $C$ ==variances==, and $B$ is the ==negative covariance of both sets of data.== $D$ is some ==ungodly abomination== that I do not know what it is.
Then it follows as thus for an ellipse,
$$\large
A(x-\mu_{1})^{2}+2B(x-\mu_{1})(y-\mu_{2})+C(y-\mu_{2})^{2} = D
$$
Kinda weird but I assume it works. I will not check. For this we need a new variable in order to calculate both the major and minor axis lengths and the inclination for the ellipse.
$$\large
R=[(A-C)^{2}+4B^{2}]^{1/2}
$$
So here is the square toot in the equation. Now, to calculate the lengths it is like this:
$$\large
b,a=\Big(\frac{2D}{A+C\pm R} \Big)^{1/2}
$$
This will give you the lengths for the major and minor axis $b$ and $a$. Which is which is just to be known later. I think the $-$ refers to the minor and the $+$ refers to the major.
The inclination or the angle $\Theta$ is given by:
$$\large
\Theta = arctan\Big(\frac{2B}{A-C-R} \Big)
$$
This is the basic equation that doesn't employ the eigenvalues. I assume the entirety of the $b,a =$ equation is related to that, but it is 8:00 PM and I want to rest my weary eyes. This is a project for another time. 

I could use this to write my own script and see how that fares compared to the other ones, but again I am just going to this later or over the weekend. I need rest.