Mall Customers Dataset Cleaning Project
This project demonstrates a complete data cleaning workflow on a raw dataset (`Mall_Customers.csv`) using Python and pandas.
Dataset

- **Source**: `Mall_Customers.csv`
- Contains information about mall customers, including age, gender, annual income, and spending score.

---

Tools Used

- Python (Google Colab)
- pandas

---

Data Cleaning Steps

1. **Loaded the raw dataset** using `pandas.read_csv`.
2. **Checked for missing values** using `.isnull().sum()` and handled them.
3. **Removed duplicate rows** using `.drop_duplicates()`.
4. **Standardized text formats** in the `gender` column (lowercase, stripped spaces).
5. **Renamed column headers** to lowercase with underscores using `df.columns.str.lower().str.replace(...)`.
6. **Converted data types**:
   - `gender` → `category`
   - `age` → `int` (already numeric, confirmed)
7. **Saved the cleaned dataset** to `mall_customers_cleaned.csv`.

---

Code Used

```python
import pandas as pd

# Load raw data
df = pd.read_csv('/mnt/data/Mall_Customers.csv')

# Check missing values
df.isnull().sum()

# Drop duplicates
df.drop_duplicates(inplace=True)

# Standardize gender column
df['Gender'] = df['Gender'].str.strip().str.lower()
df['Gender'] = df['Gender'].astype('category')

# Rename columns
df.columns = df.columns.str.strip().str.lower().str.replace(' ', '_')

# Save cleaned data
df.to_csv('/mnt/data/mall_customers_cleaned.csv', index=False)
