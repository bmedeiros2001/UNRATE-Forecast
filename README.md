# UNRATE-Forecast

This project forecasts U.S. unemployment rates using a linear regression approach with a Box-Cox transformation for better predictive accuracy. The model provides actionable insights for economic planning and labor market strategies by analyzing historical unemployment data and creating forward-looking estimates. Decision-makers can leverage these forecasts to inform policy adjustments, allocate resources, and anticipate labor force trends.

Accurate unemployment forecasts help policymakers, businesses, and analysts make informed decisions on budget allocation, workforce development, and economic policy. By anticipating shifts in the job market, organizations can strategically plan hiring, training, and resource distribution, minimizing risks and optimizing economic outcomes.

---

**Data Sources:**

| Variable | Role | Number of Records | Measurement Level | Metadata |
|----------|------|------------------|-------------------|----------|
| [U-3 (UNRATE)](https://fred.stlouisfed.org/series/UNRATE) | Target | 490 | Monthly | U-3 Unemployment Rate |
| [Initial Jobless Claims (ICSA)](https://fred.stlouisfed.org/series/ICSA) | Predictor/Independent | 2,130 | Weekly | The number of new unemployment claims filed each week. |
| [Job Openings (ITSIJR)](https://fred.stlouisfed.org/series/ITSIJR) | Predictor/Independent | 490 | Monthly | The number of available jobs that employers are trying to fill. |
| [Consumer Sentiment (UMCSENT)](https://fred.stlouisfed.org/series/UMCSENT) | Predictor/Independent | 490 | Monthly | A measure of consumer confidence and expectations about the economy. |
| [GDP Growth (GDPC1)](https://fred.stlouisfed.org/series/GDPC1) | Predictor/Independent | 165 | Quarterly | The rate of growth of the economy. |
| [Federal Fund Rate (FEDFUNDS)](https://fred.stlouisfed.org/series/FEDFUNDS) | Predictor/Independent | 490 | Monthly | The interest rate set by the Federal Reserve. |
| [S&P500 (SP500)](https://fred.stlouisfed.org/series/SP500) | Predictor/Independent | 14,914 | Daily | A stock market index that can reflect overall economic health. |
| [Consumer Price Index (CPIAUCSL)](https://fred.stlouisfed.org/series/CPIAUCSL) | Predictor/Independent | 490 | Monthly | A measure of inflation or the change in the price level of a basket of goods and services. |
| [Consumer Expenditure (PCE)](https://fred.stlouisfed.org/series/PCE) | Predictor/Independent | 490 | Monthly | The total value of goods and services consumed by households. |
| [House Price Index (CSUSHPINSA)](https://fred.stlouisfed.org/series/CSUSHPINSA) | Predictor/Independent | 490 | Monthly | A measure of changes in the prices of residential homes. |

---

**Time Frame:**
This analysis initially spans from January 1984 to October 2024, but forecasts rely on a more recent portion of the dataset beginning in December 2000.

**Inclusion Criteria:**
Data from the COVID‐19 period remains intact, reflecting its ongoing impact on economic conditions such as unemployment and consumer behavior. At the same time, we avoided including non‐lagged predictors that lack reliable future availability, ensuring that all variables we use can be legitimately forecast forward.

---

**Rationale for Lagged Variables:**
We incorporate six months of “lagged” values—for instance, prior months’ job openings and GDP—to capture the delayed influence of economic trends on current unemployment rates. This lagging strategy enriches the model by providing historical context: it accounts for the fact that changes in economic indicators do not manifest instantaneously in the labor market. By recognizing and encoding these time‐delayed effects, the model achieves a more robust and realistic projection of future unemployment trends.

**Example for Job Openings (JTSJOR):**

*JTSJOR: Job Openings for current month*

*JTSJOR (t-1): Job Openings from previous month*

*JTSJOR (t-2): Job Openings from two months ago*

*…*

*JTSJOR (t-6): Job Openings from six months ago*

<img width="721" alt="Image" src="https://github.com/user-attachments/assets/bc32ceb7-aa76-4fe0-8708-6188e51fb35e" />

---

## Summary of Steps
1. Data Cleaning
2. Box-Cox Transformation
3. Backward Regression
4. Forecast for December 2024

## Final Prediction: 4.27%
The actual UNRATE for December 2024 was 4.2%.

---

## Additional Breakdown:
### Step 1: Data Cleaning and Processing:
1. Remove PCE Column due to high correlations with other variables, especially the Consumer Price Index (CPIAUCSL) variable
2. Remove any NaN values in the predictor variables
3. Add Intercept Column with values 1
4. Time interval after processing: December 2000 - October 2024 (kept COVID data)
5. Removed non-lagged variables as they are not available for November 2024 value
6. Manually added GDP (t-1) and CSUSHPINSA (t-1) 

**Cleaned Training Data contains 280 rows and 49 columns (UNRATE + 8 predictors * 6 time lag columns)**

### Step 2: Box-Cox Transformation
The unemployment rate (UNRATE) exhibited skewness, violating the assumption of normality required for linear regression.

**Original Data:**

![image](https://github.com/user-attachments/assets/4a17cfa9-8619-4c8f-8207-ebc12decda9f)
![image](https://github.com/user-attachments/assets/92d0a612-87ae-406e-a524-2da534cd852a)



---

**After Box-Cox:**

![image](https://github.com/user-attachments/assets/4f9faada-a607-47ce-9ff5-1d1f5f74957f)
![image](https://github.com/user-attachments/assets/6f80886b-a45b-4085-b1cd-3b52d0d1d186)









