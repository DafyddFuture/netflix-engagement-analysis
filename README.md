# Netflix Engagement Analysis

## Project Overview

This project analyses Netflix's official *What We Watched* engagement data to explore viewing patterns across seven reporting periods from 2023 H1 to 2026 H1.

The analysis examines how viewing has changed over time, how engagement is distributed across titles, differences between Movies and Shows, the relationship between global availability and engagement, and how newer and older catalogue content perform.

The project uses Python and pandas for data cleaning, transformation and exploratory data analysis, with Matplotlib used for data visualisation.

## Analytical Questions

The analysis focuses on seven key questions:

1. How have total reported Netflix viewing hours changed over time?
2. Which titles recorded the highest viewing hours in a single reporting period?
3. How concentrated is viewing among the most-watched titles?
4. How do Movies and Shows compare in terms of Hours Viewed and Netflix Views?
5. Is global availability associated with higher engagement?
6. How does content age relate to engagement, and do older catalogue titles continue to attract viewing?
7. How have viewing hours for Movies and Shows changed over time?

## Data Source

The project uses Netflix's official *What We Watched: A Netflix Engagement Report* datasets covering seven half-year reporting periods:

- 2023 H1
- 2023 H2
- 2024 H1
- 2024 H2
- 2025 H1
- 2025 H2
- 2026 H1

The datasets contain title-level engagement information including Hours Viewed and, in later reporting periods, Runtime, Views, Content Type, Release Date and global availability.

Raw Excel files are stored locally in `data/raw/` and are excluded from Git using `.gitignore`. The cleaned and combined dataset used for analysis is stored in `data/processed/netflix_engagement_clean.csv`.

## Data Preparation

The seven Netflix reporting files were inspected, standardised and combined into a single analysis-ready dataset.

Key preparation steps included:

- Standardising column names and structure across reporting periods.
- Adding `Report Period` to identify each half-year dataset.
- Adding and standardising `Content Type` as Movie or Show where available.
- Converting `Release Date` to a datetime format.
- Converting `Views` to a nullable integer data type.
- Converting runtime values into a new `Runtime Minutes` variable.
- Treating special `*` values and unavailable fields as missing data rather than estimating them.
- Identifying and excluding aggregate `Other Movies` and `Other Shows` rows from title-level analysis while retaining them where appropriate for overall totals.
- Checking for duplicate observations without automatically removing legitimate repeated title-period records.
- Creating a cleaned dataset containing **115,956 observations** across the seven reporting periods.

The raw source files remain unchanged, with all transformations performed separately in the cleaning workflow.

## Key Findings

- **Overall engagement increased modestly:** reported viewing hours increased by approximately **4.5%** from 2023 H1 to 2026 H1, reaching **97.7 billion hours** in 2026 H1.

- **Viewing is highly concentrated:** the top **1%** of title-period observations accounted for **24.8%** of title-level viewing hours. The top **10%** accounted for **68.6%**.

- **Shows dominate viewing hours:** from 2023 H2 onwards, Shows generated approximately **73.7%** of title-level Hours Viewed. Movies, however, accounted for **58.2%** of Netflix Views, illustrating the effect of runtime on the two metrics.

- **Global availability is associated with stronger engagement:** globally available titles generated approximately **3.3 times** the median Hours Viewed and **3.5 times** the median Netflix Views of titles that were not globally available.

- **Newer content generally records higher typical engagement:** titles aged 0–1 years generated a median **5.2 million Hours Viewed** per title-period observation, compared with **1.4 million** for titles aged 6–10 years. A small group of older catalogue titles remained strong performers.

- **The Movie–Show gap widened over time:** between 2023 H2 and 2026 H1, Show viewing hours increased by **13.3%**, while Movie viewing hours decreased by **7.4%**.

## Tools & Technologies

- **Python** — data analysis and transformation
- **pandas** — data cleaning, manipulation and aggregation
- **Matplotlib** — data visualisation
- **Jupyter Notebook** — exploratory analysis and documentation
- **Git & GitHub** — version control and project management
- **VS Code** — development environment

## Project Structure

netflix-engagement-analysis/
├── data/
│   ├── raw/                  # Original Netflix Excel files (not tracked by Git)
│   └── processed/
│       └── netflix_engagement_clean.csv
├── notebooks/
│   ├── 01_data_inspection.ipynb
│   ├── 02_data_cleaning.ipynb
│   └── 03_eda.ipynb
├── .gitignore
└── README.md

## Project Structure

```text
netflix-engagement-analysis/
├── data/
│   ├── raw/                  # Original Netflix Excel files (not tracked by Git)
│   └── processed/
│       └── netflix_engagement_clean.csv
├── notebooks/
│   ├── 01_data_inspection.ipynb
│   ├── 02_data_cleaning.ipynb
│   └── 03_eda.ipynb
├── .gitignore
└── README.md
```

## Limitations

Several limitations should be considered when interpreting the results:

- Netflix's reporting methodology and available fields changed across reporting periods, so comparisons over time should be interpreted with care.
- `Views` and `Content Type` are unavailable for 2023 H1.
- Release Date is available for only 37,112 of the 115,952 individual title-period observations.
- Netflix Views are calculated from Hours Viewed relative to runtime and should not be interpreted as unique viewers.
- The same title may appear in multiple reporting periods, meaning observations represent title-period combinations rather than unique titles.
- Global availability is associated with higher engagement, but the analysis does not establish that global availability causes higher viewing.

## Notebook Workflow

The analysis is organised into three notebooks:

1. **`01_data_inspection.ipynb`** — inspection of the original Netflix datasets, schemas and reporting differences.
2. **`02_data_cleaning.ipynb`** — cleaning, standardisation, feature creation and combination of the seven reporting periods.
3. **`03_eda.ipynb`** — exploratory data analysis, visualisation and interpretation of the key engagement patterns.
