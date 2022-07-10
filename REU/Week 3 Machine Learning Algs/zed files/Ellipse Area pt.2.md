[[Table of Contents W3]]

## Problems
Noticeable issues were found with the area calculated from the first algorithm. Never outright trust a man on github. A new algorithm was found that does essentially the same thing except mostly focuses on the eigenvalues and eigenvectors instead of going through the Pearson coefficient to obtain them. 

## Going over the new Code

---
The new code essentially doesn't use the Pearsons Coefficient for eigenvalues and just uses numpy functions instead. The code can be seen below. The code can be found [here](https://stackoverflow.com/questions/20126061/creating-a-confidence-ellipses-in-a-sccatterplot-using-matplotlib) also.

```python
# Code from Stack Overflow Begins -----------------------------
def eigsorted(cov):
    vals, vecs = np.linalg.eigh(cov)
    order = vals.argsort()[::-1]
    return vals[order], vecs[:,order]

x = xval
y = yval

nstd = 2.0
ax = plt.subplot(111)

cov = np.cov(x, y)
vals, vecs = eigsorted(cov)
theta = np.degrees(np.arctan2(*vecs[:,0][::-1]))
w, h = 2 * nstd * np.sqrt(vals)
AREA = w * h
ell = Ellipse(xy=(np.mean(x), np.mean(y)),
              width=w, height=h,
              angle=theta, color='red')
ell.set_facecolor('none')
ax.add_artist(ell)
# Code from Stack Overflow Ends -----------------------------
```

Where the function `eigsorted` is written and then later calculations of the covariance is obtained. Again, the covariance is determined from:

$$cov_{xy} = \frac{\Sigma(x_{i}- x_{m})(y_{i}- y_{m})}{N-1}$$

The explanation of this and more can be seen in [[Confidence Ellipse]].

Eigenvectors are obtained by calculating the eigenvalues $\lambda_1$ and $\lambda_2$ from a given matrix $A$. Then you use the equations
$$
A\cdot v_{1}=\lambda_{1}\cdot v_1
$$

$$
(A-\lambda_{1})\cdot v_1=0
$$
Getting it all the way to the end we have
$$
(X\cdot v_{1}) = X\cdot 
\begin{bmatrix}
v_{1,1}\\v_{1,2}
\end{bmatrix} = 0
$$
Where $X$ is the result of subtracting the eigenvalues from matrix $A$. This was an example of a 2x2 matrix $A$ also.
With matrix math the eigenvectors can be obtained through simple choice of values that adhere to the ratio given by the completed equation.

---
The code in steps:
1. obtain the covariance of the x and y values.
2. send the covariance to a function. Within the function the use of `np.linalg.eigh()` is used. The function can be found [here](https://numpy.org/doc/stable/reference/generated/numpy.linalg.eig.html) on the numpy.org website. It returns two arrays, `w` and `v`. w being the eigenvalues and v being the eigenvectors associated.
3. Then it used the argsort() function which is used later to get the indices of the eigenvalues and eigenvectors and order them later on.
4. the `eigsorted()` function just sorts the eigenvalues and eigenvectors since when they are obtained they may or may not be in the correct order.
5. next `theta` is calculated from the inverse tangent of the eigenvectors and returned in degree value. <U>this is necessary for displaying the ellipse on the graph but is not necessary for calculations.</U>
6. Get the area from the width and height calculations. The width and height of the ellipse is found from $2 *\: \: Number\:of\:Standard\:Deviations\:*\sqrt{eigenvalues}$. <u>I am still confused as to why this is how it works but I will look more into it.</u>
7. Display the scatter plot, the ellipse, and output the area. ==The area can be later written to a text document, an excel file, or onto a google spreadsheet for posterity later==, but for now this works.