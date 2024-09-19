# **EXPERIMENT 4 - DATA WRANGLING AND DATA VISUALIZATION**

This repository showcases the solution to data wrangling and visualization problems using Python with pandas and seaborn libraries. It covers filtering and creating DataFrames based on specific conditions, computing averages, and generating insightful visualizations to better understand student performance data. The dataset (`board2.xlsx`) is used for all problems. Below is the breakdown of each problem, the methods and functions used to solve them, and the expected output for each.

---

## PROBLEM 1: Create the following DataFrames

### 1. Visayas DataFrame
#### **What is being asked**:  
Filter out students with **Math < 70** and **Hometown = Visayas**, and create a DataFrame with the columns `Name`, `Gender`, `Track`, and `Math`.

#### **Functions used**: 
- **`pd.DataFrame()`**: Create a DataFrame.
- **Boolean indexing**: Filter rows where Math < 70 and Hometown is Visayas.

#### **Expected Output**:
| Name | Gender | Track           | Math |
|------|--------|-----------------|------|
| S4   | Male   | Instrumentation | 65   |
| S11  | Female | Communication   | 48   |
| S22  | Female | Communication   | 64   |

#### **Code Breakdown**:
1. **Function Used**: `import pandas as pd`  
   **Description**: Imports the pandas library to work with data in DataFrame format.

2. **Function Used**: `data = pd.read_excel('board2.xlsx')`  
   **Description**: Reads the Excel file into a pandas DataFrame.

3. **Function Used**:  `visayas_df = data[(data['Hometown'] == 'Visayas') & (data['Math'] < 70)][['Name', 'Gender', 'Track', 'Math']]` 
   **Description**: Filters rows with `Math < 70` and `Hometown = Visayas`, and selects specific columns.

4. **Function Used**: `visayas_df`  
   **Description**: Outputs the filtered DataFrame.

#### **Conclusion**:  
By using Boolean indexing, the required data and necessary columns were successfully displayed, resulting in a concise DataFrame with students from Visayas who scored less than 70 in Math.

---

### 1a. Instrumentation DataFrame
#### **What is being asked**:  
Create a DataFrame for students with **Track = Instrumentation**, **Electronics > 70**, and **Hometown = Luzon**. The DataFrame should include `Name`, `GEAS`, and `Electronics` columns.

#### **Functions used**: 
- **Boolean indexing**: For filtering data based on conditions.
- **`pd.DataFrame()`**: Create a DataFrame.

#### **Expected Output**:  
Filtered data with students from Instrumentation track in Luzon and Electronics scores > 70.

#### **Code Breakdown**:
1. **Function Used**: `instru_df = data[(data['Track'] == 'Instrumentation') & (data['Hometown'] == 'Luzon') & (data['Electronics'] > 70)][['Name', 'GEAS', 'Electronics']]`  
   **Description**: Filters rows where the track is Instrumentation, Hometown is Luzon, and Electronics score is > 70, selecting the necessary columns.

2. **Function Used**: `instru_df`  
   **Description**: Outputs the filtered DataFrame.

#### **Conclusion**:  
This problem demonstrated the use of filtering conditions to generate a DataFrame of students following the Instrumentation track, meeting the given score and location criteria.

---

### 1b. Mindanao, Female, and Average >= 55 DataFrame
#### **What is being asked**:  
Create a DataFrame for **Gender = Female**, **Hometown = Mindanao**, and **Average >= 55**. The `Average` is computed based on the mean of technical subjects (`Math`, `Electronics`, `GEAS`, `Communication`).

#### **Functions used**: 
- **`mean()`**: Compute the average across subjects.
- **Boolean indexing**: Filter rows based on conditions.

#### **Expected Output**:  
Filtered data with female students from Mindanao with an average grade >= 55.

#### **Code Breakdown**:
1. **Function Used**: `data['Average'] = data[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)`
   **Description**: Computes the average of the four subjects across rows (axis=1).

2. **Function Used**: `mindy_df = data[(data['Hometown'] == 'Mindanao') & (data['Gender'] == 'Female') & (data['Average'] >= 55)][['Name', 'Track', 'Electronics', 'Average']]`  
   **Description**: Filters rows with Female gender, Hometown as Mindanao, and Average >= 55, selecting specific columns.

3. **Function Used**: `mindy_df`  
   **Description**: Outputs the filtered DataFrame.

#### **Conclusion**:  
This problem highlights the ability to compute new columns based on existing data (averages) and use them as a filter for more complex queries.

---

## PROBLEM 2: Visualization

### **What is being asked**:  
Generate various visualizations to show how different features contribute to the average grade of students. Bar charts, box plots, and scatterplots are used to compare different features.

#### **Functions used**: 
- **`sns.barplot()`**: Create bar plots to compare categorical data.
- **`sns.scatterplot()`**: Generate scatter plots to see correlations between variables.
- **`sns.boxplot()`**: Display the distribution and spread of data across categories.
- **`plt.show()`**: Display the plots.

#### **Expected Output**:
1. Bar charts showing average grades by Track, Gender, and Hometown.
2. Scatter plot showing the relationship between Electronics scores and Average grade.
3. Box plots showing the distribution of Average grades across Tracks.

#### **Code Breakdown**:

1. **Function Used**: `import seaborn as sns` 
   **Description**: Imports the seaborn library for visualization.

2. **Function Used**: `import matplotlib.pyplot as plt`   
   **Description**: Imports matplotlib's pyplot for plotting graphs.

3. **Function Used**: `plt.figure(figsize=(10, 6))`  
   **Description**: Creates a figure for the plot with specific dimensions.

4. **Function Used**: `sns.barplot(x='Track', y='Average', hue='Gender', data=data)`  
   **Description**: Plots a bar chart comparing average grades across tracks and genders.

5. **Function Used**: `plt.title('Average Grade by Track and Gender')`    
   **Description**: Sets the title of the plot.

6. **Function Used**: `plt.show()`  
   **Description**: Displays the generated plot.

7. **Function Used**: `sns.barplot(x='Hometown', y='Average', hue='Track', data=data)`  
   **Description**: Plots a bar chart comparing average grades by hometown and track.

8. **Function Used**: `plt.title('Average Grade by Hometown and Track')`  
   **Description**: Sets the title of the plot.

9. **Function Used**: `g = sns.catplot(data=data, x='Track', y='Average', hue='Gender', col='Hometown', kind='bar', height=6, aspect=1.2, palette='muted')`  
   **Description**: Creates a FacetGrid bar plot for each Hometown, comparing tracks and average grades.

10. **Function Used**: `g.fig.suptitle('Comparison of Average Grades by Track, Gender, and Hometown', y=1.05, fontsize=16)`  
    **Description**: Adds a title to the entire FacetGrid.

11. **Function Used**: `g.set_axis_labels('College Track', 'Average Grade')`  
    **Description**: Sets axis labels for the FacetGrid.

12. **Function Used**: `g.add_legend(title='Gender')`    
    **Description**: Adds a legend to the plot.

13. **Function Used**: `plt.figure(figsize=(10, 6))`  
    **Description**: Creates a new figure for the scatter plot.

14. **Function Used**: `sns.scatterplot(x='Electronics', y='Average', hue='Gender', style='Track', data=data, s=100)`   
    **Description**: Creates a scatter plot to visualize the relationship between Electronics scores and Average grades.

15. **Function Used**: `plt.title('Electronics Scores vs. Average Grade')`  
    **Description**: Sets the title of the scatter plot.

16. **Function Used**: `plt.show()` 
    **Description**: Displays the scatter plot.

17. **Function Used**: `sns.boxplot(x='Track', y='Average', hue='Gender', data=data)`   
    **Description**: Displays a box plot showing the spread of Average grades across different tracks.

18. **Function Used**: `plt.title('Distribution of Average Grades by Track and Gender')`  
    **Description**: Sets the title of the box plot.

19. **Function Used**: `plt.show()`  
    **Description**: Displays the box plot.

#### **Conclusion**:  
The visualizations provided deeper insights into how different variables, such as Track, Gender, and Hometown, influence students' performance. Bar charts highlighted the comparative averages, while scatter and box plots revealed more nuanced relationships.

---

### **Overall Conclusion**:
This experiment effectively demonstrates how to filter, transform, and visualize data using Python’s powerful pandas and seaborn libraries. Each problem showcases the ability to manipulate datasets to derive meaningful insights through data wrangling and visualization techniques.

---

###### Author: **Francesca Ellaiza R. Nacu**
