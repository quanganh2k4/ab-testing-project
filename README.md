# MiniProject-E-commerce A/B Testing Analysis

## 1. Project Overview
This project analyzes the results of an A/B test performed by an e-commerce company. The primary goal is to help the company make a data-driven decision on whether to implement the new webpage (**New Page**) or keep the old one (**Old Page**).

The decision is based on analyzing the **Conversion Rate**—the percentage of users who decided to pay for the product after visiting the page.

## 2. Technologies Used
The project was implemented using **Python** in a Jupyter Notebook environment, utilizing powerful data analysis and statistical libraries:
- **Pandas & NumPy:** For data manipulation and cleaning.
- **Matplotlib & Seaborn:** For data visualization.
- **Statsmodels & Scipy:** For performing statistical hypothesis testing (Z-test) and Logistic Regression.

## 3. Dataset Description
The dataset `ab_data.csv` contains **294,478** rows, representing user sessions with the following features:

| Feature | Description |
| :--- | :--- |
| **user_id** | Unique identifier for each user. |
| **timestamp** | Time at which the user visited the webpage. |
| **group** | The test group: <br> - `control`: Users who saw the Old Page.<br> - `treatment`: Users who saw the New Page. |
| **landing_page** | The actual webpage served to the user (`old_page` or `new_page`). |
| **converted** | Target variable indicating the conversion status: <br> - `0`: Not Converted (Did not buy) <br> - `1`: Converted (Bought) |

## 4. Analysis Steps
The analysis follows standard data science procedures:

1.  **Data Cleaning:** Handling mismatch data (e.g., users in the `treatment` group who wrongly received the `old_page`) to ensure data integrity.
2.  **Probability Analysis:** Calculating the initial conversion rates based on the raw data.
3.  **Hypothesis Testing (A/B Test):** Establishing statistical hypotheses:
    * **Null Hypothesis ($H_0$):** $P_{new} \leq P_{old}$ (The new page's conversion rate is less than or equal to the old page's).
    * **Alternative Hypothesis ($H_1$):** $P_{new} > P_{old}$ (The new page's conversion rate is higher than the old page's).
4.  **Logistic Regression:** Using a regression model to verify the statistical results and explore other influencing factors.

## 5. Key Findings & Conclusion

### Statistical Results
- **p-value:** The calculated p-value is **0.8867**.
- **Significance Level ($\alpha = 0.05$):** Since $0.8867 > 0.05$, we **fail to reject the Null Hypothesis ($H_0$)**.
- **Observed Conversion Rates:**
    * Old Page: ~12.04%
    * New Page: ~11.88%

### Business Recommendation
Based on the statistical analysis, the final recommendation for the company is: **DO NOT deploy the new webpage.**

**Reasoning:**
1.  Statistically, the new webpage does not provide better conversion rates; in fact, it performed slightly worse than the old page.
2.  Implementing the new page would incur technical and training costs without delivering any clear revenue uplift.
3.  The company should stick to the old page and explore other potential improvements.
