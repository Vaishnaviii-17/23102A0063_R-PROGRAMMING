# Statistical Analysis of Palmer Penguins using R

## 📌 Overview

This project performs a comprehensive statistical analysis of the **Palmer Penguins dataset** using **R programming**.

The analysis focuses on understanding the physical characteristics of three penguin species — **Adelie, Chinstrap, and Gentoo** — with particular emphasis on **body mass** and **flipper length**.

The project demonstrates the application of descriptive statistics, hypothesis testing, effect-size analysis, ANOVA, non-parametric testing, and data visualization.

---

## 🎯 Objectives

* Analyze the physical characteristics of Palmer penguins using R.
* Calculate descriptive statistics for penguin body mass.
* Compare body mass between male and female penguins.
* Perform hypothesis testing using Welch's independent two-sample t-test.
* Calculate Cohen's d effect size.
* Determine whether body mass differs significantly among penguin species using One-Way ANOVA.
* Validate the ANOVA findings using the Kruskal-Wallis non-parametric test.
* Analyze the combined effects of species and sex using Two-Way ANOVA.
* Compare flipper lengths across penguin species.
* Visualize and interpret the statistical findings.

---

## 📊 Dataset

### Palmer Penguins Dataset

The project uses the `penguins` dataset provided by the **`palmerpenguins`** R package.

The dataset contains physical measurements and biological information about three penguin species:

* **Adelie**
* **Chinstrap**
* **Gentoo**

Important variables used in this analysis include:

| Variable            | Description                   |
| ------------------- | ----------------------------- |
| `species`           | Penguin species               |
| `sex`               | Penguin sex                   |
| `body_mass_g`       | Body mass in grams            |
| `flipper_length_mm` | Flipper length in millimeters |

Missing values in the variables required for individual analyses are filtered before performing statistical tests.

---

## 🛠️ Technologies & Libraries

### Programming Language

* R

### R Packages

```r
palmerpenguins
dplyr
ggplot2
e1071
moments
effsize
car
```

### Main Functions & Techniques

* `mean()`
* `median()`
* `min()`
* `max()`
* `var()`
* `sd()`
* `quantile()`
* `IQR()`
* `skewness()`
* `kurtosis()`
* `t.test()`
* `cohen.d()`
* `aov()`
* `TukeyHSD()`
* `kruskal.test()`
* `shapiro.test()`
* `leveneTest()`
* `ggplot()`

---

## 🔬 Analysis Performed

### 1. Descriptive Statistical Analysis

Descriptive statistics were calculated for `body_mass_g`, including:

* Mean
* Median
* Minimum
* Maximum
* Variance
* Standard deviation
* First quartile (Q1)
* Third quartile (Q3)
* Interquartile range (IQR)
* Skewness
* Kurtosis

Overall body mass statistics obtained from the analysis:

| Statistic          |  Value |
| ------------------ | -----: |
| Mean               | 4202 g |
| Median             | 4050 g |
| Minimum            | 2700 g |
| Maximum            | 6300 g |
| Standard Deviation |  802 g |
| Q1                 | 3550 g |
| Q3                 | 4750 g |
| IQR                | 1200 g |
| Skewness           |  0.468 |
| Kurtosis           |   2.27 |

Species-wise descriptive statistics were also calculated for Adelie, Chinstrap, and Gentoo penguins.

Gentoo penguins had the highest average body mass, while Adelie and Chinstrap penguins had considerably lower averages.

---

### 2. Hypothesis Testing — Male vs Female Body Mass

An independent **Welch Two-Sample t-test** was performed to determine whether male and female penguins have significantly different body masses.

#### Results

* **t-statistic:** -8.5545
* **Degrees of freedom:** 323.8959
* **p-value:** 4.793891 × 10⁻¹⁶
* **Female mean:** 3862.273 g
* **Male mean:** 4545.685 g
* **95% CI:** [-840.5783, -526.2453]

Since the p-value is far below 0.05, the null hypothesis is rejected.

**Conclusion:** There is a statistically significant difference between male and female penguin body mass. Male penguins have a higher average body mass.

---

### 3. Cohen's d Effect Size

Cohen's d was calculated to determine the practical magnitude of the difference between male and female body mass.

```text
Cohen's d = -0.9362
```

The absolute value is greater than 0.8, indicating a **large effect size**.

This shows that the difference between male and female body mass is not only statistically significant but also practically substantial.

---

### 4. One-Way ANOVA

A One-Way ANOVA was performed to determine whether mean body mass differs among:

* Adelie
* Chinstrap
* Gentoo

The analysis also included assumption checks using:

* Shapiro-Wilk normality test
* Q-Q plots
* Levene's test for homogeneity of variance

The ANOVA produced:

```text
F-statistic = 343.6263
df = (2, 339)
p-value = 2.892368 × 10⁻⁸²
```

Because the p-value is much smaller than 0.05, the null hypothesis is rejected.

**Conclusion:** Penguin body mass differs significantly among the three species.

---

### 5. Non-Parametric Analysis

Because some ANOVA assumptions showed possible violations, a **Kruskal-Wallis test** was also performed.

```text
Chi-squared = 217.6
df = 2
p-value < 2.2 × 10⁻¹⁶
```

The resulting p-value was highly significant.

The ANOVA and Kruskal-Wallis tests both indicated significant differences in body mass among the three species.

The agreement between the parametric and non-parametric approaches provides a more robust basis for the conclusion.

---

### 6. Two-Way ANOVA

A Two-Way ANOVA was performed to investigate the effects of both **species** and **sex** on body mass.

The model used was:

```r
body_mass_g ~ species * sex
```

Results:

| Factor        | F-value |  p-value |
| ------------- | ------: | -------: |
| Species       | 758.358 |  < 2e-16 |
| Sex           | 387.460 |  < 2e-16 |
| Species × Sex |   8.757 | 0.000197 |

Both **species** and **sex** had significant main effects.

The **species × sex interaction** was also statistically significant, indicating that the difference between male and female body mass varies depending on the penguin species.

---

### 7. Flipper Length Analysis

An additional One-Way ANOVA was performed using:

```text
flipper_length_mm
```

as the response variable and `species` as the grouping variable.

The ANOVA produced an extremely small p-value:

```text
p-value = 1.35171 × 10⁻¹¹¹
```

Therefore, flipper length differs significantly among the three penguin species.

### Tukey's HSD Post-Hoc Results

All three pairwise comparisons were statistically significant:

| Comparison         | Difference (mm) | Adjusted p-value |
| ------------------ | --------------: | ---------------: |
| Chinstrap − Adelie |            5.87 |  1.137329 × 10⁻⁸ |
| Gentoo − Adelie    |           27.23 |          < 0.001 |
| Gentoo − Chinstrap |           21.36 |          < 0.001 |

Gentoo penguins had the longest flippers, followed by Chinstrap and Adelie penguins.

---

## 📈 Visualizations

The project uses `ggplot2` and base R graphics to visualize the statistical results.

### Body Mass Visualizations

* Histogram of body mass
* Body mass boxplot by species
* Body mass boxplot by sex
* Density plot of body mass by species
* Q-Q plots for normality assessment

### ANOVA Visualization

* Interaction plot showing the relationship between species, sex, and body mass

### Flipper Length Visualization

* Species-wise comparison of flipper length

These visualizations make it easier to identify distributions, differences between groups, and possible assumption violations.

---

## 📋 Key Findings

### Body Mass

* Gentoo penguins have the highest average body mass.
* Male penguins are substantially heavier than female penguins.
* Body mass differs significantly among the three species.
* Adelie and Chinstrap penguins have relatively similar body mass compared with the much heavier Gentoo penguins.

### Flipper Length

* Flipper length differs significantly among all three species.
* Gentoo penguins have the longest flippers.
* Chinstrap penguins have longer flippers than Adelie penguins.
* All three species pairs show statistically significant differences in flipper length.

### Species and Sex

Both species and sex significantly influence body mass.

The significant interaction between species and sex indicates that the effect of sex is not identical across all species.

---

## 🏁 Overall Conclusion

The analysis demonstrates clear physical differences among **Adelie, Chinstrap, and Gentoo penguins**.

Gentoo penguins were consistently larger, showing both higher body mass and longer flippers. Sex also had a significant influence on body mass, with males generally being heavier than females.

The project demonstrates the practical application of:

* Descriptive statistics
* Welch's t-test
* Cohen's d effect size
* One-Way ANOVA
* Tukey's HSD
* Kruskal-Wallis test
* Two-Way ANOVA
* Assumption testing
* Statistical visualization

## Using both parametric and non-parametric methods strengthens the reliability of the statistical conclusions.

## ▶️ How to Run

### Option 1 — Google Colab

1. Open Google Colab.
2. Upload `R_Programming_6.ipynb`.
3. Select the **R runtime/kernel**.
4. Run the notebook cells sequentially.
5. The required R packages will be installed within the notebook.

### Option 2 — Local R / RStudio

Install R and RStudio, then install the required packages:

```r
install.packages("palmerpenguins")
install.packages("dplyr")
install.packages("ggplot2")
install.packages("e1071")
install.packages("moments")
install.packages("effsize")
install.packages("car")
```

Then open and execute:

```text
R_Programming_6.ipynb
```

---

## 📁 Project Structure

```text
R-Palmer-Penguins-Statistical-Analysis/
│
├── R_Programming_6.ipynb
└── README.md
```

---

## 👩‍💻 Author

**Vaishnavi Sawant**

B.Tech Computer Engineering
Vidyalankar Institute of Technology

---

## ⭐ Skills Demonstrated

`R` · `Statistical Analysis` · `Hypothesis Testing` · `ANOVA` · `Non-Parametric Testing` · `Data Visualization` · `ggplot2` · `Data Analysis` · `Descriptive Statistics` · `Statistical Inference`
