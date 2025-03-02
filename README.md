# Data-Analysis-AI
# Telco Customer Churn Prediction Using AI

## Research Question
How can artificial intelligence techniques effectively predict customer churn in the telecom industry? This project explores whether AI models can use customer demographics and service usage data to identify high-risk churn profiles, enabling proactive retention strategies.

## Dataset Information
- **Dataset Name:** Telco Customer Churn Dataset
- **Location/Path:** `data/telco_customer_churn.csv`
- **Description:** The dataset contains customer records from a telecommunications company. It includes information such as customer demographics, account details, service subscriptions, and whether a customer has churned.

## Variables Description
Key variables selected for the analysis include:
- **customerID:** Unique identifier for each customer.
- **gender:** Customer's gender.
- **SeniorCitizen:** Indicator (0 = No, 1 = Yes) if the customer is a senior citizen.
- **Partner:** Whether the customer has a partner.
- **Dependents:** Whether the customer has dependents.
- **tenure:** Number of months the customer has stayed with the company.
- **MonthlyCharges:** The amount billed per month.
- **TotalCharges:** Total amount charged over the customer's tenure.
- **TotalServices:** *Calculated variable* representing the total number of services subscribed (e.g., PhoneService, InternetService, etc.).

## Descriptive Statistics
The table below summarizes descriptive statistics for five key numerical variables from the dataset:

| Variable         | Count | Mean    | Std    | Min    | 25th  | Median  | 75th   | Max     |
|------------------|-------|---------|--------|--------|-------|---------|--------|---------|
| **tenure**       | 7032  | 32.37   | 24.56  | 0      | 9     | 29      | 56     | 72      |
| **MonthlyCharges** | 7032  | 64.76  | 30.09  | 18.25  | 41.22 | 70.35   | 89.85  | 118.75  |
| **TotalCharges** | 7032  | 2283.30 | 2266.77| 18.80  | 401.45| 1397.45 | 3794.25| 8684.80 |
| **SeniorCitizen**| 7032  | 0.16    | 0.37   | 0      | 0     | 0       | 0      | 1       |
| **TotalServices**| 7032  | 2.80    | 1.20   | 0      | 2     | 3       | 4      | 5       |

## Code
Below is an example Python snippet that was used to generate the descriptive statistics table:

```python
import pandas as pd

# Load the dataset
df = pd.read_csv('data/telco_customer_churn.csv')

# Create a calculated variable 'TotalServices'
# Assuming these columns indicate service subscriptions with 'Yes' or 'No'
service_columns = ['PhoneService', 'MultipleLines', 'InternetService', 'OnlineSecurity', 'TechSupport']
df['TotalServices'] = df[service_columns].apply(lambda x: sum(x == 'Yes'), axis=1)

# Select key numerical variables for descriptive statistics
selected_vars = ['tenure', 'MonthlyCharges', 'TotalCharges', 'SeniorCitizen', 'TotalServices']
desc_stats = df[selected_vars].describe()

print(desc_stats)
