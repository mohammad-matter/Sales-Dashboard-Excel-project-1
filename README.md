# 📊 Sales Dashboard | Excel Project

## Background

This interactive Excel dashboard was built to analyze sales and profitability data for a retail superstore across the United States. The goal is to help business stakeholders quickly identify top-performing regions, product categories, and yearly trends to make data-driven decisions.

The dataset used is the **Sample Superstore** dataset, which contains **~10,000 records** of retail transactions from **2021 to 2024**, including details on sales, profit, discounts, product categories, and geographic information across **4 regions** in the US.

### The questions I wanted to answer through this dashboard:

1. 💰 How do **sales and profit** perform across different **regions** and **years**?
2. 🗺️ Which **states** are driving the most revenue within each region?
3. 📦 Which **product sub-categories** are the **top performers**?
4. 📈 What is the **yearly trend** for sales and profit — are we growing or declining?

## Excel Skills Used

The following Excel skills were utilized for analysis:

- 📐 **Formulas** — `SUMIFS()`, `AVERAGEIFS()`, `IFERROR()`, `IF()`
- ✅ **Data Validation** — Dropdown lists for Year, Region, and Metric selection
- 📊 **Charts** — Bar Chart and Line Chart
- 🧮 **Conditional Calculations** — Dynamic metric switching (Sales vs. Profit)
- 🎨 **Dashboard Design** — Clean layout with interactive controls

## Dashboard Overview


![dashboard_demo](![dashboard_demo_hq](https://github.com/user-attachments/assets/27f28321-fd6f-4e4e-b837-226d8b22a5f1)



## Dashboard Build

### 📐 Formulas

#### KPI Calculations

To calculate the core KPIs (Total Sales, Total Profit, Profit Margin, Average Discount), I used `SUMIFS()` and `AVERAGEIFS()` formulas that dynamically respond to the selected Year and Region.

```
=SUMIFS(Raw_Data[Sales], Raw_Data[Region], B2, Raw_Data[Year], A2)
```

🔢 **Formula Purpose:** This formula calculates the total sales for the selected region and year, giving us the primary KPI value.

```
=E2/SUMIFS(Raw_Data[Sales], Raw_Data[Year], A2, Raw_Data[Region], B2)
```

🔢 **Formula Purpose:** This formula calculates the profit margin by dividing total profit by total sales for the selected filters.

#### Dynamic Metric Switching

The dashboard allows users to switch between **Sales** and **Profit** views using a single dropdown. This is powered by a conditional `SUMIFS()` with `IF()`:

```
=SUMIFS(IF($C$2="Sales", Raw_Data[Sales], Raw_Data[Profit]),
        Raw_Data[Sub-Category], M2,
        Raw_Data[Year], $A$2,
        Raw_Data[Region], $B$2)
```

🔢 **Formula Purpose:** This formula checks the selected metric (Sales or Profit) and calculates the corresponding value for each sub-category, filtered by year and region.

📉 **Key Insight:** This approach eliminates the need for separate charts or sheets — one formula powers the entire dynamic view.

### ✅ Data Validation

To make the dashboard interactive, I implemented data validation dropdowns for three controls:

| Control | Options |
|---|---|
| **Select Year** | 2021, 2022, 2023, 2024 |
| **Select Region** | South, West, Central, East |
| **Metric Switch** | Sales, Profit |

🔒 **Enhanced Usability:**
- User input is restricted to predefined, validated options
- Incorrect or inconsistent entries are prevented
- The entire dashboard updates dynamically based on selections

### 📊 Charts

#### Bar Chart — Sub-Category Performance

🛠️ **Excel Features:** Utilized a horizontal bar chart to compare performance across all 17 product sub-categories.

🎨 **Design Choice:** Horizontal bar chart for easy visual comparison of values across categories.

💡 **Insights Gained:**
- **Machines** and **Phones** are consistently top-performing sub-categories in sales
- **Copiers** shows zero sales in some region-year combinations, indicating limited distribution
- **Fasteners** and **Supplies** are the lowest performers across most filters

#### Line Chart — Yearly Trend

🛠️ **Excel Features:** Utilized a line chart to display the selected metric's trend over 4 years (2021–2024).

🎨 **Design Choice:** Line chart to clearly show growth or decline patterns over time.

💡 **Insights Gained:**
- Sales show variation across years, with peaks and dips depending on the region
- This trend view helps identify whether a region is **growing** or **declining** in performance

## Data Structure

The workbook is organized into **4 sheets**:

| Sheet | Purpose |
|---|---|
| **Raw Data** | Contains ~10,000 transaction records with 16 columns |
| **Admin** | Stores dropdown list values (Years, Regions, Metrics) |
| **Calculations** | All formulas and computed values that power the dashboard |
| **Dashboard** | The final interactive dashboard with charts and controls |

### Dataset Columns

The raw data includes the following fields:

`Ship Mode` · `Segment` · `Country` · `City` · `State` · `Postal Code` · `Region` · `Category` · `Sub-Category` · `Sales` · `Quantity` · `Discount` · `Profit` · `Profit Margin` · `Order Date` · `Year`

## Conclusion

This dashboard provides a powerful yet simple tool for exploring superstore performance data. The combination of dynamic formulas with data validation creates a fully interactive experience without needing VBA or Power Query.

### Key Takeaways:

- 🗺️ **Regional Disparities:** Performance varies significantly across regions — some states dominate while others contribute minimally
- 📦 **Product Focus:** Technology products (Machines, Phones) tend to lead in sales, while Office Supplies have lower individual values but higher volume
- 📈 **Trend Analysis:** Year-over-year trends help identify growth opportunities and areas needing attention
- 💡 **Dynamic Dashboards:** Using `IF()` inside `SUMIFS()` enables metric switching without duplicating charts or formulas
