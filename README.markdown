# Property Prices in Tunisia: Data Cleaning Project

![Banner](https://imgs.search.brave.com/tSH32mSSIZZUY7viu9lEhADoBG-a1Os-0fPc9rCIu7s/rs:fit:0:180:1:0/g:ce/aHR0cHM6Ly9jZG4u/Z2xvYmFscHJvcGVy/dHlndWlkZS5jb20v/YXNzZXRzL2ltZy9D/Ty1UTk8tSTAwLmpw/Zw)
*Clean and prepare real estate data for analysis with a structured, reproducible pipeline.*

## 📋 Project Overview

This project processes the "Property Prices in Tunisia" dataset to produce a clean, analysis-ready dataset. The data cleaning pipeline addresses common issues such as missing values, duplicates, outliers, and inconsistent formatting, while adding new features to enhance the dataset's utility. The pipeline is implemented in Python using pandas and seaborn, with each step saved as a separate script for modularity and reproducibility.

The final output, `final_cleaned_property_prices.csv`, is suitable for downstream tasks like exploratory data analysis, visualization, or machine learning.

## 🛠️ Data Cleaning Steps

The data cleaning process follows a structured approach, with each step addressing a specific issue identified in the dataset. Below is an overview of the steps:

| Step | Description | Output File |
|------|-------------|-------------|
| 1. Missing or Invalid Data Handling | Replaces -1 values with NaN in `room_count`, `bathroom_count`, and `size`, and flags invalid sizes (≤ 0 or NaN) with `is_surface_valid`. | `cleaned_property_prices_step1.csv` |
| 2. Duplicate Records | Removes 1,613 exact duplicate rows to prevent overrepresentation. | `cleaned_property_prices_step2.csv` |
| 3. Outlier Detection | Flags prices > 5,000,000 TND as outliers with `is_price_outlier` for review. | `cleaned_property_prices_step3.csv` |
| 4. Formatting Inconsistencies | Standardizes `type` and `category` to title case and trims whitespace. | `cleaned_property_prices_step4.csv` |
| 5. Column Renaming and Standardization | Renames `room_count` to `bedrooms`, `bathroom_count` to `bathrooms`, creates binary `listing_type` (1 for Sale, 0 for Rent), and drops `type`. | `cleaned_property_prices_step5.csv` |
| 6. Feature Engineering | Adds `price_per_sqm` (price/size) for value comparison across properties. | `cleaned_property_prices_step6.csv` |
| 7. Final Data Validation and Export | Verifies missing values, data types, and statistics, then exports the final dataset. | `final_cleaned_property_prices.csv` |

## 📦 Prerequisites

To run the data cleaning pipeline, ensure you have the following:

- **Python 3.8+**: Installed on your system.
- **Required Libraries**:
  ```bash
  pip install pandas numpy seaborn
  ```
- **Dataset**: The original dataset, `Property Prices in Tunisia.csv`, available in the project directory or from [source link, if applicable].
- **Environment**: A Python environment (e.g., VS Code, Jupyter Notebook, or terminal).

## 🚀 Setup and Usage

1. **Clone or Download the Project**:
   - Place all Python scripts and the original dataset in a directory (e.g., `C:\Users\HP\Downloads\archive\`).
   - Example directory structure:
     ```
     data_cleaning_project/
     ├── Property Prices in Tunisia.csv
     ├── missing_data_handling.py
     ├── duplicate_records_handling.py
     ├── outlier_detection.py
     ├── formatting_inconsistencies.py
     ├── column_renaming_standardization.py
     ├── feature_engineering.py
     ├── final_validation_export.py
     ├── README.md
     ```

2. **Run the Scripts Sequentially**:
   - Each script loads the output from the previous step (e.g., `cleaned_property_prices_step1.csv` for step 2).
   - In VS Code or a terminal, run each script in order:
     ```bash
     python missing_data_handling.py
     python duplicate_records_handling.py
     python outlier_detection.py
     python formatting_inconsistencies.py
     python column_renaming_standardization.py
     python feature_engineering.py
     python final_validation_export.py
     ```
   - Alternatively, use a Jupyter notebook to combine all steps (see `data_cleaning.ipynb` if provided).

3. **Verify Outputs**:
   - Each script generates a CSV file (e.g., `cleaned_property_prices_step1.csv` to `final_cleaned_property_prices.csv`).
   - Check console outputs for verification steps (e.g., missing value counts, duplicate counts).

4. **Use the Final Dataset**:
   - The final output, `final_cleaned_property_prices.csv`, is ready for analysis or visualization.

## 💻 Example Output

Running `final_validation_export.py` produces output like:

```plaintext
Missing values in critical columns:
price          0
size           123
bedrooms       456
bathrooms      456
category       0
listing_type   0
price_per_sqm  123
dtype: int64

Data types of all columns:
price              float64
size               float64
bedrooms           float64
bathrooms          float64
category           object
listing_type       int64
price_per_sqm      float64
...

Final cleaned dataset exported as 'final_cleaned_property_prices.csv'
```

## 🎨 Styling in VS Code

To view this README and code with a professional style in VS Code:
- Install the **Markdown Preview Enhanced** extension for enhanced Markdown rendering.
- Use a theme like **Dracula** or **GitHub Dark** (`File > Preferences > Color Theme`).
- Enable `Editor: Format On Save` with **Prettier** for consistent Markdown and Python formatting.
- Use a clean font like **Fira Code** (`Editor: Font Family` in Settings).

## 🙌 Acknowledgments

- **Dataset**: Sourced from [source link, if applicable, or "Property Prices in Tunisia dataset"].
- **Tools**: Built with pandas, numpy, and seaborn for robust data processing.
- **Contributors**: [Your name, if desired] for implementing the pipeline.

---

*Happy analyzing! For issues or contributions, please open an issue or contact [your email, if desired].*
