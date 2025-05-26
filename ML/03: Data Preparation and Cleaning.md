# Lecture 3: Data Preparation and Cleaning

**Duration**: ~20 minutes  
**Objective**: Learn how to prepare and clean data for machine learning (ML) models, ensuring the computer can understand it.

## Why Data Preparation Matters
- **Analogy**: Imagine baking a cake. If you use spoiled ingredients (bad data), the cake (ML model) will taste awful. Clean data = better predictions.
- **Key Idea**: “Garbage in, garbage out” – ML models need clean, organized data to work well.
- **Example**: A movie ratings dataset with missing ratings or text like “Comedy” needs cleaning before predicting user preferences.

## Steps for Data Preparation
1. **Handle Missing Data**: Fill in or remove missing values (e.g., a missing movie rating).
2. **Convert Text to Numbers**: ML models need numbers, not words (e.g., “Comedy” → 1, “Drama” → 2).
3. **Scale Data**: Adjust numbers to similar ranges (e.g., make ages 20–80 and incomes $20K–$100K comparable).
4. **Remove Errors**: Fix typos or outliers (e.g., a movie rating of 99 when max is 5).

## Example: Cleaning a Movie Ratings Dataset
- **Dataset**: Movies with ratings, genres, and release years.
- **Issues**:
  - Missing ratings for some movies.
  - Genres are text (e.g., “Comedy”).
  - Years range widely (1980–2025).
- **Table (Before Cleaning)**:
  | Movie       | Rating | Genre  | Year |
  |-------------|--------|--------|------|
  | Movie A     | 4      | Comedy | 2000 |
  | Movie B     | -      | Drama  | 2015 |
  | Movie C     | 3      | Comedy | 2020 |
  | Movie D     | 99     | Action | 1990 |
- **Cleaning Steps**:
  - Fill missing rating (Movie B) with the average rating.
  - Encode genres: Comedy = 1, Drama = 2, Action = 3.
  - Scale years to 0–1 range (e.g., 1990 → 0, 2025 → 1).
- **Table (After Cleaning)**:
  | Movie       | Rating | Genre | Scaled Year |
  |-------------|--------|-------|-------------|
  | Movie A     | 4.0    | 1     | 0.29        |
  | Movie B     | 3.5    | 2     | 0.71        |
  | Movie C     | 3.0    | 1     | 0.86        |
  | Movie D     | 5.0    | 3     | 0.00        |

## Python Example: Cleaning Data with Pandas and Scikit-learn
- **Tool**: Google Colab (no setup needed).
- **Code** (heavily commented for clarity):
  ```python
  import pandas as pd
  from sklearn.impute import SimpleImputer
  from sklearn.preprocessing import MinMaxScaler
  # Create sample movie dataset
  data = {
      'Rating': [4, None, 3, 99],  # Missing value, outlier
      'Genre': ['Comedy', 'Drama', 'Comedy', 'Action'],
      'Year': [2000, 2015, 2020, 1990]
  }
  df = pd.DataFrame(data)
  print("Before cleaning:\n", df)
  # Step 1: Fix outlier (Rating > 5 → 5)
  df['Rating'] = df['Rating'].clip(upper=5)
  # Step 2: Fill missing ratings with average
  imputer = SimpleImputer(strategy='mean')
  df['Rating'] = imputer.fit_transform(df[['Rating']])
  # Step 3: Convert Genre to numbers
  df['Genre'] = df['Genre'].map({'Comedy': 1, 'Drama': 2, 'Action': 3})
  # Step 4: Scale Year to 0–1
  scaler = MinMaxScaler()
  df['Scaled_Year'] = scaler.fit_transform(df[['Year']])
  print("After cleaning:\n", df[['Rating', 'Genre', 'Scaled_Year']])
  # Plot ratings by genre
  import matplotlib.pyplot as plt
  plt.bar(df['Genre'], df['Rating'], color='#36A2EB')
  plt.xlabel('Genre (1=Comedy, 2=Drama, 3=Action)')
  plt.ylabel('Rating')
  plt.title('Movie Ratings by Genre')
  plt.show()
  ```
- **Explanation**: “This code fixes missing ratings, turns genres into numbers, scales years, and shows a bar chart of ratings by genre.”
- **Output (Simplified)**:
  ```
  Before cleaning:
     Rating   Genre  Year
  0    4.0  Comedy  2000
  1    NaN   Drama  2015
  2    3.0  Comedy  2020
  3   99.0  Action  1990
  After cleaning:
     Rating  Genre  Scaled_Year
  0    4.0      1     0.29
  1    4.0      2     0.71
  2    3.0      1     0.86
  3    5.0      3     0.00
  ```
- **Visual**: Bar chart showing ratings by genre.

## Practice Exercise: Clean a Dataset in Google Colab
- **Task**: Clean a small movie dataset and visualize the results.
- **Steps**:
  1. Open a provided Google Colab notebook (link to be shared, or create one with the code above).
  2. Load a dataset with 10 movies (ratings, genres, years; some missing values).
  3. Use the provided code to:
     - Fill missing ratings with the average.
     - Encode genres (e.g., Comedy = 1, Drama = 2).
     - Scale years to 0–1.
  4. Plot a bar chart of ratings by genre using Matplotlib.
  5. Tweak one rating (e.g., change 4 to 5) and re-run to see how the chart changes.
- **Tool**: Google Colab.
- **Goal**: Practice data cleaning and visualize the impact.
- **Sample Dataset**:
  | Movie       | Rating | Genre  | Year |
  |-------------|--------|--------|------|
  | Movie 1     | 3.5    | Comedy | 2010 |
  | Movie 2     | -      | Drama  | 2005 |
  | Movie 3     | 4.0    | Action | 2020 |
  | ... (7 more rows) | ... | ... | ... |
- **Expected Output**: Cleaned table and bar chart.

## Tools Introduced
- **Pandas**: Organizes data into tables (like spreadsheets).
- **Scikit-learn**: Provides tools for cleaning (e.g., `SimpleImputer`, `MinMaxScaler`).
- **Matplotlib**: Creates plots to visualize data.
- **Google Colab**: Free platform to run Python code without setup.

## Tips for Non-IT Students
- **Start Small**: Focus on running the code and understanding the output (table, plot).
- **Don’t Fear Code**: The notebook explains each line (e.g., “This fills missing values”).
- **Play Around**: Change a rating or year in the dataset to see how it affects the results.
- **Ask Why**: Cleaning makes data usable for ML, like organizing notes before studying.

## Visual: Bar Chart of Cleaned Data
Here’s a chart showing ratings by genre after cleaning:

```chartjs
{
  "type": "bar",
  "data": {
    "labels": ["Comedy (1)", "Drama (2)", "Action (3)"],
    "datasets": [{
      "label": "Movie Ratings",
      "data": [3.5, 4.0, 5.0],
      "backgroundColor": ["#36A2EB", "#FF6384", "#FFCE56"],
      "borderColor": ["#36A2EB", "#FF6384", "#FFCE56"],
      "borderWidth": 1
    }]
  },
  "options": {
    "scales": {
      "x": { "title": { "display": true, "text": "Genre" } },
      "y": { "title": { "display": true, "text": "Rating" }, "beginAtZero": true, "max": 5 }
    },
    "plugins": { "title": { "display": true, "text": "Movie Ratings by Genre" } }
  }
}
```

## Next Steps
- **Review**: Check the cleaned dataset and chart to ensure you understand each step.
- **Prepare for Lecture 4**: We’ll use clean data to evaluate ML models (e.g., accuracy of predictions).
- **Explore**: Try cleaning a different dataset (e.g., student grades) in Colab for extra practice.
