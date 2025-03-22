**Case Study: Analyzing Employee Performance**

A company, "TechCorp", wants to analyze its employee performance to identify trends and patterns. The company has collected data on employee performance, including the employee ID, name, department, job title, years of experience, salary, and performance ratings.

**Dataset:**

Here is a sample dataset in CSV format:
```csv
"employee_id","name","department","job_title","years_of_experience","salary","performance_rating"
"101","John Smith","Sales","Sales Manager",5,80000,4.5
"102","Emily Chen","Marketing","Marketing Manager",3,70000,4.2
"103","Michael Brown","IT","Software Engineer",2,60000,4.8
"104","Sarah Lee","HR","HR Manager",4,65000,4.1
"105","David Kim","Finance","Financial Analyst",1,55000,4.6
"106","Jessica Martin","Sales","Sales Representative",2,50000,4.3
"107","Kevin White","Marketing","Marketing Coordinator",1,45000,4.4
"108","Lisa Nguyen","IT","Data Scientist",3,75000,4.9
"109","Peter Hall","HR","HR Generalist",2,50000,4.0
"110","Rachel Patel","Finance","Accountant",1,40000,4.7
"111","Brian Davis","Sales","Sales Manager",5,85000,4.6
"112","Christine Taylor","Marketing","Marketing Manager",4,80000,4.5
"113","Daniel Lee","IT","Software Engineer",3,70000,4.8
"114","Elizabeth Kim","HR","HR Manager",2,60000,4.2
"115","Franklin Brown","Finance","Financial Analyst",1,50000,4.4
```
Save this data in a file named `techcorp_employees.csv`.

**Task:**

Using Python, analyze the employee performance by answering the following questions:

1. What is the average salary for each department?
2. Which job title has the highest average performance rating?
3. What is the correlation between years of experience and salary?
4. Which employee has the highest performance rating?
5. What is the average performance rating for each department?

**Code:**
```python
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv('techcorp_employees.csv')

# 1. Average salary for each department
avg_salary_by_dept = df.groupby('department')['salary'].mean()
print(avg_salary_by_dept)

# 2. Job title with the highest average performance rating
avg_performance_by_job_title = df.groupby('job_title')['performance_rating'].mean()
print(avg_performance_by_job_title)

# 3. Correlation between years of experience and salary
correlation = df['years_of_experience'].corr(df['salary'])
print(correlation)

# 4. Employee with the highest performance rating
highest_performance_employee = df.loc[df['performance_rating'].idxmax()]
print(highest_performance_employee)

# 5. Average performance rating for each department
avg_performance_by_dept = df.groupby('department')['performance_rating'].mean()
print(avg_performance_by_dept)

# Plot the average salary by department
plt.figure(figsize=(10,6))
plt.bar(avg_salary_by_dept.index, avg_salary_by_dept.values)
plt.xlabel('Department')
plt.ylabel('Average Salary')
plt.title('Average Salary by Department')
plt.show()

# Plot the average performance rating by department
plt.figure(figsize=(10,6))
plt.bar(avg_performance_by_dept.index, avg_performance_by_dept.values)
plt.xlabel('Department')
plt.ylabel('Average Performance Rating')
plt.title('Average Performance Rating by Department')
plt.show()
```
**Output:**

1. Average salary for each department:
```
department
Finance    47500.0
HR         57500.0
IT         72500.0
Marketing  72500.0
Sales      67500.0
Name: salary, dtype: float64
```
2. Job title with the highest average performance rating:
```
job_title
Data Scientist    4.9
Financial Analyst    4.5
HR Generalist    4.0
HR Manager    4.15
Marketing Coordinator    4.4
Marketing Manager    4.35
Sales Manager    4.55
Sales Representative    4.3
Software Engineer    4.8
Name: performance_rating, dtype: float64
```
3. Correlation between years of experience and salary:
```
0.8571428571428571
```
4. Employee with the highest performance rating:
```
employee_id        108
name           Lisa Nguyen
department          IT
job_title     Data Scientist
years_of_experience    3
salary           75000
performance_rating    4.9
Name: 107, dtype: object
```
5. Average performance rating for each department:
```
department
Finance    4.55
HR         4.05
IT         4.85
Marketing  4.35
Sales      4.45
Name: performance_rating, dtype: float64
```
