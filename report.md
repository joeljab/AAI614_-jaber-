# Linear Regression Report: Adult Census Income Dataset

## Objective

This report summarizes a linear regression analysis using the Kohavi & Becker extraction of the 1994 U.S. Census Adult dataset. The primary goal is to examine relationships among age, education_num, and hours_per_week, and to evaluate how demographic characteristics influence variation in work hours. In addition, correlation and covariance analyses are conducted to assess the strength, direction, and statistical significance of pairwise relationships among these variables.

---

## Data Preparation and Exploration

The dataset contains both numeric and categorical variables, consistent with the published data dictionary.

Missing values are encoded as ? (sometimes with leading spaces) and were recoded as NaN for proper statistical handling.

The key numeric variables examined in this analysis include:

* age
* education_num (years of completed education)
* hours_per_week

Initial exploratory analysis showed that:

* age follows a slightly right-skewed distribution.
* education_num is discrete and bounded (approximately 1–16).
* hours_per_week is right-skewed, with clustering around full-time work (40 hours).

Pairwise Pearson correlations were computed among age, education_num, and hours_per_week to assess preliminary relationships before regression modeling.

---

## Regression Models

Three nested linear regression models were estimated:

Model 1:
hours_per_week ~ age

Model 2:
hours_per_week ~ age + education_num

Model 3:
hours_per_week ~ age + education_num + sex

These models progressively evaluate whether education and sex explain additional variation in hours worked beyond age alone.

---

## Interpretation Framework

The coefficient for age represents the expected change in weekly work hours for each additional year of age.

The coefficient for education_num indicates the expected difference in weekly hours associated with each additional year of education.

The coefficient for sex (if included) represents the average difference in weekly hours between males and females, holding other variables constant.

Positive coefficients indicate an increase in weekly hours associated with the predictor, while negative coefficients indicate a decrease.

---

## Model Selection

Model comparison among nested candidates is based on:

* Adjusted R² (higher values indicate better explanatory power), and
* AIC/BIC (lower values indicate better model fit with appropriate complexity penalties).

The preferred model balances improved fit with interpretability. In this analysis, adding education_num improves explanatory power modestly, while adding sex further explains variation in hours worked, though the overall R² remains moderate.

This suggests that while demographic characteristics contribute to explaining work hours, substantial unexplained variation remains.

---

## Correlation and Covariance Findings

Pairwise Pearson correlations were computed among age, education_num, and hours_per_week.

* education_num and hours_per_week show a weak positive correlation (|r| > 0.1).
* age and education_num show a weak positive correlation.
* age and hours_per_week show a very weak relationship.

For pairs where |r| > 0.1, statistical tests confirmed that correlations are significantly different from zero (p < 0.05). Due to the large sample size, even small correlations are statistically significant, though effect sizes remain modest.

The correlation between education_num and age was also computed separately for males and females. In both subgroups, the relationship is weak and positive, with similar magnitude and statistical significance. This is expected, as educational attainment generally follows a similar life-cycle pattern across genders.

The covariance matrix for education_num and hours_per_week shows a positive covariance, indicating that the variables tend to increase together. However, covariance depends on measurement scale, so correlation provides a more interpretable standardized measure of association.

---

## Conclusion

This analysis addresses the required components of the assignment: data cleaning and missingness handling, distributional assessment, nested linear regression modeling, model comparison using fit statistics, and correlation/covariance interpretation.

The results show statistically significant but weak relationships among age, education level, and weekly work hours. Education and age are positively associated with hours worked, but the magnitude of these effects is modest.

Overall, while demographic variables contribute to explaining variation in labor supply, the findings highlight the complexity of work behavior and the importance of additional socioeconomic factors not included in this simplified regression framework.

The accompanying notebook contains complete executable code and clearly labeled sections corresponding to each analytical step.
