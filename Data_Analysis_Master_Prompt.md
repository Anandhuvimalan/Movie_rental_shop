# Dynamic Workspace Data Analysis Master Prompt

This prompt is designed for AI assistants that have access to your local project folder or workspace (like Google Gemini Code Assist, Cursor, or GitHub Copilot). It instructs the AI to **automatically search your workspace, find the CSV files on its own**, understand them, and generate a complete, professional Data Analysis Jupyter Notebook. 

**How to use:**
1. Open your AI assistant within your project workspace where your CSV files are located.
2. Copy the text between `BEGIN PROMPT` and `END PROMPT` and send it to the AI.
3. Sit back and watch it find your data and write the complete analysis!

---
**BEGIN PROMPT**
---

**Role & Objective:**
You are an Expert Data Scientist, Business Analyst, and Python Educator. I will NOT be attaching any CSV files. Instead, you have access to my project folder/workspace. **Your very first task** is to search the root folder and subfolders of this workspace to locate any `.csv` datasets. Once found, use their paths and dynamically analyze this specific data to generate a complete, end-to-end, production-ready Python data analysis pipeline in the format of a Jupyter Notebook (IPYNB). 

Your target audience is data analysis students or business stakeholders, so your output must be **highly readable, beginner-friendly, and professionally executed**. You must provide detailed Markdown documentation explaining your thought process ("why" and "how") before every code block. All your analysis, metrics, and code must be dynamically tailored to the precise columns, data types, and business context of the data you discover in my folder.

Please follow these exact steps sequentially. Do not skip or shorten any step.need heading for each sections.

### **Step 1: Automated Data Discovery & Documentation**
1. Systematically search the project workspace to find all `.csv` files. Print out the names and paths of the files you discovered.
2. Read the schema of these files and determine the overarching business domain (e.g., E-commerce, Education, HR, Finance).
3. Generate a comprehensive **Data Dictionary** explaining the presumed meaning and data type of every column in every table you found.

### **Step 2: Data Import & Comprehensive Inspection**
Generate Python code using `pandas` and `numpy` to:
1. Import all the `.csv` files using the paths you discovered.
2. Inspect the data using `.info()`, `.describe(include='all')`, and `.head()`.
3. Check for the number of unique identifiers or primary keys to understand the grain of the data.

### **Step 3: Dynamic Data Cleaning & Preprocessing**
Based strictly on the data types and actual columns present, generate code to handle:
1. **Missing Data:** Dynamically identify columns with missing values. Decide whether to impute (mean/median/mode) or drop them based on the column's business importance, and explicitly document your reasoning.
2. **Outliers:** Identify continuous numerical columns. Generate code to detect outliers (using IQR or Z-score) and handle them appropriately (cap, drop, or transform).
3. **Data Type Casting:** Ensure dates are converted to `datetime` objects, and categorical strings are treated correctly.ensure proper data type . there must be datatype converstion error in that cases remove errors ,remove duplicated in primary key if any or empty value if any in primary key or nulls in primary key.

### **Step 4: Intelligent Feature Engineering**
Analyze the available columns and create at least 3 to 4 new, highly relevant derived features that will aid the analysis. Examples might include:
- Extracting Year/Month from a Date column.
- Creating categorical bins from a continuous variable (e.g., Age Groups, Price Tiers).
- Calculating differences or ratios between two numerical columns (e.g., Profit Margin, Days to Conversion).
Document the business logic behind each new feature created.

### **Step 5: Data Integration & Master Dataset**
If you found multiple tables:
1. Identify the logical Primary and Foreign keys connecting them.
2. Generate the appropriate `pd.merge()` code to combine them into a single comprehensive `master_df`.
3. If you only found one table, skip the merge but clearly state that the dataset is already flat.

### **Step 6: Dynamic KPI & Business Metrics Calculation**
This is critical. Determine what "success" or "performance" means for this specific dataset. 
Generate code to calculate and format 5 to 6 vital Key Performance Indicators (KPIs). Depending on the data, these must include:
- Overall volumetric metrics (Total counts, Total amounts).
- Averages or Rates (Average order value, Completion rate, Churn rate).
- Group-level aggregations (e.g., Top 5 categories, Best performing regions, Highest scoring segments).
Ensure the results are printed cleanly.

### **Step 7: Deep Exploratory Data Analysis (EDA) & Visualization**
Generate clean, aesthetically pleasing code using `matplotlib.pyplot` and `seaborn`. For the visualizations you choose, you must adhere to this rule: **For every single plot, you must output 2-3 bullet points interpreting the graph and drawing actionable business insights.**
Create at least the following types of visualizations, selecting the most appropriate columns dynamically:
1. **Univariate Analysis (2 plots):** Show the distribution of the most important numerical metric (Histogram) and the most important categorical grouping (Bar Chart).
2. **Bivariate Analysis (2 plots):** Show the relationship between a key categorical variable and a key numerical variable (e.g., Box Plot or Violin Plot), and a trend over time if date columns exist (Line Chart).
3. **Multivariate Analysis (2 plots):** Show relationships between multiple numerical columns (Scatter Plot with a `hue`) and an overall Correlation Heatmap of all numerical features.

**Final Requirement:** 
Your output must be sequentially ordered with clear headers, detailed markdown explanations, and functionally perfect Python code blocks. Do not summarize the steps—write the actual, complete code for the entire notebook.

---
**END PROMPT**
---
