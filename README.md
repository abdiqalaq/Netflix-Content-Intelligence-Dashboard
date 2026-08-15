# Netflix Content Intelligence Dashboard
## Power Query Data Cleaning and Transformation

## Project Overview

This project focuses on preparing the Netflix Movies and TV Shows dataset for business intelligence analysis using Microsoft Power BI. During Week 2, the primary objective was to clean, transform, and prepare multiple datasets using Power Query to ensure high-quality, analysis-ready data for subsequent modelling, DAX calculations, and dashboard development.

The Power Query stage improves data consistency, removes quality issues, and creates additional features required for interactive reporting.

---

# Datasets Used

The following datasets were imported into Power BI:

- movies_metadata.csv
- credits.csv
- keywords.csv
- links.csv
- ratings.csv

Each dataset was cleaned individually before being integrated into the final data model.

---

# Power Query Data Cleaning

The following data cleaning operations were performed.

## 1. Data Import

All CSV datasets were imported into Power BI using the Power Query Editor.
<img width="1317" height="967" alt="image" src="https://github.com/user-attachments/assets/9ce7b913-52b6-4b2d-bac9-091757d5d656" />

---

## 2. Data Type Corrections

Incorrect data types were corrected to improve consistency and enable accurate analysis.

Examples include:

- Movie ID → Whole Number
- Revenue → Whole Number
- Budget → Whole Number
- Runtime → Whole Number
- Release Date → Date
- Vote Average → Decimal Number
- Vote Count → Whole Number

---

## 3. Duplicate Removal

Duplicate records were identified and removed using unique identifiers to improve data quality.
<img width="1914" height="943" alt="image" src="https://github.com/user-attachments/assets/fd97de2e-ec4b-4739-b121-c5b5fea7526c" />

---

## 4. Blank Row Removal

Completely blank records were removed from all imported datasets.

---

## 5. Text Cleaning

Text fields were standardized using Power Query formatting tools.

Operations performed include:

- Trim
- Clean
<img width="1876" height="955" alt="image" src="https://github.com/user-attachments/assets/158ce50f-0bbd-4f4d-9d21-ea6af2a3bfcb" />

These transformations removed unnecessary spaces and non-printable characters.

---

## 6. Missing Value Handling

Datasets were reviewed for missing values.

Where appropriate:

- Missing values were replaced where necessary.
- Irrelevant null records were retained where they did not affect analysis.
- Important fields were validated before modelling.

---

## 7. Remove Unnecessary Columns

Unused attributes were removed to simplify the data model and improve report performance.

Examples include metadata fields that were not required for analysis.

---

## 8. Date Transformation

The Release Date field was converted into Date format.

Additional date attributes were extracted:

- Year
- Month
- Quarter
- Day

These fields support time-series analysis and dashboard filtering.

---

## 9. Split Columns

Text columns were split using Power Query's Split Column functionality to demonstrate advanced transformation techniques.

---

## 10. Merge Queries

Related datasets were merged using common identifiers to enrich movie records with additional information.

Merge operations were performed using the Merge Queries functionality in Power Query.

---

## 11. Conditional Columns

Business logic was implemented using Conditional Columns.

Example:

Revenue Category

- Blockbuster
- Successful
- Low Revenue

This enables segmentation of movies according to financial performance.

---

## 12. Custom Transformations

Additional calculated attributes were created using Power Query transformation features to improve downstream analysis.

---

# Advanced Power Query Features

The following advanced Power Query techniques were implemented.

- Merge Queries
- Column Profiling
- Reference Queries
- Group By
- Summarized Tables
- Conditional Columns

### Merge Queries

Datasets were merged using common keys to combine related information from multiple tables.
<img width="1891" height="666" alt="image" src="https://github.com/user-attachments/assets/2730c940-f63c-499d-b6df-5c98840c6d2a" />

### Column Profiling

Power Query's Column Quality, Column Distribution, and Column Profile features were used to assess data quality and identify potential issues before modelling.

### Reference Queries

Reference queries were created to preserve the original datasets while generating transformed analytical tables.

### Group By

Grouping operations were performed to summarize movie information, including:

- Number of Movies by Year
- Average Revenue by Year
<img width="1870" height="940" alt="image" src="https://github.com/user-attachments/assets/4730a157-2412-4c9d-8bfb-69042a7089e0" />

### Summarized Tables

Summary tables were generated using Group By aggregations for business reporting and analysis.

### Conditional Columns

Business categories were created using nested conditions to classify records according to predefined business rules.
<img width="1771" height="925" alt="image" src="https://github.com/user-attachments/assets/c7f29fe6-1fd1-4c0b-90de-72ce4248654c" />

---

# Data Preparation Outcome

After completing Power Query transformations:

- Cleaned datasets were produced.
- Duplicate records were removed.
- Data types were standardized.
- Missing values were handled.
- Date dimensions were generated.
- Summary tables were created.
- Queries were optimized for reporting.

The cleaned datasets are now ready for:

- Data Modelling
- Relationship Creation
- DAX Calculations
- Dashboard Development

---

# Evidence Produced

The following evidence was captured during Week 2:

- Raw dataset screenshots
- Power Query Editor screenshots
- Applied Steps screenshots
- Column Profiling screenshots
- Final cleaned dataset screenshots
- Advanced Power Query transformation screenshots

---

# Technologies Used

- Microsoft Power BI Desktop
- Power Query Editor
- CSV Datasets
- GitHub

---

# Week 2 Deliverables

- Cleaned datasets
- Power Query transformations
- Advanced Power Query operations
- Prepared analytical tables
- Documentation


# Part 3: Data Modelling

## Overview

This section focuses on designing the data model used in the Power BI project. The objective was to organize the dataset into a structured model that enables efficient filtering, accurate DAX calculations, and high-performance dashboard visualizations.

## Data Model Structure

### Fact Table

The **Ratings** table serves as the central fact table since it contains transactional records of user movie ratings.

**Key fields:**

* `movieId`
* `userId`
* `rating`
* `timestamp`

### Dimension Tables

The model incorporates several dimension tables to provide descriptive information:

| Table               | Purpose                                                                                      |
| ------------------- | -------------------------------------------------------------------------------------------- |
| **movies_metadata** | Stores movie details such as title, genres, runtime, language, popularity, and release date. |
| **credits**         | Contains cast and crew information.                                                          |
| **keywords**        | Stores movie keywords used for categorization.                                               |
| **Date**            | Custom calendar table used for time-based analysis.                                          |

The **links** table functions as a bridge between MovieLens and TMDb identifiers, allowing relationships between datasets that use different movie IDs.

## Date Table

A custom Date table was created using DAX's `CALENDAR()` function to support time intelligence.

Additional columns include:

* Year
* Quarter
* Month
* Month Number

These fields enable chronological filtering and trend analysis across the dashboard.

## Table Relationships

The data model includes the following relationships:

| Relationship               | Cardinality | Cross Filter |
| -------------------------- | ----------- | ------------ |
| movies_metadata → credits  | One-to-One  | Both         |
| movies_metadata → keywords | One-to-One  | Both         |
| movies_metadata → links    | Many-to-One | Single       |
| links → ratings            | Many-to-One | Single       |
| Date → movies_metadata     | One-to-Many | Single       |

## Final Data Model

The completed model follows a **star-like schema**:

* **Fact Table:** Ratings
* **Dimension Tables:** Movies Metadata, Credits, Keywords, Date
* **Bridge Table:** Links

This design improves query performance, supports efficient filtering, simplifies DAX calculations, and provides a solid foundation for interactive Power BI dashboards.

![Final Data Model](Screenshots/ModelView.png)



# DAX Measures Implemented

The dashboard includes a total of **19 DAX measures**, organized into the required categories.

## 1. Basic Aggregation Measures

These measures summarize key numerical values in the dataset.

- **Total Movies** – Counts the total number of movies.
- **Total Budget** – Calculates the total production budget.
- **Total Revenue** – Calculates the total movie revenue.
- **Average Rating** – Computes the average movie rating.
<img width="1356" height="747" alt="image" src="https://github.com/user-attachments/assets/3bea0af8-4716-4873-9fa3-275d38393ab6" />

---

## 2. Time-Based Measures

These measures analyze movie performance over time using the **release_year** field.

- **Movies Released** – Counts the number of movies released each year.
- **Revenue by Year** – Calculates total revenue by release year.
- **Budget by Year** – Calculates total budget by release year.
- **Average Rating by Year** – Computes the average rating for movies released each year.
<img width="1361" height="740" alt="image" src="https://github.com/user-attachments/assets/2f1bb8ec-dfa4-45e1-a165-20a1ff26acd5" />

---

## 3. Percentage and Ratio Measures

These measures evaluate financial performance.

- **Profit** – Calculates the difference between total revenue and total budget.
- **Profit Margin** – Computes profit as a percentage of total revenue.
- **Average Revenue per Movie** – Calculates the average revenue generated per movie.
<img width="1359" height="742" alt="image" src="https://github.com/user-attachments/assets/a57c9311-6c01-4422-82ba-83e41c706b43" />

---

## 4. Ranking Measures

These measures rank movies based on key performance metrics.

- **Rank by Revenue** – Ranks movies from highest to lowest revenue.
- **Rank by Budget** – Ranks movies from highest to lowest production budget.
- **Rank by Rating** – Ranks movies based on their average ratings.
<img width="1360" height="744" alt="image" src="https://github.com/user-attachments/assets/f25d4551-46fb-4626-86b1-60033c3c5127" />

---

## 5. Conditional KPI / Status Measures

These measures classify performance using conditional logic.

- **Rating Status** – Categorizes ratings as *Good* or *Needs Attention*.
- **Profit Status** – Indicates whether a movie is *Profitable* or made a *Loss*.
- **Revenue Status** – Classifies movies as *High Revenue* or *Low Revenue* based on average revenue.
<img width="1358" height="745" alt="image" src="https://github.com/user-attachments/assets/32e752e1-d4a5-4e6d-a857-c8251451d612" />

---

## 6. Dynamic Measures

These measures make the report interactive.

- **Selected Budget Category** – Displays the currently selected budget category from the slicer.
- **Dashboard Title** – Dynamically updates the dashboard title based on the selected budget category.
<img width="1348" height="742" alt="image" src="https://github.com/user-attachments/assets/4423907c-c8af-4dc5-ad8c-c66de2f9585d" />

---

## Summary

| Category | Number of Measures |
|----------|-------------------:|
| Basic Aggregation | 4 |
| Time-Based | 4 |
| Percentage & Ratio | 3 |
| Ranking | 3 |
| KPI / Status | 3 |
| Dynamic | 2 |
| **Total** | **19** |


## Dashboard Visualizations & Layout

The Power BI dashboard is designed using a **Cinematic Dark Theme** with high-contrast visual cues for executive-level reporting. It spans five dedicated pages:

### Page 1: Executive Summary
* **Dynamic Header Banner**: Powered by `[Dynamic Title]`, updating dynamically based on the selected language slicer.
* **Core KPI Cards**: Four high-level metric cards showing `Total Movies`, `Total Revenue`, `Total Profit`, and `Average Rating`.
* **Budget vs. Revenue Split**: A Donut chart highlighting overall expenditure versus gross revenue.
* **Top 10 High-Profit Movies**: Horizontal Clustered Bar Chart filtered using a `Top 10 N` visual filter by `[Total Profit]`.
* **Global Slicers**: Interactive filters for `release_date` (Range Slider), `original_language` (Dropdown), and `status`.

<img width="745" height="343" alt="image" src="https://github.com/user-attachments/assets/11d2be26-1ebf-4900-a653-9e2b01f2d7cd" />


### Page 2: Financial Trend & Market Growth Analysis
* **Revenue & Movie Count Over Time**: A Line and Stacked Column Chart tracking yearly revenue alongside production volume.
* **Profit Breakdown (Decomposition Tree)**: An interactive visual allowing users to drill down into `[Total Profit]` by language, status, and release year.
* **YoY Performance Indicator**: A KPI visual measuring yearly revenue growth against the `[YoY Revenue Growth %]` target.

<img width="601" height="340" alt="image" src="https://github.com/user-attachments/assets/19059b76-c6a6-45a2-9baf-989e96aa6e7a" />



### Page 3: Geographic & Language Performance Matrix
* **Global Production Heatmap**: Filled Map displaying revenue intensity across production countries.
* **Language vs. Rating Matrix**: A Matrix visual mapping language against binned ratings (1–10), formatted with **Gradient Background Color (Conditional Formatting)**.
* **Top 10 Languages by Box Office**: Clustered Bar Chart displaying the highest-grossing original languages.

<img width="601" height="337" alt="image" src="https://github.com/user-attachments/assets/b93b9494-0c9d-449a-97b3-3430a28d4f4e" />





### Page 4: Detailed Movie Drill-Through
* **Drill-Through Target**: Configured with `movies_metadata[title]` and `original_language` drill-through fields, complete with an automated Back Navigation button.
* **Movie Inspection Table**: Granular details including title, release date, runtime, budget, revenue, profit, rating, and vote counts.
* **Search Slicer**: A text-search slicer for instant title lookup.

<img width="606" height="340" alt="image" src="https://github.com/user-attachments/assets/29508243-c711-4c65-bccf-1d03bbc65b5f" />


### Page 5: Ratings & Audience Sentiment
* **Quality Target Score (Gauge Chart)**: Bounded between `0` and `10` with a target threshold marker set at `7.0`.
* **User Engagement vs. Quality (Scatter Plot)**: Plots `Total Rating Count` (X-Axis) against `Average Rating` (Y-Axis), with bubble size representing `Total Revenue`.

<img width="604" height="337" alt="image" src="https://github.com/user-attachments/assets/3c6dd0bf-096a-40b6-9818-c102ce9a0a73" />







