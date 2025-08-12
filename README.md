import pandas as pd
import matplotlib.pyplot as plt
from scipy.stats import linregress

df = pd.read_csv('sea_level_data.csv')

plt.scatter(df['Year'], df['Sea_Level'], color='blue', label='Actual Data')

res = linregress(df['Year'], df['Sea_Level'])
predicted = res.intercept + res.slope * df['Year']

plt.plot(df['Year'], predicted, color='red', label='Prediction')

plt.title('Sea Level Predictor')
plt.xlabel('Year')
plt.ylabel('Sea Level (mm)')
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()

print(f"Regression slope (annual increase): {res.slope:.2f} mm/year")
print(f"Intercept: {res.intercept:.2f}")

