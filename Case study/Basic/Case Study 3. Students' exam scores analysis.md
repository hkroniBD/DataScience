### Task Assignment

**Objective:** Perform a simple data analysis using Python on a dataset containing information about students' exam scores. The dataset includes the following columns: `Student_ID`, `Name`, `Age`, `Gender`, `Math_Score`, `Science_Score`, and `English_Score`.

**Tasks:**
1. Load the dataset from a CSV file.
2. Perform basic data exploration (e.g., display the first few rows, check for missing values, etc.).
3. Calculate the average score for each subject (Math, Science, English).
4. Calculate the overall average score for each student.
5. Identify the top 5 students based on their overall average score.
6. Visualize the distribution of scores for each subject using histograms.
7. Save the results (e.g., top 5 students) to a new CSV file.

---

### Dataset (CSV Format)

Below is the dataset in CSV format. Save this as `student_scores.csv`:

```csv
Student_ID,Name,Age,Gender,Math_Score,Science_Score,English_Score
1,John Doe,16,Male,85,90,88
2,Jane Smith,17,Female,92,89,91
3,Alice Johnson,16,Female,78,85,80
4,Bob Brown,17,Male,88,92,85
5,Charlie Davis,16,Male,76,78,74
6,Diana Evans,17,Female,95,94,96
7,Michael Wilson,16,Male,82,85,88
8,Sophia Martinez,17,Female,90,91,93
9,William Anderson,16,Male,79,80,77
10,Olivia Thomas,17,Female,93,92,94
```

---

### Solution

```python
import pandas as pd
import matplotlib.pyplot as plt

# Task 1: Load the dataset
df = pd.read_csv('student_scores.csv')

# Task 2: Basic data exploration
print("First 5 rows of the dataset:")
print(df.head())

print("\nDataset information:")
print(df.info())

print("\nChecking for missing values:")
print(df.isnull().sum())

# Task 3: Calculate the average score for each subject
math_avg = df['Math_Score'].mean()
science_avg = df['Science_Score'].mean()
english_avg = df['English_Score'].mean()

print(f"\nAverage Math Score: {math_avg:.2f}")
print(f"Average Science Score: {science_avg:.2f}")
print(f"Average English Score: {english_avg:.2f}")

# Task 4: Calculate the overall average score for each student
df['Overall_Avg'] = df[['Math_Score', 'Science_Score', 'English_Score']].mean(axis=1)

# Task 5: Identify the top 5 students based on their overall average score
top_5_students = df.nlargest(5, 'Overall_Avg')[['Student_ID', 'Name', 'Overall_Avg']]
print("\nTop 5 students based on overall average score:")
print(top_5_students)

# Task 6: Visualize the distribution of scores for each subject
plt.figure(figsize=(15, 5))

plt.subplot(1, 3, 1)
plt.hist(df['Math_Score'], bins=10, color='blue', alpha=0.7)
plt.title('Math Score Distribution')

plt.subplot(1, 3, 2)
plt.hist(df['Science_Score'], bins=10, color='green', alpha=0.7)
plt.title('Science Score Distribution')

plt.subplot(1, 3, 3)
plt.hist(df['English_Score'], bins=10, color='red', alpha=0.7)
plt.title('English Score Distribution')

plt.tight_layout()
plt.show()

# Task 7: Save the top 5 students to a new CSV file
top_5_students.to_csv('top_5_students.csv', index=False)
print("\nTop 5 students saved to 'top_5_students.csv'.")
```

---

### Explanation of the Code

1. **Loading the Dataset:** The dataset is loaded using `pd.read_csv()`.
2. **Data Exploration:** The first few rows, dataset information, and missing values are checked.
3. **Average Scores:** The mean score for each subject is calculated using `.mean()`.
4. **Overall Average:** A new column `Overall_Avg` is created to store the average score of each student across all subjects.
5. **Top 5 Students:** The `nlargest()` function is used to identify the top 5 students based on their overall average score.
6. **Visualization:** Histograms are plotted to visualize the distribution of scores for each subject.
7. **Saving Results:** The top 5 students are saved to a new CSV file using `.to_csv()`.

---

### Output

1. **Average Scores:**
   ```
   Average Math Score: 85.80
   Average Science Score: 87.60
   Average English Score: 86.60
   ```

2. **Top 5 Students:**
   ```
      Student_ID           Name  Overall_Avg
   5          6    Diana Evans    95.000000
   9         10  Olivia Thomas    93.000000
   1          2    Jane Smith    90.666667
   7          8  Sophia Martinez  91.333333
   3          4      Bob Brown    88.333333
   ```

3. **Visualization:** Histograms for Math, Science, and English scores are displayed.

4. **Saved File:** The top 5 students are saved in `top_5_students.csv`.
