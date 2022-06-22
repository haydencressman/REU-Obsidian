[[Table of Contents]]

## <u>Calculating Confidence Ellipse on Scatter Plot<u/>

### Explanation
The **Script** can be found [here](https://matplotlib.org/stable/gallery/statistics/confidence_ellipse.html) and the **explanation** that notes are taken from is found [here](https://carstenschelp.github.io/2018/09/14/Plot_Confidence_Ellipse_001.html).

---
This model uses the [Pearson's Correlation Coefficient](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient) as shown below:

$$\rho_{xy} = \frac{cov(x,y)}{\sigma_x\sigma_y}$$

Where $cov(x,y)$ is the **covariance** of $(x,y)$ and $\sigma_x$ and $\sigma_y$ are the **standard deviations** of $x$ and $y$ respectively. The standard deviations shown are pulled directly from the covariance matrix calculated within the python code. The code is shown further down below.

**Covariance** is again given by:

$$cov_{xy} = \frac{\Sigma(x_{i}- x_{m})(y_{i}- y_{m})}{N-1}$$

The numerator is basically the variance equation, where $x_i$ is the iterated value of $x$ and $x_m$ is the mean of $x$ values. This is the same for $y$. $N$ is the number of data points.

The radii is calculated as followed from $\rho$

$$Horizontal\:Radius = \sqrt{1+\rho}$$
$$Vertical\:Radius=\sqrt{1-\rho}$$

Then, rotate the ellipse 45 Degrees counter-clockwise
The size of the ellipse is designated by $n$ Standard Deviations from the mean center
Scaling the ellipse by $(2*n*\sigma_x)$ and $(2*n*\sigma_y)$ for each direction depending on how confident you want your interval to be.
The ellipse center is shifted to that it is about the point $[\mu_x,\mu_y]$ which is the mean of each sets of data on the scatter plot.
---
The **Pearson Coefficient** is normalized, meaning that the correlation values range from -1 to 1.
The coefficient $\rho$ basically provides a <u>**representation of the relation of the radii of the ellipse to it's center**</u> based on the dataset.

This means before modification, the ellipse is centered at the origin. There is a proof here that since the Pearson Coefficient is normalized to be in the range of -1 to 1, then the maximum radii of any side is going to be $\sqrt{2}$, at least from the origin. From the previously given equations for calculating the radii, this can be seen, as the maximum value can only be $\sqrt2$.

---
Essentially eigenvalues are used, however they are masked by the overall equations. The proof goes on to explain as such.
For a normalized dataset the eigenvalues $\lambda_1$ and $\lambda_2$ can be shown as thus,

$$\lambda_{1}= 1 + \rho$$
$$\lambda_{2}=1-\rho$$

The eigenvalue calculations of the covariance matrix of the two datasets (normalized) can be seen  below:

$$|\Sigma_N-\lambda\cdot I| = 0$$
Where $\Sigma_N$ is the normalized covariance matrix, $\lambda$ is an eigenvalue, and $I$ is the identity matrix.
These equations show that for $\lambda$ to make the determinant of $\Sigma_N$ zero in their difference are eigenvalues of the matrix $\Sigma_N$.
Broken down the Equation to produce eigenvalues is as follows:
$$\Bigg|\begin{bmatrix}1 & \rho\\\rho & 1\end{bmatrix}-\lambda\cdot\begin{bmatrix}1 & 0\\0&1\end{bmatrix}\Bigg| = 0$$
$$\Bigg|\begin{matrix}1-\lambda&\rho\\\rho&1-\lambda\end{matrix}\Bigg| = 0$$
$$(1-\lambda)^2-\rho^2=0$$
$$(1-\lambda)^2=\rho^2$$
This equation has two real toots as given by,
$$1-\lambda_{1}= \rho\quad and \quad 1+\lambda = \rho$$
Thus showing that beforehand the radii distances are in fact eigenvalues of the covariance matrix. To further prove _which_ eigenvalue relates to either axis, one can relate these eigenvalues to an eigenvector in order to get the direction. For this case the proof of $1-\rho=\lambda_2$ will be used to show negative direction.

The equation for eigenvector from corresponding eigenvalue is shown,
$$(\Sigma_N-(1-\rho)\cdot I)\cdot v_2=0$$
Where $v_2$ is the corresponding eigenvector for $\lambda_2$
$$\Bigg(\begin{bmatrix}1&\rho\\\rho&1\end{bmatrix}-\begin{bmatrix}1-\rho&0\\0&1-\rho\end{bmatrix}\Bigg)\cdot v_2=\begin{bmatrix}0\\0\end{bmatrix}$$
$$\begin{bmatrix}\rho&\rho\\\rho&\rho\end{bmatrix}\cdot \begin{bmatrix}v_{21}\\v_{22}\end{bmatrix} =\begin{bmatrix}0\\0\end{bmatrix} $$
$$\Bigg|\begin{bmatrix}\rho\cdot v_{21} +\rho\cdot v_{22} = 0\\\rho\cdot v_{21} + \rho\cdot v_{22} = 0\end{bmatrix}\Bigg|$$
$$\Bigg|\begin{matrix}v_{21} = -v_{22}\\v_{21}=-v_{22}\end{matrix}\Bigg|$$

Some steps were skipped but only in simple algebraic operations. This shows that for $1-\rho$ the eigenvector has the same absolute value however the signs are reverse. The same is proven for $1+\rho$ in this similar fashion, however the final matrix appears as such,
$$\Bigg|\begin{matrix}v_{12} = v_{11}\\v_{11}=v_{12}\end{matrix}\Bigg|$$

The slopes of these eigenvectors are going to be -1 and 1 respectively, or in other words $-45\degree$ or $45\degree$ respectively. This shows that $\sqrt{1+\rho}$ involves the ascending axis and $\sqrt{1-\rho}$ is the descending axis.

---
The code this proof is showing is shown below, with comments provided by the original poster of said code on the matplotlib library.

Some modifications were made, namely with the Global AREA variable being used to calculate the area of the ellipse based on the radii calculated.
### <u>python code
```python
def confidence_ellipse(x, y, ax, n_std=2.0, facecolor='none', **kwargs):
    """
    Create a plot of the covariance confidence ellipse of *x* and *y*.

    Parameters
    ----------
    x, y : array-like, shape (n, )
        Input data.

    ax : matplotlib.axes.Axes
        The axes object to draw the ellipse into.

    n_std : float
        The number of standard deviations to determine the ellipse's radiuses.

    **kwargs
        Forwarded to `~matplotlib.patches.Ellipse`

    Returns
    -------
    matplotlib.patches.Ellipse
    """
    global AREA
    
    if x.size != y.size:
        raise ValueError("x and y must be the same size")

    cov = np.cov(x, y)
    pearson = cov[0, 1]/np.sqrt(cov[0, 0] * cov[1, 1])
    # Using a special case to obtain the eigenvalues of this
    # two-dimensionl dataset.
    ell_radius_x = np.sqrt(1 + pearson)
    ell_radius_y = np.sqrt(1 - pearson)
    ellipse = ptch.Ellipse((0, 0), width=ell_radius_x * 2, height=ell_radius_y * 2,
                      facecolor=facecolor, **kwargs)

    # Calculating the stdandard deviation of x from
    # the squareroot of the variance and multiplying
    # with the given number of standard deviations.
    scale_x = np.sqrt(cov[0, 0]) * n_std
    mean_x = np.mean(x)

    # calculating the stdandard deviation of y ...
    scale_y = np.sqrt(cov[1, 1]) * n_std
    mean_y = np.mean(y)

    transf = mpl.transforms.Affine2D() \
        .rotate_deg(45) \
        .scale(scale_x, scale_y) \
        .translate(mean_x, mean_y)
    
    AREA = m.pi * scale_x * scale_y
    ellipse.set_transform(transf + ax.transData)
    return ax.add_patch(ellipse)
```
