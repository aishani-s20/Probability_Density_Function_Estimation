# Air Quality Probability Density Function Estimation using Roll-Number-Parameterized Non-Linear Model

This project implements a non-linear data transformation and parameter estimation for **Nitrogen Dioxide (NO2)** levels based on the India Air Quality dataset. The transformation parameters are uniquely determined by a **University Roll Number** to ensure personalized modeling as required by the assignment guidelines.

---

## Project Overview
The core objective is to learn the parameters of a specific Probability Density Function (PDF) after applying a customized transformation to environmental data. The workflow includes:

* **Data Transformation**: Converting raw NO2 feature values ($x$) into a transformed variable ($z$) using a roll-number-specific sine-based model.
* **Parameter Estimation**: Learning values for $\lambda$, $\mu$, and $c$ for the predicted probability $\hat{p}(z)$.
* **Visualization**: Plotting the transformed data distribution against the fitted model.

---

## Mathematical Framework

### 1. Data Transformation
Each value of $x$ is transformed into $z$ using the following function:

$$z = T_{r}(x) = x + a_{r} \sin(b_{r} x)$$

**Parameter Derivation:**
For University Roll Number ($r$) **102303250**:
* $a_r = 0.05 \times (r \pmod 7)$
* $b_r = 0.3 \times ((r \pmod 5) + 1)$

### 2. Probability Density Function (PDF)
The transformed variable $z$ is modeled using the function:

$$\hat{p}(z) = c \cdot e^{-\lambda(z-\mu)^{2}}$$

The parameters are estimated in the implementation using Maximum Likelihood Estimation (MLE) principles:
* **$\mu$**: The mean of the transformed data $z$.
* **$\lambda$**: Derived from variance ($\sigma^2$), where $\lambda = \frac{1}{2\sigma^2}$.
* **$c$**: The normalization constant, $c = \frac{1}{\sqrt{2\pi\sigma^2}}$.

---

## Implementation Results

### Dataset
* **Source**: [India Air Quality Data](https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data)
* **Target Feature**: `no2`

### Calculated Parameters (Roll No: 102303250)
| Parameter | Value |
| :--- | :--- |
| **$a_r$** | 0.0 |
| **$b_r$** | 0.3 |
| **Estimated $\mu$** | 25.809623 |
| **Estimated $\lambda$** | 0.001460 |
| **Estimated $c$** | 0.021561 |

---

## Visualization
The project includes a visualization component that compares the histogram of the transformed data ($z$) with the mathematically estimated PDF curve.



* **Transformed Data**: Displayed as a blue-shaded histogram showing the actual density of $z$.
* **Estimated PDF**: Represented by a red line following the learned parameters $\lambda$, $\mu$, and $c$.
