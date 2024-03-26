 import pandas as pd
import matplotlib.pyplot as plt

 
url = 'https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv'
df = pd.read_csv(url)

 
df_global = df.drop(['Province/State', 'Country/Region', 'Lat', 'Long'], axis=1)
cases_global = df_global.sum()

 
cases_global.index = pd.to_datetime(cases_global.index)

 
plt.figure(figsize=(10, 6))
plt.bar(cases_global.index, cases_global.values, color='blue')
plt.title('Global COVID-19 Cases Over Time')
plt.xlabel('Date')
plt.ylabel('Number of Cases')
plt.grid(axis='y')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
