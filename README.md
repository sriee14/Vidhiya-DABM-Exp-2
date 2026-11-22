# Exp No.2 : Exploratory Data Analysis (EDA)

## Aim
To perform Exploratory Data Analysis (EDA) on the heart disease dataset to understand the data distribution, relationships, and key patterns useful for business insights and model building.

## Dataset
The dataset used for this experiment is `heartdisease.csv`. It contains medical and demographic information such as age, sex, cholesterol levels (`totChol`), `BMI`, blood pressure, and target values (`TenYearCHD`) indicating heart disease presence.

## Algorithm
1. Import required Python libraries (`numpy`, `pandas`, `seaborn`, `matplotlib`).
2. Load the dataset into a Pandas DataFrame.
3. Display the dataset structure, shape, and descriptive statistics.
4. Check for missing values and duplicate rows.
5. Examine correlations among numeric features using a correlation matrix and heatmap.
6. Visualize univariate distributions using histograms, boxplots, and countplots.
7. Analyze bivariate and multivariate relationships using scatter plots and pairplots.

## Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Basic Exploration** | `df.info()` | Inspect dataset structure and data types |
| | `df.describe()` | Generate descriptive statistics |
| | `df.isnull().sum()` | Detect missing values in each column |
| | `df.duplicated().sum()` | Identify duplicate rows |
| | `df.corr()` | Find correlations between numeric variables |
| **Univariate Analysis** | `sns.histplot()` | Plot histogram (distribution of single variable) |
| | `sns.boxplot()` | Identify outliers using boxplot |
| | `sns.countplot()` | Count occurrences of categorical variables |
| **Bivariate Analysis** | `sns.scatterplot()` | Display relationship between two variables |
| | `sns.heatmap()` | Show correlation matrix visually |
| **Multivariate Analysis** | `sns.pairplot()` | Show pairwise relationships across variables |
| **Visualization Controls** | `plt.figure()`, `plt.title()`, `plt.xlabel()`, `plt.ylabel()`, `plt.show()` | Configure and display plotted charts |

## Program & Output
```
# Exploratory Data Analysis (EDA) on Heart Disease Dataset

# Step 1: Import Essential Libraries
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
```
## Input 1
```
# Step 2: Load the Dataset
df = pd.read_csv('heartdisease.csv')

# Step 3: Basic Exploration

# Inspect dataset structure and data types
print("\n--- Dataset Information ---")
print(df.info())
```
## Output 1
```
--- Dataset Information ---
<class 'pandas.DataFrame'>
RangeIndex: 3658 entries, 0 to 3657
Data columns (total 17 columns):
 #   Column           Non-Null Count  Dtype  
---  ------           --------------  -----  
 0   sno              3658 non-null   int64  
 1   gender           3658 non-null   int64  
 2   age              3658 non-null   int64  
 3   education        3658 non-null   int64  
 4   currentSmoker    3658 non-null   int64  
 5   cigsPerDay       3658 non-null   int64  
 6   BPMeds           3658 non-null   int64  
 7   prevalentStroke  3658 non-null   int64  
 8   prevalentHyp     3658 non-null   int64  
 9   diabetes         3658 non-null   int64  
 10  totChol          3658 non-null   int64  
 11  sysBP            3658 non-null   float64
 12  diaBP            3658 non-null   float64
 13  BMI              3658 non-null   float64
 14  heartRate        3658 non-null   int64  
 15  glucose          3658 non-null   int64  
 16  TenYearCHD       3658 non-null   int64  
dtypes: float64(3), int64(14)
memory usage: 486.0 KB
None
```
## Input 2
```
# Generate descriptive statistics
print("\n--- Descriptive Statistics ---")
print(df.describe())
```
## Output 2
```
--- Descriptive Statistics ---
               sno      gender           age    education  currentSmoker  \
count  3658.000000  3658.000000  3658.000000  3658.000000    3658.000000   
mean   2124.551941     0.443685    49.551941     1.980317       0.489065   
std    1230.833763     0.496886     8.562029     1.022656       0.499949   
min       1.000000     0.000000    32.000000     1.000000       0.000000   
25%    1052.250000     0.000000    42.000000     1.000000       0.000000   
50%    2141.500000     0.000000    49.000000     2.000000       0.000000   
75%    3201.750000     1.000000    56.000000     3.000000       1.000000   
max    4240.000000     1.000000    70.000000     4.000000       1.000000   

        cigsPerDay       BPMeds  prevalentStroke  prevalentHyp     diabetes  \
count  3658.000000  3658.000000      3658.000000   3658.000000  3658.000000   
mean      9.025424     0.030344         0.005741      0.311646     0.027064   
std      11.921590     0.171557         0.075561      0.463229     0.162292   
min       0.000000     0.000000         0.000000      0.000000     0.000000   
25%       0.000000     0.000000         0.000000      0.000000     0.000000   
50%       0.000000     0.000000         0.000000      0.000000     0.000000   
75%      20.000000     0.000000         0.000000      1.000000     0.000000   
max      70.000000     1.000000         1.000000      1.000000     1.000000   

           totChol        sysBP        diaBP          BMI    heartRate  \
count  3658.000000  3658.000000  3658.000000  3658.000000  3658.000000   
mean    236.847731   132.370558    82.917031    25.782802    75.730727   
std      44.097681    22.086866    11.974258     4.065601    11.981525   
min     113.000000    83.500000    48.000000    15.540000    44.000000   
25%     206.000000   117.000000    75.000000    23.080000    68.000000   
50%     234.000000   128.000000    82.000000    25.380000    75.000000   
75%     263.000000   143.875000    90.000000    28.037500    82.000000   
max     600.000000   295.000000   142.500000    56.800000   143.000000   

           glucose   TenYearCHD  
count  3658.000000  3658.000000  
mean     81.852925     0.152269  
std      23.904164     0.359331  
min      40.000000     0.000000  
25%      71.000000     0.000000  
50%      78.000000     0.000000  
75%      87.000000     0.000000  
max     394.000000     1.000000  
```
## Input 3
```
# Check number of rows and columns
print("\n--- Dataset Shape ---")
print("Rows:", df.shape[0], "Columns:", df.shape[1])
```
## Output 3
```
--- Dataset Shape ---
Rows: 3658 Columns: 17

```
## Input 4
```
# Display first 10 rows
print("\n--- First 10 Rows ---")
print(df.head(10))
```
## Output 4
```
--- First 10 Rows ---
   sno  gender   age  education  currentSmoker  cigsPerDay  BPMeds  \
0    1        1   39          4              0           0       0   
1    2        0   46          2              0           0       0   
2    3        1   48          1              1          20       0   
3    4        0   61          3              1          30       0   
4    5        0   46          3              1          23       0   
5    6        0   43          2              0           0       0   
6    7        0   63          1              0           0       0   
7    8        0   45          2              1          20       0   
8    9        1   52          1              0           0       0   
9   10        1   43          1              1          30       0   

   prevalentStroke  prevalentHyp  diabetes  totChol  sysBP  diaBP    BMI  \
0                0             0         0      195  106.0   70.0  26.97   
1                0             0         0      250  121.0   81.0  28.73   
2                0             0         0      245  127.5   80.0  25.34   
3                0             1         0      225  150.0   95.0  28.58   
4                0             0         0      285  130.0   84.0  23.10   
5                0             1         0      228  180.0  110.0  30.30   
6                0             0         0      205  138.0   71.0  33.11   
7                0             0         0      313  100.0   71.0  21.68   
8                0             1         0      260  141.5   89.0  26.36   
9                0             1         0      225  162.0  107.0  23.61   

   heartRate  glucose  TenYearCHD  
0         80       77           0  
1         95       76           0  
2         75       70           0  
3         65      103           1  
4         85       85           0  
5         77       99           0  
6         60       85           1  
7         79       78           0  
8         76       79           0  
9         93       88           0  
```
## Input 5
```
# Step 4: Check Data Quality

# Check missing values
print("\n--- Missing Values ---")
print(df.isnull().sum())
```
## Output 5
```
--- Missing Values ---
sno                0
gender             0
age                0
education          0
currentSmoker      0
cigsPerDay         0
BPMeds             0
prevalentStroke    0
prevalentHyp       0
diabetes           0
totChol            0
sysBP              0
diaBP              0
BMI                0
heartRate          0
glucose            0
TenYearCHD         0
dtype: int64
```
## Input 6
```
# Check duplicate rows
print("\n--- Duplicate Rows ---")
print(df.duplicated().sum())
```
## Output 6
```
--- Duplicate Rows ---
0
```
## Input 7
```
# Step 5: Correlation Analysis

# Calculate correlation
print("\n--- Correlation Matrix ---")
print(df.corr(numeric_only=True))
```
## Output 7
```
--- Correlation Matrix ---
                      sno   gender        age  education  currentSmoker  \
sno              1.000000  0.021182  0.001253   0.011385      -0.003227   
gender           0.021182  1.000000 -0.024412   0.017729       0.206114   
age              0.001253 -0.024412  1.000000  -0.159499      -0.210771   
education        0.011385  0.017729 -0.159499   1.000000       0.025251   
currentSmoker   -0.003227  0.206114 -0.210771   0.025251       1.000000   
cigsPerDay       0.002308  0.330322 -0.189295   0.013790       0.773913   
BPMeds           0.027799 -0.052124  0.134732  -0.013739      -0.051923   
prevalentStroke  0.031476 -0.002312  0.050893  -0.030386      -0.038150   
prevalentHyp     0.022094  0.001424  0.306239  -0.078828      -0.108078   
diabetes         0.036771  0.013819  0.109092  -0.039627      -0.041849   
totChol         -0.014659 -0.070321  0.268252  -0.013522      -0.051034   
sysBP            0.005526 -0.045358  0.388267  -0.124360      -0.134428   
diaBP            0.009075  0.051872  0.208283  -0.058059      -0.115955   
BMI              0.010674  0.073111  0.137511  -0.137555      -0.159821   
heartRate        0.035081 -0.115285 -0.002722  -0.064214       0.050841   
glucose          0.023293  0.002940  0.118349  -0.031998      -0.053242   
TenYearCHD      -0.003796  0.091688  0.233983  -0.063279       0.019165   

                 cigsPerDay    BPMeds  prevalentStroke  prevalentHyp  \
sno                0.002308  0.027799         0.031476      0.022094   
gender             0.330322 -0.052124        -0.002312      0.001424   
age               -0.189295  0.134732         0.050893      0.306239   
education          0.013790 -0.013739        -0.030386     -0.078828   
currentSmoker      0.773913 -0.051923        -0.038150     -0.108078   
cigsPerDay         1.000000 -0.046504        -0.036286     -0.070460   
BPMeds            -0.046504  1.000000         0.113125      0.262910   
prevalentStroke   -0.036286  0.113125         1.000000      0.066057   
prevalentHyp      -0.070460  0.262910         0.066057      1.000000   
diabetes          -0.036961  0.049066         0.009625      0.080556   
totChol           -0.030400  0.094083         0.012736      0.166655   
sysBP             -0.094781  0.271263         0.061070      0.697675   
diaBP             -0.056746  0.199630         0.055834      0.617734   
BMI               -0.087395  0.105642         0.036496      0.302949   
heartRate          0.064030  0.012889        -0.017019      0.146818   
glucose           -0.053726  0.054232         0.016061      0.086942   
TenYearCHD         0.052014  0.089152         0.048366      0.181387   

                 diabetes   totChol     sysBP     diaBP       BMI  heartRate  \
sno              0.036771 -0.014659  0.005526  0.009075  0.010674   0.035081   
gender           0.013819 -0.070321 -0.045358  0.051872  0.073111  -0.115285   
age              0.109092  0.268252  0.388267  0.208283  0.137511  -0.002722   
education       -0.039627 -0.013522 -0.124360 -0.058059 -0.137555  -0.064214   
currentSmoker   -0.041849 -0.051034 -0.134428 -0.115955 -0.159821   0.050841   
cigsPerDay      -0.036961 -0.030400 -0.094781 -0.056746 -0.087395   0.064030   
BPMeds           0.049066  0.094083  0.271263  0.199630  0.105642   0.012889   
prevalentStroke  0.009625  0.012736  0.061070  0.055834  0.036496  -0.017019   
prevalentHyp     0.080556  0.166655  0.697675  0.617734  0.302949   0.146818   
diabetes         1.000000  0.048451  0.102552  0.050686  0.089009   0.060984   
totChol          0.048451  1.000000  0.219925  0.174422  0.121056   0.093053   
sysBP            0.102552  0.219925  1.000000  0.786669  0.330917   0.184797   
diaBP            0.050686  0.174422  0.786669  1.000000  0.385348   0.178744   
BMI              0.089009  0.121056  0.330917  0.385348  1.000000   0.074131   
heartRate        0.060984  0.093053  0.184797  0.178744  0.074131   1.000000   
glucose          0.614820  0.049884  0.134651  0.063540  0.083683   0.097074   
TenYearCHD       0.093431  0.091338  0.222821  0.150124  0.082055   0.020514   

                  glucose  TenYearCHD  
sno              0.023293   -0.003796  
gender           0.002940    0.091688  
age              0.118349    0.233983  
education       -0.031998   -0.063279  
currentSmoker   -0.053242    0.019165  
cigsPerDay      -0.053726    0.052014  
BPMeds           0.054232    0.089152  
prevalentStroke  0.016061    0.048366  
prevalentHyp     0.086942    0.181387  
diabetes         0.614820    0.093431  
totChol          0.049884    0.091338  
sysBP            0.134651    0.222821  
diaBP            0.063540    0.150124  
BMI              0.083683    0.082055  
heartRate        0.097074    0.020514  
glucose          1.000000    0.121990  
TenYearCHD       0.121990    1.000000  
```

## Input 8
```
# Visualize correlation using heatmap
plt.figure(figsize=(10, 6))
sns.heatmap(df.corr(numeric_only=True), annot=True, cmap='coolwarm')
plt.title("Correlation Heatmap of Heart Disease Dataset")
plt.show()
```
## Output 8

<img width="865" height="624" alt="image" src="https://github.com/user-attachments/assets/b9db4599-6643-4ae6-b8ab-17e5b62abd63" />


## Input 9
```
# Step 6: Univariate Analysis

# Histogram for Age distribution
print("\n--- Histogram for Age Distribution ---")
plt.figure(figsize=(8, 5))
sns.histplot(df['age'], kde=True, bins=20, color='teal')
plt.title("Distribution of Age")
plt.xlabel("Age")
plt.ylabel("Count")
plt.show()
```
## Output 9
```
--- Histogram for Age Distribution ---
```
<img width="695" height="470" alt="image" src="https://github.com/user-attachments/assets/a5cc8e37-0753-4392-96f0-20fa5d3c5fb8" />

## Input 10
```
# Boxplot for Cholesterol
print("\n--- Boxplot for Cholesterol ---")
plt.figure(figsize=(6, 4))
sns.boxplot(x=df['totChol'])
plt.title("Boxplot of Cholesterol Levels")
plt.xlabel("Cholesterol")
plt.show()
```
## Output 11
```
--- Boxplot for Cholesterol ---
```
<img width="489" height="393" alt="image" src="https://github.com/user-attachments/assets/781b511d-e071-48f6-841f-11e5cc432aaf" />

## Input 12
```
# Countplot for Gender
print("\n--- Countplot for Gender ---")
if 'sex' in df.columns:
    plt.figure(figsize=(5, 4))
    sns.countplot(x='sex', data=df)
    plt.title("Count of Gender")
    plt.xlabel("Sex (0 = Female, 1 = Male)")
    plt.ylabel("Count")
    plt.show()
```
## Output 13
```
--- Countplot for Gender ---

```
## Input 14
```
# Step 7: Bivariate Analysis

# Scatter plot: Age vs Cholesterol
print("\n--- Scatter Plot: Age vs Cholesterol ---")
plt.figure(figsize=(8, 5))
sns.scatterplot(
    x='age',
    y='totChol',
    data=df,
    hue='TenYearCHD',
    palette='coolwarm'
)
plt.title("Age vs Cholesterol (by Heart Disease Target)")
plt.xlabel("Age")
plt.ylabel("Cholesterol")
plt.show()
```
## Output 15
```
--- Scatter Plot: Age vs Cholesterol ---
```
<img width="695" height="470" alt="image" src="https://github.com/user-attachments/assets/21136589-9fdc-4a0a-a074-b4b4ea8af4c4" />

## Input 16
```
# Step 8: Multivariate Analysis

# Pairplot for multiple relationships
print("\n--- Pairplot for Multiple Relationships ---")
selected_columns = ['age', 'totChol', 'BMI', 'TenYearCHD']

sns.pairplot(
    df[selected_columns],
    diag_kind='kde'
)
plt.suptitle(
    "Pairwise Relationship between Variables",
    y=1.02
)
plt.show()
```
## Output 16
```
--- Pairplot for Multiple Relationships ---

```
<img width="986" height="1023" alt="image" src="https://github.com/user-attachments/assets/59df7f13-66b8-4277-b82c-a7129e63ef93" />

## Result

The Exploratory Data Analysis (EDA) was successfully performed on the heart disease dataset. Data patterns, correlations, and distributions were identified through visual and statistical techniques. The dataset is ready for regression and classificaition modelling
