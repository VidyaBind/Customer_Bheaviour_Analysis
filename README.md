# Customer Shopping Behavior Analysis

An end-to-end data analytics project that analyzes **3,900 retail transactions** to uncover spending patterns, customer segments, product preferences and subscription behavior, using **Python, MySQL and Power BI**.

**Business question:** Who are our customers, what do they buy, and where can the business grow revenue and improve retention?

---

## Key Findings

| # | Finding | Number |
|---|---------|--------|
| 1 | Male customers generate about 68% of revenue | $157,890 (Male) vs $75,191 (Female) |
| 2 | Most customers are already loyal; very few are new | 3,116 Loyal, 701 Returning, 83 New |
| 3 | Only about 27% of customers are subscribers | 1,053 subscribers vs 2,847 non-subscribers |
| 4 | Subscribers do **not** spend more per order | $59.49 (subscribers) vs $59.87 (non-subscribers) |
| 5 | Most repeat buyers (>5 purchases) are not subscribed | 958 subscribed vs 2,518 not subscribed |
| 6 | Express shipping orders are slightly larger than Standard | $60.48 vs $58.46 average |
| 7 | Several products are heavily discount-dependent | Hat 50%, Sneakers 49.66%, Coat 49.07% of purchases discounted |
| 8 | Highest-rated items | Gloves (3.86), Sandals (3.84), Boots (3.82) |

**Headline takeaway:** The business has a strong base of loyal customers but is converting very few of them into subscribers, and the subscription program has not yet increased spend per order.

---

## Dataset

| Attribute | Detail |
|-----------|--------|
| Source file | `customer_shopping_behavior.csv` |
| Rows / Columns | 3,900 / 18 |
| Missing values | 37 in `Review Rating` |
| Demographics | Age, Gender, Location, Subscription Status |
| Purchase details | Item, Category, Purchase Amount (USD), Season, Size, Color, Shipping Type |
| Behavior | Discount applied, Promo code used, Frequency of purchases, Previous purchases, Review rating |

---

## Tools & Technologies

- **Python** (Pandas): data loading, cleaning, EDA and feature engineering
- **MySQL**: business analysis with joins, subqueries, CTEs and window functions
- **Power BI**: interactive KPI dashboard
- **Jupyter Notebook**: analysis environment
- **Gamma**: stakeholder presentation

---

## Project Workflow

### 1. Exploratory Data Analysis (Python)
- Loaded the data with Pandas and inspected its structure using `df.info()` and `.describe()`.
- Summarized key statistics: average purchase of about **$59.76** and average review rating of about **3.75**.
- Identified the most frequent values in categorical columns.

### 2. Data Preparation & Feature Engineering
- **Missing data:** imputed `Review Rating` nulls using the median of each product category.
- **Standardization:** renamed columns to snake_case for consistency.
- **New features:** created `age_group` and `purchase_frequency_days`.
- **Consistency:** dropped `promo_code_used` after confirming it was redundant with `discount_applied`.
- **Integration:** loaded the cleaned DataFrame into MySQL for SQL analysis.

### 3. SQL Analysis (MySQL)
Ten business questions answered in [`Customer_behaviour_queries.sql`](Customer_behaviour_queries.sql):

| Q | Business question | SQL concepts |
|---|-------------------|--------------|
| 1 | Revenue by gender | `GROUP BY`, `SUM` |
| 2 | Discount users who spent above average | Subquery |
| 3 | Top 5 products by average rating | `AVG`, `ORDER BY`, `LIMIT` |
| 4 | Standard vs Express shipping spend | `GROUP BY`, `IN` |
| 5 | Subscribers vs non-subscribers: spend and revenue | Multiple aggregates |
| 6 | Top 5 products by discount rate | `CASE WHEN` |
| 7 | New / Returning / Loyal customer segmentation | CTE, `CASE` |
| 8 | Top 3 products within each category | CTE, `ROW_NUMBER() OVER (PARTITION BY ...)` |
| 9 | Are repeat buyers more likely to subscribe? | Filtering, aggregation |
| 10 | Revenue contribution by age group | `GROUP BY`, `ORDER BY` |

**Segmentation logic (Q7):** 1 previous purchase = New, 2 to 10 = Returning, more than 10 = Loyal.

**Top products by category (Q8):**
- Accessories: Jewelry, Sunglasses, Belt
- Clothing: Blouse, Pants, Shirt
- Footwear: Sandals, Shoes, Sneakers
- Outerwear: Jacket, Coat

### 4. Power BI Dashboard
An interactive dashboard with filters and age and category trends for stakeholders.

- **KPIs:** 3.9K customers, $59.76 average purchase, 3.75 average rating
- **Subscription mix:** 27% subscribed, 73% not subscribed

> Add dashboard screenshots to an `images/` folder and reference them here:
>
> `<img width="1234" height="667" alt="image" src="https://github.com/user-attachments/assets/12563ce0-677a-4f3c-87c0-1e741ea3925f" />

---

## Business Recommendations

1. **Boost subscriptions:** promote exclusive subscriber benefits, since only 27% of customers subscribe and subscribers currently spend no more than non-subscribers.
2. **Launch a loyalty program:** reward repeat buyers to protect and grow the Loyal segment, which is about 80% of customers.
3. **Review the discount policy:** discounted orders are not larger on average, so balance promotions against margin and target discount-dependent products such as Hat, Sneakers and Coat.
4. **Improve product positioning and targeting:** highlight top-rated and best-selling items, and focus marketing on high-revenue age groups and express-shipping users.

---


## How to Reproduce

1. Run the Jupyter notebook to clean the data and engineer features.
2. Load the cleaned data into a MySQL database named `customer_behaviour` (table: `customer`).
3. Run the queries in `Customer_behaviour_queries.sql`.
4. Open the `.pbix` file in Power BI Desktop to explore the dashboard.

---

## Skills Demonstrated

Python · Pandas · EDA · Data Cleaning · Feature Engineering · MySQL · CTEs · Window Functions · Power BI · Data Visualization · Customer Segmentation · Business Analysis · Data Storytelling

---
