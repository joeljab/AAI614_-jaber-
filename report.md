# Linear Regression Report: Adult Census Income Dataset

## Objective
This report summarizes a linear regression analysis using the Kohavi & Becker extraction of the 1994 U.S. Census Adult dataset. The outcome variable is **hours_per_week**, and the main predictor is **sex**, with additional controls for **education_num** and **gross_income_group**.

## Data Preparation and Exploration
- The dataset contains a mix of numeric and categorical variables, consistent with the data dictionary.
- Missing values are encoded as `?` (sometimes with leading spaces) and were recoded as `NaN`.
- `capital_gain` and `capital_loss` are typically highly right-skewed and mostly zero. Because of this zero inflation, they can be meaningfully transformed to categorical bins (for example: none/low/high).
- `fnlwgt` is a sampling weight and is usually right-skewed rather than symmetric. Comparing distributions by sex can reveal whether weights differ systematically between men and women.
- If extreme `fnlwgt` values are considered outliers for analysis stability, they may be set to missing (for example, above the 99th percentile), as long as this decision is explicitly documented.

## Regression Models
Three nested linear models are estimated:
1. **Model 1:** `hours_per_week ~ sex`
2. **Model 2:** `hours_per_week ~ sex + education_num`
3. **Model 3:** `hours_per_week ~ sex + education_num + gross_income_group`

### Interpretation Framework
- The coefficient for `sex` indicates the average difference in weekly work hours between men and women.
- Adding `education_num` checks whether differences by sex persist after controlling for education.
- Adding `gross_income_group` evaluates whether income category explains additional variation in hours worked.

### Model Selection
For choosing the best model among nested candidates, compare:
- **Adjusted R²** (higher is better), and
- **AIC/BIC** (lower is better).

A practical decision rule is to prioritize a model with better fit metrics while retaining interpretability.

## Correlation and Covariance Findings
- Pairwise Pearson correlations are computed among `age`, `education_num`, and `hours_per_week`.
- Any pair with `|r| > 0.1` should be tested against 0 for statistical significance.
- Correlation between `education_num` and `age` should also be compared by sex using subgroup-specific tests.
- The covariance matrix for `education_num` and `hours_per_week` indicates whether they vary in the same direction (positive covariance) or opposite directions (negative covariance), and by how much in raw units.

## Conclusion
This analysis pipeline addresses all required assignment components: data typing and missingness checks, distributional analysis and transformation decisions, weighted variable assessment, regression modeling with controls, and correlation/covariance interpretation. The accompanying notebook (`regression.ipynb`) contains complete executable code and section headers aligned to each assignment prompt.
