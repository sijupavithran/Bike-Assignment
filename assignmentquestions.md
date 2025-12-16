# Assignment-based and General Subjective Questions

## Assignment-based Subjective Questions

### Question 1: Categorical Variables Analysis

**From your analysis of the categorical variables from the dataset, what could you infer about their effect on the dependent variable?**

The categorical variables from the dataset are Season, Weathersit, Holiday, and Year as these can be clearly split into categories. The following can be inferred:

#### Seasonality
Spring has the lowest demand. Rentals in summer, fall, and winter are higher than those in spring.

#### Holiday Impact
There is a close to 10% drop in bike rentals during holidays compared to working days.

#### Yearly Trend
There is an increase in bike rentals in 2019 compared to 2018, which indicates an overall increase in demand over the year.

### Question 2: Importance of drop_first=True

**Why is it important to use `drop_first=True` during dummy variable creation?**

This is crucial for preventing multicollinearity (specifically the "Dummy Variable Trap") and ensures the creation of independent variables.

---

## General Subjective Questions

### Question 1: Linear Regression Algorithm

**Explain the linear regression algorithm in detail.**

Simple linear regression is a statistical method for establishing the relationship between two variables using a straight line. The line is drawn by finding the slope and intercept, which define the line and minimize regression errors.

#### Basic Concepts

The simplest form has one *x* variable (independent) and one *y* variable (dependent). The independent variable is what you use to predict the dependent variable.

#### Formula

The formula for simple linear regression is:

$$h(x) = y = \beta_0 + \beta_1 x + e$$

Where:
- **y**: Predicted value of the dependent variable.
- **β₀**: Intercept (predicted value of *y* when *x* = 0).
- **β₁**: Regression coefficient (how much we expect *y* to change as *x* increases).
- **x**: Independent variable.
- **e**: Error of the estimate.

#### Multiple Linear Regression

When predicting complex processes, use multiple linear regression:

$$h(x_1, x_2, \ldots, x_k) = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \cdots + \beta_k x_k$$

#### Assumptions of Linear Regression

1. **Linearity**: The relationship between *x* and *y* should be linear. (Check with a scatterplot).

2. **Independence of Errors**: Data should be independent of errors. (Check by examining a scatterplot of residuals vs. fits).

3. **Normal Distribution**: Residuals should be normally distributed. (Check with a histogram of residuals or Q-Q plot).

4. **Variance Equality (Homoscedasticity)**: Data should have equal variances. (Check by examining a scatterplot for outliers).

#### Cost Function

The Mean Squared Error (MSE) cost function is:

$$J(\theta) = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$$

Where $\hat{y}_i = \theta_0 + \theta_1 x_i$. The goal is to find optimal values for θ₀ and θ₁.

#### Gradient Descent Optimization

Gradient descent is an optimization technique to minimize prediction error:

1. Start with random values for slope and intercept.
2. Calculate the error between predicted and actual values.
3. Find how much each parameter contributes to the error (gradient).
4. Update parameters in the direction that reduces error.
5. Repeat until error is minimized.

#### Evaluation Metrics

**Mean Square Error (MSE)**: Sensitive to outliers. Lower values indicate better performance.

$$\text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$$

**Mean Absolute Error (MAE)**: Not sensitive to outliers. Lower values indicate better performance.

$$\text{MAE} = \frac{1}{n} \sum_{i=1}^{n} |Y_i - \hat{Y}_i|$$

**Root Mean Squared Error (RMSE)**:

$$\text{RMSE} = \sqrt{\frac{\sum_{i=1}^{n} (y_{i,\text{actual}} - y_{i,\text{predicted}})^2}{n}}$$

**R-Squared (R²)**: Indicates the proportion of variance explained. Range: 0 to 1. Higher is better.

$$R^2 = 1 - \frac{\text{RSS}}{\text{TSS}}$$

**Adjusted R²**: Penalizes the addition of useless predictors to prevent overfitting.

$$\text{Adjusted } R^2 = 1 - \frac{(1 - R^2)(n - 1)}{n - k - 1}$$

#### Lasso Regression (Regularization)

Lasso adds a penalty term to prevent overfitting:

$$J(\theta) = \frac{1}{2m} \sum_{i=1}^{n} (\hat{y}_i - y_i)^2 + \lambda \sum_{j=1}^{k} |\theta_j|$$

### Question 2: Anscombe's Quartet

**Explain Anscombe's quartet in detail.**

Anscombe's quartet demonstrates the importance of visualizing data before applying algorithms to build models. It consists of four datasets that have nearly identical simple descriptive statistics (mean, variance, correlation, and regression line), yet appear very different when graphed.

Data features must be plotted to identify anomalies such as outliers, data diversity, and linear separability.

### Question 3: Pearson's R

**What is Pearson's R?**

The Pearson product-moment correlation coefficient (denoted by *r*) measures the strength of a linear association between two variables.

- **Range**: -1 to +1
- **r = 0**: No association between variables.
- **r > 0**: Positive association (one variable increases, so does the other).
- **r < 0**: Negative association (one variable increases, the other decreases).
- **r = ±1**: Perfect linear relationship.

### Question 4: Scaling

**What is scaling? Why is scaling performed? What is the difference between normalized and standardized scaling?**

#### Definition

Scaling is a geometric change that linearly enlarges or reduces values.

#### Why Scaling is Performed

- Data preprocessing to normalize data within a specific range.
- Accelerates algorithmic calculations (helps Gradient Descent converge faster).
- Handles features with different magnitudes, units, and ranges (e.g., comparing "Age" vs "Salary").

#### Types

**Normalized Scaling (Min-Max)**: Values fall between 0 and 1.

$$x_{\text{normalized}} = \frac{x - x_{\min}}{x_{\max} - x_{\min}}$$

**Standardized Scaling (Z-score)**: Values have mean 0 and standard deviation 1.

$$x_{\text{standardized}} = \frac{x - \bar{x}}{\sigma}$$

### Question 5: VIF Becoming Infinite

**You might have observed that sometimes the value of VIF is infinite. Why does this happen?**

#### Answer

Variance Inflation Factor (VIF) becomes infinite when a predictor variable is perfectly linearly correlated with one or more other predictor variables (Perfect Multicollinearity).

#### Mathematical Explanation

VIF for a predictor X_i is defined as:

$$\text{VIF}_i = \frac{1}{1 - R_i^2}$$

Where R²_i is the R-squared value obtained by regressing X_i on all other predictors.

#### When VIF → ∞

If variable X_i can be exactly predicted from other predictors, then R²_i = 1.

Substituting this into the formula:

$$\text{VIF}_i = \frac{1}{1 - 1} = \frac{1}{0} = \infty$$

### Question 6: Q-Q Plot

**What is a Q-Q plot? Explain the use and importance of a Q-Q plot in linear regression.**

A Q-Q plot (quantile-quantile plot) is a scatterplot that compares the quantiles of two distributions. Typically, one distribution is observed data (your residuals) and the other is a theoretical reference distribution (usually the Normal Distribution).

#### Interpretation

- **Points on 45-degree line**: Data closely follow the reference distribution (Normality).
- **Curved points/Deviation**: Data are skewed, have heavy tails, or are not normal.

#### Importance in Linear Regression

It is used to check the Normality Assumption of the residuals. If the residuals are not normally distributed, the confidence intervals and hypothesis tests regarding the regression coefficients may not be valid.
