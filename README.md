# 🧮 Retail Sales Analysis  

A comprehensive **SQL-based retail sales analysis** exploring key performance metrics across **customer demographics, product categories, sales channels, and profitability**.  
This project demonstrates strong command of **SQL querying, data transformation, and Power BI visualization**, transforming raw retail data into **insightful business intelligence** that drives informed decision-making.  

---

## 📘 Overview  

The project focuses on end-to-end analytics; from **database creation** to **dashboard storytelling** uncovering performance insights that enhance **sales strategy, customer retention, and profit optimization**.  

### Core Objectives:
- ✅ Create and structure a relational **sales database**
- ✅ Import, clean, and transform raw transactional data
- ✅ Perform **exploratory and comparative data analysis**
- ✅ Visualize trends and KPIs in **Power BI**

The goal is to convert raw retail transactions into **business-ready insights** for improved decision-making, operational efficiency, and customer experience.  

---

## 📊 Dataset  

- **Source:** Axia SQL Project  
- **Key Fields:** Transaction ID, Sales Date & Time, COGS, Gender, Category, Quantity, Price per Unit, Total Sales  

---

## 🧰 Tools & Technologies  

- **SQL Server** – Database creation, data manipulation, and exploratory queries  
- **Power BI** – Visualization, DAX measures, and report design  
- **Excel / CSV** – Source data preparation and validation  

---

## 🔎 Analysis Workflow  

1. **Database Creation**  
   - Built the `RETAIL_SALES` database in SQL Server  
   - Structured relational schema for transaction data  

2. **Data Importation & Preparation**  
   - Imported flat-file data into SQL Server  
   - Removed null and inconsistent entries  
   - Validated data integrity and formatting  

3. **Data Transformation & Querying**  
   - Conducted descriptive, trend, and categorical analysis  
   - Queried metrics like **total sales**, **average age**, **purchase behavior**, and **sales by category**  

4. **Visualization in Power BI**  
   - Imported SQL query results into Power BI
   - Created calculated columns for month and year-based grouping  
   - Built reports for executive-level decision support  
   - Designed DAX-driven KPIs, monthly performance visuals, and category comparisons  

---

## 🧩SQL Queries 

```sql
 --1. Write a SQL query to retrieve all columns for sales made on '2022-11-05'
 SELECT*
 FROM [Retail Sales Analysis]
 WHERE sale_date = '2022-11-05';

 --2. Write a SQL query to retrieve all transactions where the category is 'Clothing' and the quantity sold is more than 4 in the month of Nov-2022 
 SELECT*
 FROM [Retail Sales Analysis]
 WHERE sale_date IN ('2022-11-01','2022-11-30')
 AND category ='Clothing' AND quantiy > 4;

 --3. Write a SQL query to calculate the total sales (total_sale) for each category
 SELECT DISTINCT category, SUM(total_sale) AS TotalSale
 FROM [Retail Sales Analysis]
 GROUP BY category
 ORDER BY TotalSale DESC;

 --4. Write a SQL query to find the average age of customers who purchased items from the 'Beauty' category
 SELECT AVG(age) AS Customers_Avg_Age
 FROM [Retail Sales Analysis]
 WHERE category = 'Beauty'

--5. Write a SQL query to find all transactions where the total_sale is greater than 1000
 SELECT*
 FROM [Retail Sales Analysis]
 WHERE total_sale > 1000

 --6. Write a SQL query to find the total number of transactions (transaction_id) made by each gender in each category
 SELECT category, gender, COUNT(transactions_id) AS total_transaction 
 FROM [Retail Sales Analysis]
 GROUP BY category, gender
 ORDER BY total_transaction DESC;

--7. Write a SQL query to calculate the average sale for each month. Find out best-selling month in each year .
 SELECT YEAR(sale_date) AS Sales_Year, MONTH(sale_date) AS Sales_Month, AVG(total_sale) AS Avg_monthly_sales
 FROM [Retail Sales Analysis]
 GROUP BY YEAR(sale_date), MONTH(sale_date)
 ORDER BY Sales_Year, Sales_Month, Avg_monthly_sales;

--8. Write a SQL query to find the top 5 customers based on the highest total sales.
 SELECT Top 5 customer_id,  SUM(total_sale) AS Highest_Sales
 FROM [Retail Sales Analysis]
 GROUP BY customer_id
 ORDER BY Highest_Sales DESC;

--9. Write a SQL query to find the number of unique customers who purchased items from each category.
 SELECT category, COUNT(DISTINCT customer_id) AS Customers
 FROM [Retail Sales Analysis]
 GROUP BY category
 ORDER BY Customers DESC;

--10. Write a SQL query to create each shift and number of orders (Example Morning <12, Afternoon Between 12 & 17, Evening >17) 
 SELECT CASE 
 WHEN DATEPART(HOUR, sale_time) < 12 THEN 'Morning'
 WHEN DATEPART(HOUR, sale_time) BETWEEN 12 AND 17 THEN 'Afternoon'
 ELSE 'Evening'
 END AS Shift,
 COUNT(*) AS Number_of_Orders
 FROM [Retail Sales Analysis]
 GROUP BY CASE 
 WHEN DATEPART(HOUR, sale_time) < 12 THEN 'Morning'
 WHEN DATEPART(HOUR, sale_time) BETWEEN 12 AND 17 THEN 'Afternoon'
 ELSE 'Evening'
 END;
```

👉 **[View Interactive Power BI Dashboard →]** (https://app.powerbi.com/view?r=eyJrIjoiYzdjZjM4OGYtNzlmOS00ODdkLWI1YjMtZmRiNGM4NzViNzRjIiwidCI6ImRkYjk1YzMwLWU3OWUtNDdiNy05YTVmLWE0MmNkZDljOTk5ZCJ9)  

---

## 💡 Key Insights  

- 💰 **₦908K Total Sales** generated across all categories  
- 🌆 **53.45%** of orders occurred in the evening  
- 👥 **Average customer age:** 41.35 years  
- 🧍‍♂️ **Top Customer:** ID 3 with ₦38K in purchases  
- 🖥️ **Electronics** sales outperform **Clothing** by 0.3% and **Beauty** by 8.4%  
- 📅 **2023 outperformed 2022** in total sales (₦459K vs ₦449K) and customer count (1,021 vs 966)

---

The dashboard provides:  
- Real-time tracking of **sales performance and customer engagement**  
- **Category-level profitability** and product contribution  
- **Time-series visualizations** for trend and seasonal analysis  
- **Interactive filters and KPIs** for dynamic insight exploration  

---

## 🧩 Insights Summary  

This analysis reveals a **healthy retail operation** with strong customer diversity and consistent sales growth. However, performance gaps exist across certain product lines and sales periods.  

**Highlights:**  
- Electronics dominate category revenue  
- Evening transactions represent over half of all sales  
- 2023 saw growth in both total sales and customer base but decline in average monthly sales. 

---

## 🎯 Recommendations  

1. **Category Optimization:**  
   - Increase marketing investment in high-performing categories (Electronics)  
   - Reevaluate underperforming product lines for pricing or promotion adjustments  

2. **Customer Retention:**  
   - Target repeat customers (especially high-value IDs) with loyalty programs  

3. **Time-based Strategy:**  
   - Extend promotions to align with evening purchase peaks  

4. **Advanced Forecasting:**  
   - Use SQL and Power BI time-intelligence DAX for future demand forecasting  

5. **Operational Efficiency:**  
   - Establish an automated data refresh schedule to keep Power BI insights real-time  

---

## 🧠 Key Learning & Impact  

This project demonstrates expertise in:
- Translating **business problems** into **SQL queries**  
- Designing **data pipelines** from raw import to interactive visualization  
- Communicating insights that directly influence **revenue and strategy decisions**  

It reflects a strong foundation in **data analytics, storytelling, and technical execution** essential for real-world BI and data roles.  

---

## 📬 Contact  

If you’re looking for a data-driven problem solver who can turn complex datasets into actionable stories, let’s connect:  

- **Name:** Opeyemi Ayodeji  
- **LinkedIn:** (https://www.linkedin.com/in/opeyemi-ayodeji-86a696b0/)  
- **Email:** sopeyemi65@gmail.com  

---

✨ *Transforming raw data into meaningful business intelligence; one query at a time.*  
