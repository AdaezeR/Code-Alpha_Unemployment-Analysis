# Code-Alpha_Unemployment-Analysis
This project analyzes unemployment rate data to uncover trends, patterns, and the impact of external shocks such as COVID-19 on employment levels.  Using Python, the dataset is cleaned, explored, and visualized to generate insights that can inform economic and social policy decisions
Objectives
Analyze unemployment rate trends over time
Perform data cleaning and preprocessing
Explore patterns across regions and time
Investigate the impact of COVID-19 on unemployment
Identify seasonal trends
Generate actionable insights
🛠️ Tools & Technologies
Python
Pandas
Matplotlib
Jupyter Notebook
📂 Dataset

The dataset contains:

Region
Date
Estimated Unemployment Rate (%)
Estimated Employed
Labour Participation Rate (%)
🧹 Data Cleaning

Key preprocessing steps:

Removed leading/trailing spaces in column names
Converted date columns to datetime format
Merged multiple datasets
Renamed columns for easier analysis
Sorted data chronologically
📊 Exploratory Data Analysis
🔹 1. Unemployment Trend Over Time
import pandas as pd
import matplotlib.pyplot as plt

df1 = pd.read_csv("Unemployment in India.csv")
df2 = pd.read_csv("Unemployment_Rate_upto_11_2020.csv")

df1.columns = df1.columns.str.strip()
df2.columns = df2.columns.str.strip()

df1['Date'] = pd.to_datetime(df1['Date'], dayfirst=True)
df2['Date'] = pd.to_datetime(df2['Date'], dayfirst=True)

df = pd.concat([df1, df2], ignore_index=True)

df.rename(columns={'Estimated Unemployment Rate (%)': 'Unemployment_Rate'}, inplace=True)

df = df.sort_values(by='Date')

plt.figure(figsize=(10,5))
plt.plot(df['Date'], df['Unemployment_Rate'])
plt.title("Unemployment Rate Over Time")
plt.xlabel("Date")
plt.ylabel("Unemployment Rate (%)")
plt.show()
🔹 2. Monthly Unemployment Trend
monthly_avg = df.groupby(df['Date'].dt.to_period('M'))['Unemployment_Rate'].mean()

monthly_avg.plot(figsize=(10,5), title="Monthly Average Unemployment Rate")
plt.ylabel("Unemployment Rate (%)")
plt.show()
🔹 3. Regional Analysis
region_avg = df.groupby('Region')['Unemployment_Rate'].mean().sort_values()

region_avg.plot(kind='barh', figsize=(8,6), title="Unemployment by Region")
plt.show()
🦠 COVID-19 Impact Analysis
covid_period = df[(df['Date'] >= '2020-03-01') & (df['Date'] <= '2020-12-31')]

plt.figure(figsize=(10,5))
plt.plot(covid_period['Date'], covid_period['Unemployment_Rate'])
plt.title("Unemployment Rate During COVID-19")
plt.xlabel("Date")
plt.ylabel("Unemployment Rate (%)")
plt.show()
🔍 Key Insights
📌 Impact of COVID-19
A sharp spike in unemployment was observed between March and May 2020
This corresponds with lockdowns and economic shutdowns
Informal sector workers were heavily affected
📌 Trend Analysis
Stable unemployment trends before 2020
Significant disruption during COVID-19
Gradual recovery post-lockdown
📌 Seasonal Patterns
Slight monthly fluctuations suggest seasonal employment trends
COVID-19 disrupted normal seasonal patterns
📌 Regional Differences
Some regions consistently exhibit higher unemployment rates
Indicates structural economic differences across regions
🧠 Policy Recommendations
Strengthen social safety nets during economic crises
Support small and medium enterprises (SMEs)
Promote digital and remote job opportunities
Improve labor market resilience
📈 Conclusion

The analysis highlights the significant impact of COVID-19 on unemployment rates and reveals underlying structural and seasonal trends. These insights can help guide economic planning and policy interventions.

🚀 How to Run This Project
Clone the repository:
git clone https://github.com/AdaezeR/Code Alpha_Unemployment-analysis.git
Navigate to the project folder:
unemployment-analysis
Install dependencies:
pip install pandas matplotlib
Run the Jupyter Notebook
👩‍💻 Author

Adaeze Rose

Data Analyst | Data Scientist
Skilled in Python, Data Analysis, and Visualization
