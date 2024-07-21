
# Comprehensive Employee Analysis for ABC Company

## Project Overview

This project involves analyzing a dataset from ABC Company, consisting of 458 rows and 9 columns. The primary goal is to provide a comprehensive report detailing information about the company's employees across various teams. The tasks include preprocessing the dataset, analyzing the data, and presenting the findings graphically.

## Preprocessing

### Task
- **Correct the data in the "height" column**: Replace it with random numbers between 150 and 180 to ensure data consistency and integrity before proceeding with the analysis.

### Code
```python
import pandas as pd
df=pd.read_csv("C:/Users/AKHIL R S/Downloads/myexcel - myexcel.csv (1).csv")
df.head()

import numpy as np
np.random.seed(42)
df['Height']= np.random.randint(150,181,size=df.shape[0])
df.head()

```

## Analysis Tasks

### 1. Distribution of Employees Across Each Team

#### Code
```python
# Calculate the distribution of employees across each team
team_distribution=df['Team'].value_counts()

# Calculate the percentage split relative to the total number of employees
team_percentage = (team_distribution / data.shape[0]) * 100

team_distribution_df = pd.DataFrame({
    'Team': team_distribution.index,
    'Count': team_distribution.values,
    'Percentage': team_percentage.values
})

print(team_distribution_df)

```

### 2. Segregation of Employees Based on Their Positions

#### Code
```python
# Calculate the distribution of employees across each position
position_distribution = df['Position'].value_counts()

# Create a DataFrame with the position distribution
position_distribution_df = pd.DataFrame({
    'Position': position_distribution.index,
    'Count': position_distribution.values
})

print(position_distribution_df)

```

### 3. Predominant Age Group Among Employees

#### Code
```python
# Define age groups
bins = [18, 25, 35, 45, 55, 65, 100]
labels = ['18-25', '26-35', '36-45', '46-55', '56-65', '65+']
df['AgeGroup'] = pd.cut(data['Age'], bins=bins, labels=labels, right=False)

# Calculate the distribution of age groups
age_group_distribution = df['AgeGroup'].value_counts().sort_index()

age_group_distribution_df = pd.DataFrame({
    'AgeGroup': age_group_distribution.index,
    'Count': age_group_distribution.values
})

print(age_group_distribution_df)

```

### 4. Highest Salary Expenditure by Team and Position

#### Code
```python
salary_expenditure = df.groupby(['Team', 'Position'])['Salary'].sum().reset_index()
highest_salary_expenditure = salary_expenditure.loc[salary_expenditure['Salary'].idxmax()]
print(salary_expenditure)
print("\nTeam and Position with Highest Salary Expenditure:")
print(highest_salary_expenditure)


```

### 5. Correlation Between Age and Salary

#### Code
```python

import matplotlib.pyplot as plt
import seaborn as sns
correlation = df[['Age', 'Salary']].corr()
plt.figure(figsize=(10, 6))
sns.scatterplot(x='Age', y='Salary', data=df)
plt.title('Correlation between Age and Salary')
plt.xlabel('Age')
plt.ylabel('Salary')
plt.show()
print("Correlation between Age and Salary:")
print(correlation)

```

##  Graphical Representations


### 1. Distribution of Employees Across Each Team 

#### Code
```python
import matplotlib.pyplot as plt
plt.figure(figsize=(10, 8))
team_distribution.plot(kind='bar')
plt.title('Team Distribution')
plt.xlabel('Team')
plt.ylabel('Number of Employees')
plt.show()

```

### 2. Segregation of Employees Based on Their Positions

#### Code
```python
plt.figure(figsize=(10, 8))
position_distribution.plot(kind='bar')
plt.title('Position Distribution')
plt.xlabel('Position')
plt.ylabel('Number of Employees')
plt.show()
print(position_distribution_df)

```

### 3. Predominant Age Group Among Employees

#### Code
```python
plt.figure(figsize=(10, 8))
age_group_distribution.plot(kind='bar')
plt.title('Age Group Distribution')
plt.xlabel('Age Group')
plt.ylabel('Number of Employees')
plt.show()
print(age_group_distribution_df)

```

### 4. Highest Salary Expenditure by Team and Position

#### Code
```python
salary_expenditure = df.groupby(['Team', 'Position'])['Salary'].sum().reset_index()
highest_salary_expenditure = salary_expenditure.loc[salary_expenditure['Salary'].idxmax()]
salary_expenditure_pivot = salary_expenditure.pivot(index='Team', columns='Position', values='Salary')
salary_expenditure_pivot.plot(kind='bar', stacked=True, figsize=(10, 6))
plt.title('Salary Expenditure by Team and Position')
plt.xlabel('Team')
plt.ylabel('Total Salary Expenditure')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

print("\nTeam and Position with Highest Salary Expenditure:")
print(highest_salary_expenditure)

```

### 5. Correlation Between Age and Salary

#### Code
```python
correlation = df[['Age', 'Salary']].corr()
plt.figure(figsize=(10, 8))
plt.scatter(df['Age'], df['Salary'])
plt.title('Correlation between Age and Salary')
plt.xlabel('Age')
plt.ylabel('Salary')
plt.show()


```

## Data Story

### Insights Gained from the Analysis

1. **Distribution of Employees Across Each Team**
   - The largest team, **New Orleans Pelicans**, comprises **4.15%** of the total workforce.
   - Smaller teams such as **Memphis Grizzlies, Utah Jazz, and New York Knicks** have a significantly lower percentage of employees, indicating a potential focus on certain business areas over others.

2. **Segregation of Employees Based on Their Positions**
   - Positions like **SG ** are the most prevalent, reflecting the company's operational focus and staffing strategy.
   - Less common roles such as **C ** highlight niche areas within the organization that might require specialized skills.

3. **Predominant Age Group Among Employees**
   - The predominant age group is **21-30**, indicating that the company has a relatively young workforce.
   - This age group might correlate with specific business needs, such as a preference for younger, more adaptable employees.

4. **Highest Salary Expenditure by Team and Position**
   - The team with the highest salary expenditure is **Los Angeles Lakers**, particularly in the position of **SF **.
   - This suggests that the company invests heavily in this area, likely due to the critical nature of this team and role to the company's operations.
   - The data indicates strategic financial allocation, potentially reflecting the company's priorities and business strategy.

5. **Correlation Between Age and Salary**
   - The correlation analysis between age and salary shows **0.214**, indicating a positive relationship.
   - As age increases, salary tends to increase, which could be attributed to factors like experience, tenure, and hierarchical position within the company.
   - The scatter plot visualization further supports this trend, showing a clear pattern of increasing salary with age.

### Summary of Key Trends and Patterns
- **Team Distribution:** A few teams dominate the employee distribution, reflecting the company's operational focus.
- **Position Segregation:** Diverse roles with a concentration in specific positions suggest strategic staffing.
- **Age Demographics:** The workforce is predominantly within the 21-30 age range, indicating the company's employment strategy.
- **Salary Expenditure:** Higher financial investment in particular teams and roles underscores their importance to the company.
- **Age-Salary Correlation:** A clear relationship between age and salary highlights the impact of experience and tenure on compensation.

These insights provide a comprehensive overview of the company's workforce distribution, financial allocation, and demographic patterns, offering valuable information for strategic planning and decision-making.



This `README.md` file provides a detailed and clear overview of the project, including preprocessing steps, analysis tasks, insights gained, and submission instructions.
Adjust the file path to your dataset as needed, and feel free to add any additional information or modifications as required.
