# Netflix Data Analysis Project

A six-task data analysis project on a Netflix titles dataset, built with Python, pandas, matplotlib and Plotly. It goes from cleaning the raw data to a final business insights report.

## Dataset

- **Source:** Provided as part of the internship task
- **Raw size:** 8,790 rows and 10 columns (`show_id`, `type`, `title`, `director`, `country`, `date_added`, `release_year`, `rating`, `duration`, `listed_in`)
- **After cleaning:** 8,786 rows and 16 columns
- **Coverage:** titles added from 2008 to 25 September 2021, so **2021 is a partial year**

## Tools Used

- Python 3.14
- pandas, matplotlib, Plotly
- Jupyter Notebook in VS Code

## Project Structure

```
Netflix_project/
├── 01_data_cleaning.ipynb               Task 1
├── 02_content_type_analysis.ipynb       Task 2
├── 03_country_analysis.ipynb            Task 3
├── 04_trend_analysis.ipynb              Task 4
├── 05_rating_genre_analysis.ipynb       Task 5
├── 06_business_insights_report.ipynb    Task 6
├── Dataset.csv                          raw data (never edited)
├── netflix_cleaned.csv                  output of Task 1
├── country_ranking.csv                  output of Task 3
├── Netflix_Business_Insights_Report.html   final report
├── audience_heatmap.html                interactive chart (Task 5)
├── dashboard_1_overview.html            dashboards (Task 6)
├── dashboard_2_geography_genre.html
├── dashboard_3_format_freshness.html
├── charts (.png files for Tasks 2, 3 and 4)
└── README.md
```

## Task 1: Data Cleaning and Preparation

- Found hidden missing values: `isnull()` reported none, but the text "Not Given" was used as a placeholder in `director` (2,588 rows) and `country` (287 rows). Replaced it with "Unknown" and kept the rows.
- Stripped extra spaces, removed 4 duplicate titles, and converted `date_added` to a real date.
- Added columns: `year_added`, `month_added`, `primary_country`, `rating_group`, `duration_value`, `duration_unit`.
- Result: 8,790 rows became 8,786, with 0 empty cells. Output: `netflix_cleaned.csv`.
- Notebook: `01_data_cleaning.ipynb`

## Task 2: Content Type Analysis

- Movies: 6,123 (69.69%). TV Shows: 2,663 (30.31%).
- TV Shows' share of newly added titles rose from 25.0% in 2018 to 33.7% in 2021 (partial year).
- Notebook: `02_content_type_analysis.ipynb`

## Task 3: Country-Wise Content Analysis

- 85 countries represented. The United States holds 38.12% of titles with a known country, India 12.42% and the United Kingdom 7.51%.
- The top 10 countries supply 78.02% of titles, while 42 countries have fewer than 10 titles each.
- Notebook: `03_country_analysis.ipynb`

## Task 4: Trend Analysis by Release Year

- Titles by release year grew fast until 2016 (+62.3%), peaked in 2018 (1,144 titles), then declined.
- From 2018 to 2020, Movies fell from 766 to 517 titles while TV Shows rose from 378 to 436.
- 2021 is a partial year, so its drop is not treated as a real decline.
- Notebook: `04_trend_analysis.ipynb`

## Task 5: Content Rating and Genre Analysis

- Adults (45.58%) and Teens (30.10%) make up about 76% of titles.
- Kids content is 17.4% of TV Shows but only 7.2% of Movies.
- 42 genres, after splitting the multi-genre `listed_in` column. International Movies (2,751 titles) and Dramas (2,423) lead.
- Independent Movies is the most adult genre (71.4% Adults). Interactive charts built with Plotly.
- Notebook: `05_rating_genre_analysis.ipynb`

## Task 6: Business Insights Report

- Capstone report with an executive summary, KPI scorecard, three interactive dashboards and seven actionable insights.
- Main finding: the catalog is movie-heavy and aimed at older audiences, with TV Shows gaining share.
- Notebook: `06_business_insights_report.ipynb`
- Report: `Netflix_Business_Insights_Report.html` (needs an internet connection to load the charts)

## Key Lessons

- A column can hide missing values in plain text, so always check `value_counts()`, not only `isnull()`.
- Check whether the data covers a full year before reading a drop as a trend.
- Genre shares add up to more than 100%, because one title can carry several genres.
- Use the median when a column has a few extreme values.

## How to Run

1. Install the requirements:
   ```
   pip install pandas matplotlib plotly nbformat
   ```
2. Put `Dataset.csv` in the project folder.
3. Run `01_data_cleaning.ipynb` first, since it creates `netflix_cleaned.csv`.
4. Run the other notebooks in any order. Each loads `netflix_cleaned.csv`.
