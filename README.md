# Project: Data Manipulation

## Overview
This project demonstrates data manipulation techniques in Python. It involves reading a dataset of dog information, which includes attributes such as name, breed, color, height, weight, and date of birth. The data is organized into a pandas DataFrame and displayed as a table for analysis.

## Key Features
- **Data Loading**: The dataset is loaded into a pandas DataFrame.
- **Data Display**: A table of dog attributes is displayed in a structured format, showcasing information such as name, breed, and physical characteristics.
- **Duplication Check**: Duplicate rows in the dataset are handled in further steps for analysis or cleaning.

## Data Sample
The dataset includes the following columns:

- **Name**: Dog's name (e.g., Max, Bella).
- **Breed**: Breed of the dog (e.g., Labrador, Poodle).
- **Color**: Color of the dog (e.g., Black, White).
- **Height**: Height of the dog in centimeters.
- **Weight**: Weight of the dog in kilograms.
- **Date of Birth**: The dog's birthdate.

### Sample Data Preview

| Index | Name    | Breed    | Color | Height (cm) | Weight (kg) | Date of Birth |
|-------|---------|----------|-------|-------------|-------------|---------------|
| 0     | Max     | Labrador | Black | 60          | 30          | 2018-06-20    |
| 1     | Bella   | Poodle   | White | 40          | 20          | 2019-03-14    |
| 2     | Charlie | Beagle   | Brown | 35          | 18          | 2017-09-25    |

## Requirements
- **Python 3.x**
- **pandas library**

## How to Run
1. Ensure that Python and pandas are installed on your machine.
2. Load the dataset into a pandas DataFrame.
3. Run the script to display the data in a table format.

### Code Example:
```python
import pandas as pd

# Load the dataset into a DataFrame
df = pd.read_csv('dogs.csv')

# Display the first few rows of the dataset
print(df.head())

# Check for duplicate rows
duplicates = df[df.duplicated()]
print(f"Duplicate rows:\n{duplicates}")

# Optionally remove duplicates
df_cleaned = df.drop_duplicates()

# Remove rows with missing values
df_cleaned = df_cleaned.dropna()

# Example: Average weight by breed
avg_weight_by_breed = df_cleaned.groupby('Breed')['Weight (kg)'].mean()
print(avg_weight_by_breed)

# Visualization of weight distribution
import matplotlib.pyplot as plt
import seaborn as sns

sns.histplot(df_cleaned['Weight (kg)'])
plt.show()
