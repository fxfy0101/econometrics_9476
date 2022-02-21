# 9474 Advanced Topics in Econometrics II

## Homework 1

Design, code, and run a simulation exploring the sensitivity of IV estimates and standard confidence intervals to the strength of the instrument. Use sample size
$n = 100$ observations per dataset. Let

$Y_i = 0.4 + 0.8 X_i + U_i$

$$X_i = 0.5 + \gamma_1Z_i + V_i$$

$$\begin{bmatrix}U\\V\end{bmatrix} \sim N\left(\begin{bmatrix}0\\0\end{bmatrix}, \begin{bmatrix}1.0, 0.5\\0.5, 1.0\end{bmatrix}\right)$$

Each simulation runs 1,000 replications. In each simulation, $\gamma_1$ has different values so we can see how small it must be to start affecting the properties of the IV estimator and CIs.

Two packages are imported. `tidyverse` is used to make plots and `MASS` is used to generate bivariate normal random numbers.I defined functions to estimate first stage and second stage coefficient (constant excluded), fitted values, residuals, and the 2SLS variance and covariance matrix. Formulas are:

$$\hat{\beta}_{OLS} = (X'X)^{-1}X'y$$
$$\hat{y}_{OLS} = X(X'X)^{-1}X'y$$

$$\hat{\beta}_{2SLS} = (Z'X)^{-1}Z'y$$

$$\hat{y}_{2SLS} = X(Z'X)^{-1}Z'y$$

$$\hat{V}_{\hat{\beta}_{2SLS}} = (\hat{X}'X)^{-1}\left(\sum_{i = 1}^n\hat{U}_i^2\hat{X}_i\hat{X}_i'\right)(\hat{X}'X)^{-1}$$
where $\hat{U}_i$ is the residuals from the 2SLS estimation.
