

# Athlete Data Analysis Project

## Overview

This project focuses on analyzing data related to athletes, specifically exploring the relationship between athletes' ages, genders, and their profiles obtained from Wikidata. The main goals include:

- Loading athlete data from a CSV file.
- Fetching additional information from Wikidata.
- Analyzing the age distribution of athletes by gender.
- Visualizing the data using histograms.

## Requirements

Before running the code, ensure you have the following packages installed:

- `pandas`
- `requests`
- `matplotlib`
- `seaborn`
- `plotly`

You can install the necessary libraries using pip:

```bash
pip install pandas requests matplotlib seaborn plotly
```

## Directory Structure

Ensure your directory structure looks like this:

```
/project_directory
│
├── Athletes.csv                   # Original athlete data file
├── Athletes_Wikidata_FullName_Age.csv  # Processed athlete data with Wikidata info
├── Not_Found_Names.txt            # Names not found in Wikidata
└── athlete_analysis.py             # Main script for data analysis
```

## How to Run the Code

1. **Clone the repository or download the files:**

   Ensure all files are located in a single directory.

2. **Load Data and Fetch Additional Info:**

   Run the main script to load athlete data from the CSV file and fetch additional information from Wikidata.

   ```python
   # Load and process athletes data
   processed_file_path = 'Athletes_Wikidata_FullName_Age.csv'
   not_found_file_path = 'Not_Found_Names.txt'
   athletes_csv = 'Athletes.csv'

   results = process_athletes(athletes_csv, processed_file_path, not_found_file_path)
   ```

3. **Visualize Data:**

   After processing the data, you can visualize the distribution of athletes' ages by gender. Here’s how you can do it:

   ```python
   # Import necessary libraries
   import pandas as pd
   import matplotlib.pyplot as plt
   import seaborn as sns

   # Load the processed data
   df = pd.read_csv('Athletes_Wikidata_FullName_Age.csv')

   # Filter and visualize data
   df['age'] = pd.to_numeric(df['age'], errors='coerce')
   df_filtered = df[(df['age'] >= 0) & (df['age'] <= 100)]
   df_known_gender = df_filtered[df_filtered['gender'].isin(['Female', 'Male'])]

   # Create a histogram
   plt.figure(figsize=(12, 6))
   sns.histplot(data=df_known_gender, x='age', hue='gender', multiple='dodge', bins=range(0, 101, 5), kde=False, palette={'Female': 'pink', 'Male': 'blue'})
   plt.title("Distribution of Athletes' Ages by Gender")
   plt.xlabel('Age')
   plt.ylabel('Number of Athletes')
   plt.xlim(0, 60)
   plt.grid(True)
   plt.show()
   ```

4. **Explore the Data:**

   You can also explore the data by viewing the first few rows:

   ```python
   df.head()
   ```

## Code Explanation

- The main script fetches athlete information from Wikidata based on names from a provided CSV file.
- It processes the data to extract useful information like age and gender.
- Finally, it generates visualizations to help analyze the distribution of athletes' ages by gender.

## Contribution

Feel free to contribute to this project by suggesting improvements, reporting issues, or submitting pull requests.

## License

This project is licensed under the MIT License. See the LICENSE file for more information.

