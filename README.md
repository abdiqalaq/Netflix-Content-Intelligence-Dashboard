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

### Page 2: Financial Trend & Market Growth Analysis
* **Revenue & Movie Count Over Time**: A Line and Stacked Column Chart tracking yearly revenue alongside production volume.
* **Profit Breakdown (Decomposition Tree)**: An interactive visual allowing users to drill down into `[Total Profit]` by language, status, and release year.
* **YoY Performance Indicator**: A KPI visual measuring yearly revenue growth against the `[YoY Revenue Growth %]` target.

### Page 3: Geographic & Language Performance Matrix
* **Global Production Heatmap**: Filled Map displaying revenue intensity across production countries.
* **Language vs. Rating Matrix**: A Matrix visual mapping language against binned ratings (1–10), formatted with **Gradient Background Color (Conditional Formatting)**.
* **Top 10 Languages by Box Office**: Clustered Bar Chart displaying the highest-grossing original languages.

### Page 4: Detailed Movie Drill-Through
* **Drill-Through Target**: Configured with `movies_metadata[title]` and `original_language` drill-through fields, complete with an automated Back Navigation button.
* **Movie Inspection Table**: Granular details including title, release date, runtime, budget, revenue, profit, rating, and vote counts.
* **Search Slicer**: A text-search slicer for instant title lookup.

### Page 5: Ratings & Audience Sentiment
* **Quality Target Score (Gauge Chart)**: Bounded between `0` and `10` with a target threshold marker set at `7.0`.
* **User Engagement vs. Quality (Scatter Plot)**: Plots `Total Rating Count` (X-Axis) against `Average Rating` (Y-Axis), with bubble size representing `Total Revenue`.
