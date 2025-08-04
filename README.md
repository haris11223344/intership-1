# intership-1
Daily tasks-1



Data Cleaning Documentation
1. Missing Value Handling
Objective: Identify and address empty or null values to prevent analysis errors.

Methods:
Python (Pandas):

python
# Check for missing values
df.isnull().sum()

# Handle missing values
df.fillna({
    'numerical_column': df['numerical_column'].median(),  # For numbers
    'categorical_column': 'Unknown'                      # For text
}, inplace=True)
Excel:

Use Filters → Blanks to identify empty cells

Fill with:

=MEDIAN() for numerical columns

=MODE() or "Unknown" for categorical columns

2. Duplicate Removal
Objective: Eliminate redundant rows while preserving unique records.

Methods:
Python (Pandas):

python
df.drop_duplicates(inplace=True)  # Keeps first occurrence
Excel:

Select data → Data tab → Remove Duplicates

Verify columns for duplicate criteria

3. Text Standardization
Objective: Ensure consistent formatting for categorical data.

Standardization Rules:
Gender: Convert to Male/Female/Other

Country Names: Use ISO codes or canonical forms (e.g., "USA" not "United States")

General Text:

python
df['text_column'] = df['text_column'].str.strip().str.title()
4. Date Format Conversion
Objective: Enforce uniform date representation.

Methods:
Python (Pandas):

python
df['date_column'] = pd.to_datetime(df['date_column'], format='%d-%m-%Y')
Excel:

Right-click → Format Cells → Custom → Enter dd-mm-yyyy

Use TEXT() function for conversions:

text
=TEXT(A2, "dd-mm-yyyy")
5. Column Header Cleaning
Objective: Improve readability and machine compatibility.

Rules:
Lowercase (e.g., customer_id not Customer ID)

Underscore-separated (e.g., order_date)

No special characters or spaces

Python Implementation:

python
df.columns = df.columns.str.lower().str.replace(' ', '_')
6. Data Type Validation
Objective: Ensure correct typing for analytical operations.

Common Fixes:
Column Type	Action	Python Code
Numeric	Convert strings to integers	df['age'] = pd.to_numeric(df['age'])
Dates	Parse string dates	pd.to_datetime(df['date_column'])
Boolean	Map text to True/False	df['flag'].map({'Yes': True, 'No': False})
Excel Methods:
Use VALUE() for numbers

DATEVALUE() for dates

Custom formatting via Format Cells

Quality Assurance
Post-Cleaning Checks:

python
df.info()          # Verify data types
df.describe()      # Check numerical ranges
df['gender'].value_counts()  # Validate categorical standardization
Excel:

Apply conditional formatting to highlight outliers

Use COUNTIF to validate categorical values

<img width="1838" height="924" alt="Screenshot 2025-08-04 145514" src="https://github.com/user-attachments/assets/a0ebc136-c527-4f0a-8fc9-26d6190f47c3" />
<img width="1823" height="893" alt="image" src="https://github.com/user-attachments/assets/b56461de-7b13-4cfe-a5a6-1b9a322a15b6" />


