# nhanes_inferential_2021_23

## Project Overview
This project uses NHANES 2021-2023 data to perform basic inferential statistics and explore relationships between health metrics and demographic variables. The goal is to answer questions about the dataset through data cleaning, transformation, analysis, and visualization in Google Colab. 

## Data Loading and Preparation
- **Data Source**: NHANES 2021-2023 SAS files loaded using `pandas.read_sas()` with format='xport'.
- **Variables Used**:
  -   Marital Status(`DMDMARTZ`)
  -   Educational Level(`DMDEDUC2`)
  -   Age in Years(`RIDAGEYR`)
  -   Systolic Blood Pressure(`BPXOSY3`)
  -   Diastolic Blood Pressure(`BPXODI3`)
  -   Vitamin D Lab Interpretation(`LBDVD2LC`)
  -   Hepatitis B Lab Antibodies(`LBXHBS`)
  -   Weak/Failing Kidneys(`KIQ022`)
  -   Minutes of Sedentary Behavior(`PAD680`)
  -   Current Self-reported Weight(`WHD020`)

## Data Cleaning and Recording
- Placeholder values (`7777`, `9999`, `.`) replaced with `NaN` for continuous variables (`PAD680`, `WHD020`).
- Categorical variables recoded to meaningful levels:
  - Marital Status: `1 = Married`, others `= Not married`, `77/99 = NaN`.
  - Education Level: `5 = Bachelors or higher`, `1-4 = Less than bachelors`, `7/9 = NaN`.
  - Hepatitis B Antibodies: `1 = Positive`, `2 = Negative`, `3/4 = NaN`.
  - Weak/Failing Kidneys: `1 = Yes`, `2 = No`, `7/9 = NaN`.
  - Vitamin D Lab Interpretation used as-is with two levels.
- Dropped rows with missing values before performing statistical tests to ensure valid analysis.

## Answers to Questions

### Question 1: Association between Marital Status and Education Level
- Variables: Recoded Marital Status and Education Level.
- Test: Chi-square test 
- **Result:** Significant association found (example: chi-square statistic and p-value), indicating marital status and education level are related. The result showed a p-value less than 0.05.

### Question 2: Difference in Mean Sedentary Behavior by Marital Status
- Variables: Marital Status and Sedentary Behavior Time (`PAD680`).
- Test: Independent samples t-test.
- Visualization: Boxplot comparing sedentary behavior minutes by marital status.
- **Result:** t-statistic ≈ -3.87, p-value ≈ 0.0001  
- Interpretation: A statistically significant difference exists(p-value<0.05). The negative t-statistic (-3.87) indicates that married individuals have a lower mean sedentary time than unmarried individuals. 

### Question 3: Effects of Age and Marital Status on Systolic Blood Pressure
- Variables: Age (`RIDAGEYR`), Marital Status (`DMDMARTZ`), Systolic Blood Pressure (`BPXOSY3`).
- Visualization: Scatterplot with regression lines overlaid, color-coded by marital status.
    - Married: Blue line
    - Unmarried: Orange line
- **Interpretation:** Systolic blood pressure generally increases with age in both groups. Slight differences in marital status were observed. In the visualization, systolic blood pressure tends to increase with age in both groups. The upward slope of the regression line shows a positive correlation between age and blood pressure. Including marital status, the not married line looks slightly higher across most ages, even though both "Married" and "Not married show similar upward trends.

<img width="868" height="512" alt="image" src="https://github.com/user-attachments/assets/c7766405-3acf-4b45-b036-ea9ce7335eb0" />
  
### Question 4: Correlation Between Self-Reported Weight and Sedentary Behavior
- Variables: Self-reported weight (`WHD020`) and minutes of sedentary behavior (`PAD680`).
- Test: Pearson correlation.
- Visualization: Scatterplot with regression line.
- **Result:** Correlation coefficient ≈ 0.156, p-value < 0.001  
- Interpretation: There is a weak but statistically significant positive correlation, suggesting that higher weight is slightly associated with more sedentary behavior. The scatterplot shows the relationship between self-reported weight and sedentary time. The red regression line slopes slightly upward, and even though the data points are scattered, they generally lie in the same direction, indicating a positive relationship between the two variables. The correlation coefficient (r) of 0.156 indicates a weak positive correlation.

<img width="859" height="547" alt="image" src="https://github.com/user-attachments/assets/d3f2975e-b528-41e7-aff9-610608a79ab3" />


### Question 5: (Creative Analysis): Difference in Vitamin D Levels by Weak/Failing Kidney Status
- Variables: Vitamin D levels (`LBDVD2LC`) and Kidney status (`KIQ010` recoded).
- Test: Chi-square test comparing Vitamin D categorical levels across kidney status groups.
- **Result:** Chi-square ≈ 0.944, p-value ≈ 0.624  
Interpretation: The chi-square statistic is small, and the p-value of 0.6236 is well above 0.05, indicating no statistically significant association between Vitamin D status and weak/failing kidneys in the dataset.
