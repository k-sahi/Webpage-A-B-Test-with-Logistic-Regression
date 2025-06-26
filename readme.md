# A/B Test Analysis for a New Webpage Design

## Project Overview

This project analyzes the results of an A/B test conducted to determine if a new webpage design leads to a higher conversion rate than the old design. The analysis includes:
1.  **Data Cleaning:** Handling mismatched data, duplicate entries, and ensuring data integrity.
2.  **Statistical A/B Test:** A rigorous Z-test for proportions to determine if the observed difference in conversion rates is statistically significant.
3.  **Logistic Regression Modeling:** A deeper dive to understand the impact of the new page while controlling for other factors like the time of day and day of the week.

**Conclusion:** The analysis concluded that there is no statistically significant evidence to suggest the new page performs better than the old one. Therefore, the recommendation is **not to launch the new page**.

## Dataset

The dataset used is `ab_data.csv`, which contains user data for the A/B test. Each row represents a user and includes the following columns:
-   `user_id`: A unique identifier for each user.
-   `timestamp`: The time at which the user viewed the page.
-   `group`: Which group the user was in (`control` or `treatment`).
-   `landing_page`: Which page the user saw (`old_page` or `new_page`).
-   `converted`: Whether the user converted (`1`) or not (`0`).

## Methodology

### 1. Data Cleaning
-   Removed 3,893 rows where the `group` and `landing_page` did not align (e.g., control group seeing the new page).
-   Removed 1 duplicate `user_id` to ensure each user is counted only once.
-   The final cleaned dataset contains 290,584 unique users.

### 2. A/B Test (Z-test)
A one-tailed Z-test was performed to test the hypothesis that the new page's conversion rate is greater than the old page's.
-   **Null Hypothesis (H₀):** The new page's conversion rate is less than or equal to the old page's. (P_new <= P_old)
-   **Alternative Hypothesis (H₁):** The new page's conversion rate is greater than the old page's. (P_new > P_old)
-   **Significance Level (α):** 0.05

### 3. Logistic Regression
A logistic regression model was built to predict conversion based on the group, hour of the day, and day of the week. This helps confirm the A/B test results while checking for confounding variables.

## Key Findings

1.  **A/B Test Result:** The Z-test yielded a **p-value of approximately 0.905**. Since this is much higher than the significance level of 0.05, we **fail to reject the null hypothesis**.
2.  **Logistic Regression Result:** The coefficient for the treatment group (`group_treatment`) in the logistic regression model was not statistically significant (p-value ≈ 0.19). This confirms the A/B test result, showing that the new page has no significant impact on conversion when controlling for other factors.
3.  **Final Recommendation:** **Do not launch the new webpage.** The data strongly suggests it does not improve the conversion rate. Resources should be re-allocated to designing a different page or optimizing other identified factors.

## How to Run This Project

1.  Clone this repository to your local machine:
    ```bash
    git clone https://github.com/your-username/ab-test-analysis.git
    ```
2.  Navigate to the project directory:
    ```bash
    cd ab-test-analysis
    ```
3.  Install the required Python libraries:
    ```bash
    pip install -r requirements.txt
    ```
4.  Launch Jupyter Notebook and open the `ab_test_analysis.ipynb` file to view and run the analysis.
    ```bash
    jupyter notebook
    ```

## Dependencies
-   pandas
-   numpy
-   statsmodels
-   matplotlib
-   seaborn
-   notebook