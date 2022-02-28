
# HousePrice-Regression
Documentation for HousePrice Regression problem from preprocessing to model fitting [(Notebook Link)](https://www.kaggle.com/harshitvish/da-assignment1/notebook) [(Github Link)](https://github.com/Shikhar03Stark/HousePrice-Regression)

## Steps followed
 1. Pre-processing

	 a. [Feature Selection](#feature-selection)

	 b. [Imputation](#imputation)

	 c. [Transformation and scaling](#transformation-and-scaling)

	 d. [PCA (dimensionality reduction)](#pca)

 2. [Linear Regression](#linear-regression)

	 a. Built-in LinearRegression Class (various algorithms)

	 b. Built-in Ridge Class (svd, eig solvers)

 3. [Validation Accuracy](#validation-accuracy)

 4. [Rank in Leaderboard](#rank-in-leaderboard)

---
### *Feature Selection*
Initial Dataset had 79 features (excluding ID and Output) and most were of object data-type.
I picked all features whose data-type matches one of the following
 - `int64`
 - `int32`
 - `float64`
 - `float32`

Which resulted in 37 features. Input dataset shape (1460, 37)

---
### *Imputation*
In the input dataset there were few features which had null values. I used median imputation for missing values.

---
### *Transformation and Scaling*
A lot of the features were skewed, I picked all the features whose skewness was outside the range of [-0.5, 0.5] and applied log transformation `log_e(1 + x)`.
After correcting skewness, I applied StandardScaler class on Input data so as to mean-center the data and reduce bias towards any one feature.

---
### *PCA*
After the previous pre-processing steps, I applied LinearRegression and gained close to 0.50 R2 score.
I then extracted Principle Components of Input (5 components) and then used it in Ridge to increase the R2 score.

---
### *Linear Regression*
I applied 2 built-in Regression models LinearRegression and Ridge.
I used 5 algorithms for LinearRegression Class
 - `svd`
 - `eig`
 - `qr`
 - `svd-qr`
 - `svd-jacobi`

I used 2 solvers for Ridge Class
 - `svd`
 - `eig`

And achieved similar results due to small input, transformation and rescaling.

---
### *Validation Accuracy*


|            | R2       | MAE          | MSE          |
|------------|----------|--------------|--------------|
| ridge_svd  | 0.563289 | 27204.097906 | 1.819488e+09 |
| ridge_eig  | 0.563289 | 27204.097906 | 1.819488e+09 |
| svd        | 0.511364 | 22100.095640 | 2.035823e+09 |
| eig        | 0.511364 | 22100.095640 | 2.035823e+09 |
| qr         | 0.511364 | 22100.095640 | 2.035823e+09 |
| svd-qr     | 0.511364 | 22100.095640 | 2.035823e+09 |
| svd-jacobi | 0.511364 | 22100.095640 | 2.035823e+09 |

### *Rank in Leaderboard*
Using only Built-in LinearRegression and Ridge Regression
I was placed at **4309** position.

RMSE: *1.61730*

Code: [Notebook Link](https://www.kaggle.com/harshitvish/da-assignment1/notebook)
