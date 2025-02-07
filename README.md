# UNRATE-Forecast

## Predict U-3 Labor Underutilization Rate of December 2024
**Summary:** This model will predict U-3 Labor Underutilization Rate for December 2024 (November 1st, 2024). Modeled with Multiple Linear Regression Model using the predictors in the table below, all converted to a monthly level, for the time period Jan 1984 to Oct 2024.

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


**Time Frame:**
This analysis initially spans from January 1984 to October 2024, but forecasts rely on a more recent portion of the dataset beginning in December 2000.

**Inclusion Criteria:**
Data from the COVID‐19 period remains intact, reflecting its ongoing impact on economic conditions such as unemployment and consumer behavior. At the same time, we avoided including non‐lagged predictors that lack reliable future availability, ensuring that all variables we use can be legitimately forecast forward.

**Rationale for Lagged Variables:**
We incorporate six months of “lagged” values—for instance, prior months’ job openings and GDP—to capture the delayed influence of economic trends on current unemployment rates. This lagging strategy enriches the model by providing historical context: it accounts for the fact that changes in economic indicators do not manifest instantaneously in the labor market. By recognizing and encoding these time‐delayed effects, the model achieves a more robust and realistic projection of future unemployment trends.

**Example for Job Openings (JTSJOR):**

*JTSJOR: Job Openings for current month*

*JTSJOR (t-1): Job Openings from previous month*

*JTSJOR (t-2): Job Openings from two months ago*

*…*

*JTSJOR (t-6): Job Openings from six months ago*

<img src="Screenshot 2025-02-07 at 12.47.36 PM.png" alt="image" width="700"/>

