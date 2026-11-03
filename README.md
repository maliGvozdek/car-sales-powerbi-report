# Car Sales Analysis – Power BI Report

Interactive Power BI report analysing 23,906 car sales: sales trends over time,
regional differences, customer habits and dealer performance.

![Report overview](report/screenshots/overview.png)

## Overview

Business analysis helps companies make better decisions based on data. By analysing sales, customers and market trends, it is possible to spot patterns, strengths and weaknesses, and find opportunities to improve.

This project analyses the car market. The goal was to build an interactive business report in Power BI and use data visualisation techniques to present complex data in a clear and understandable way. The report gives insight into:

- vehicle sales and sales trends over time
- geographic characteristics of the market
- customer habits
- dealer performance

## Dataset

- **Source:** [Car Sales Report](https://www.kaggle.com/datasets/missionjee/car-sales-report) by Vasu_Avasthi on Kaggle
- **Size:** 23,906 rows, 16 attributes
- **Licence:** Apache 2.0 (see [data/LICENSE.txt](data/LICENSE.txt))

The dataset is suitable for many kinds of analysis, such as market analysis, seasonal patterns, predictive analysis and supply chain analysis. Its size and number of attributes make it a good base for exploring the car market.

## Data preparation

The raw data needed two steps: cleaning, and transforming it into a star schema. Both were done in Python (pandas) in [scripts/sp_p.ipynb](scripts/sp_p.ipynb).

- Replaced the text column `Car_id` with a new integer ID, `Sale_ID`
- Checked the structure with `df.info()` and looked for duplicates (none found)
- Fixed an encoding error in text values, e.g. "DoubleÂ Overhead Camshaft" → "Double Overhead Camshaft"
- Removed the columns `Dealer_No` and `Phone`, which were not needed for the analysis
- Converted `Date` to a date type and split it into year, month and day
- Created four dimension tables from unique combinations of values, each with its
  own ID, then built the fact table by joining them back to the sales data

## Data model

The tables were imported into Power BI as CSV files (Get data → Text/CSV).

<!-- photo-->

Screenshot above shows the star model. fact table is in the middle, while other dimensional tabels are around it.

## Report pages

After importing the tables into Power BI, the last step was building the reports. The final result is one home page and five reports, each covering its own category.

### Home page

<!-- photo -->

The main purpose of this page is easy navigation. It has five buttons, each leading to one report, and a couple of charts.

### Sales by brand

<!-- photo -->

Compares sales across car brands. A bar chart shows the number of cars sold per brand, and pie charts show sales by body style and by colour. Cards show the average price, most popular model and brand, and the preferred engine and transmission. This helps a dealer see which brands and car features are most in demand.

### Sales trend over time

<!-- photo -->

Shows the number of cars sold over time, with a forecast of future sales based on past data. It also includes a KPI for the total sales goal, sales by dealer, and cards for the top model, brand and dealer. It reveals seasonal demand: for example, sales are high in September.

### Geographical analysis

<!-- photo -->

A map shows where dealers are located by region, and a bar chart compares sales per dealer. Cards show the top dealer, total sales value, average price and number of sales. A chart compares the number of sales with the average price by month. Useful for tracking dealer performance and setting sales goals.

### Customer analysis

<!-- photo -->

Looks at who buys cars: the split by gender, average price, and average and median customer income. A combined chart shows which income groups buy the most expensive cars, and a scatter plot compares car price with annual income.

### Price analysis

<!-- photo -->

Shows the average price per brand (with a region filter), the relationship between price and income, the top 5 best-selling models, and sales by body style.

## Tools
Python (pandas) · Power BI · Jupyter Notebook

## Repository structure
```
data/      original dataset, fact and dimension tables, licence
docs/      full project report (PDF, in Croatian)
report/    Power BI file (.pbix) and screenshots
scripts/   Jupyter notebook for data cleaning and modelling
```

## Data & licence
The original dataset is by Vasu_Avasthi, published on Kaggle under the Apache 2.0 licence. I cleaned it in Python and transformed it into a star schema (fact and dimension tables) for this project.

## Author
Luka Gvozdanović - [LinkedIn](www.linkedin.com/in/luka-gvozdanovic)
