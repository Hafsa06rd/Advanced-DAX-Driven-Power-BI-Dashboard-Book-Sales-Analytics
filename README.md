# Advanced-DAX-Driven-Power-BI-Dashboard-Book-Sales-Analytics


<div align="center">

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Data Analytics](https://img.shields.io/badge/Data%20Analytics-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)

**An interactive 11-page Power BI dashboard analyzing 550 Amazon bestselling books (2009–2019),
featuring advanced DAX measures, decomposition trees, scatter analytics, and YTD intelligence.**

</div>

---

##  Project Overview

This dashboard explores reader behavior, pricing dynamics, and genre trends across Amazon's Top 50 Bestselling Books over a decade (2009–2019).

The project demonstrates proficiency in:
- **Power BI report design** across multiple page types
- **Advanced DAX** : including YTD, CALCULATE, SWITCH, MIN/MAX, MEDIAN, and custom classifiers
- **Visual storytelling** using 8+ distinct chart types
- **Business intelligence thinking** applied to a consumer-market dataset

---

##  Business Questions Answered

| # | Question |
|---|----------|
| 1 | How have total book reviews evolved year over year from 2009 to 2019? |
| 2 | Is there a correlation between book price and user rating? |
| 3 | Which genre — Fiction or Non Fiction — dominates the bestseller list? |
| 4 | Which books and authors consistently accumulate the highest review volumes? |
| 5 | How are books distributed across low, medium, and high review categories? |
| 6 | What is the year-to-date review performance relative to historical trends? |
| 7 | Which authors and genres drive the most reader engagement over time? |

---

##  Dashboard Pages

| Page | Visual Type | Description |
|------|-------------|-------------|
| **KPI Card** | Cards (×6) | Key metrics: Avg Rating, Min/Max Price, Total Books, Total Reviews, Median Rating |
| **Total Reviews by Year** | Line Chart | Year-over-year review volume split by Fiction vs. Non Fiction |
| **Total Books by Year** | Combo Chart | Books published per year with genre breakdown |
| **Total Books by Genre** | Donut Chart | Genre distribution across the full dataset |
| **Total Review by Name** | Bar Chart | Top books ranked by total review count |
| **Average Rating by Genre** | Pie Chart | Average user rating comparison by genre |
| **Scatter: Price vs. Rating** | Scatter Plot | Correlation between book price and user rating, sized by reviews |
| **Total Reviews YTD & Category** | Column Chart | YTD review measure alongside custom review category classification |
| **Time Series Area Chart** | Area Chart | Dual-series trend of reviews and books over time |
| **Decomposition Tree** | Decomp Tree | Drill-down of Total Reviews → Author → Year → Genre |
| **Stacked Column Chart** | Combo Chart | Stacked review volume by year with genre segmentation |

---

##  Key DAX Measures

### Total Reviews
```dax
Total Reviews = SUM(Hafsa_bestsellers[Reviews])
```

### Average Rating
```dax
Avg Rating = AVERAGE(Hafsa_bestsellers[User Rating])
```

### Median Rating
```dax
Median Rating = MEDIAN(Hafsa_bestsellers[User Rating])
```

### Total Books
```dax
Total Books = COUNTROWS(Hafsa_bestsellers)
```

### Min & Max Price
```dax
Min Price = MIN(Hafsa_bestsellers[Price])
Max Price = MAX(Hafsa_bestsellers[Price])
```

### Total Reviews YTD
```dax
Total Reviews YTD =
TOTALYTD(
    SUM(Hafsa_bestsellers[Reviews]),
    Hafsa_bestsellers[Year]
)
```

### Review Category (Custom Classifier)
```dax
Review Category =
SWITCH(
    TRUE(),
    [Total Reviews] < 5000,  "Low",
    [Total Reviews] < 20000, "Medium",
    "High"
)
```

---

##  Dataset

| Attribute | Details |
|-----------|---------|
| **Original Name** | Amazon Top 50 Bestselling Books 2009–2019 |
| **Source** | [Kaggle — sootersaalu](https://www.kaggle.com/datasets/sootersaalu/amazon-top-50-bestselling-books-2009-2019) |
| **Records** | 550 rows |
| **Time Range** | 2009 – 2019 |
| **License** | Public / Open |

###  Dataset Naming Note

The dataset used in this Power BI file was **renamed for customization and project organization purposes**. The internal table name referenced throughout all DAX measures and visuals is `bestsellers_data`, which differs from the original filename on Kaggle.

> The original dataset file will be provided in this repository under the `/data` folder, along with the Kaggle source link above.

**If you want to run the `.pbix` file with the original Kaggle dataset, you have two options:**

**Option A : Rename the file before connecting (recommended):**
Download the CSV from Kaggle and rename it to match the name expected by the Power Query source before reconnecting.

**Option B : Update the source in Power Query:**
Connect to the file under any name, then verify that the query name in Power Query Editor matches `bestsellers_data`. If it doesn't, rename the query accordingly so all DAX measures resolve correctly.

### Columns

| Column | Type | Description |
|--------|------|-------------|
| `Name` | Text | Book title |
| `Author` | Text | Author name |
| `User Rating` | Float | Rating out of 5.0 |
| `Reviews` | Integer | Number of Amazon customer reviews |
| `Price` | Integer | Price in USD |
| `Year` | Integer | Year the book appeared in the Top 50 |
| `Genre` | Text | Fiction or Non Fiction |

---

##  Tools & Technologies

| Tool | Usage |
|------|-------|
| **Power BI Desktop** | Report design, data modeling, visualization |
| **DAX** | All calculated measures and KPIs |
| **Power Query (M)** | Data import and light transformation |
| **Microsoft Excel / CSV** | Source data format |

---

##  How to Use

### Prerequisites
- [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (any version from 2023 onward)

### Steps

1. **Clone or download** this repository
2. **Download the dataset** from [Kaggle](https://www.kaggle.com/datasets/sootersaalu/amazon-top-50-bestselling-books-2009-2019) and save the CSV locally
3. **Open** `Advanced DAX-Driven Power BI Dashboard — Book Sales Analytics.pbix` in Power BI Desktop
4. **Reconnect the data source:**
   - Go to `Home → Transform Data`
   - Right-click the `Hafsa_bestsellers` query → `Edit`
   - In Applied Steps, click `Source` → update the file path to your downloaded CSV
   - Click `Close & Apply`
5. All visuals and DAX measures will reload automatically

---

##  Key Insights

- **Non Fiction** books maintained a consistent presence across all 11 years, while **Fiction** spikes correlate with major franchise releases
- Books priced in the **$10–$14 range** tend to attract the highest review volumes, suggesting this is the consumer sweet spot on Amazon
- A small number of **recurring authors** (appearing 5+ times across years) account for a disproportionate share of total reviews — a classic Pareto pattern
- **User ratings are highly compressed** in this dataset (range: 3.3–4.9), meaning small differences in rating (e.g., 4.5 vs. 4.7) carry significant competitive meaning
- Total review volume grew steadily from **2009 to 2013**, then plateaued — potentially reflecting maturation of the Amazon review ecosystem

---

##  License

This project is released for educational and research purposes.
Dataset credit: [Souter Saalu on Kaggle](https://www.kaggle.com/datasets/sootersaalu/amazon-top-50-bestselling-books-2009-2019)

---
##  Note from Me :)
>This project was developed as part of an applied portfolio effort in data visualization and business intelligence, combining advanced DAX-driven analytics with interactive Power BI dashboard design techniques. The goal was to transform a real-world consumer dataset into actionable insights through structured visual storytelling. Contributions, suggestions, and feedback are welcome, feel free to explore!
