# 📊 Sales Insights Data Analysis Project

A hands-on data analysis project focused on extracting meaningful sales insights using **MySQL** and **Power BI**.
<img width="1536" height="1024" alt="AIMS_GRID" src="https://github.com/user-attachments/assets/858f4456-19b6-460e-99f4-325d8359121b" />

---

## 🛠️ Instructions to Setup MySQL on Your Local Computer

1. Follow the steps in this video to install MySQL on your local computer:  
   ▶️ https://www.youtube.com/watch?v=WuBcTJnIuzo

2. The SQL database dump is available in the **`db_dump.sql`** file above.  
   - Download the `db_dump.sql` file to your local computer  
   - Import it by following the instructions given in the tutorial video

---

## 🧮 Data Analysis Using SQL

1. Show all customer records

    `SELECT * FROM customers;`

1. Show total number of customers

    `SELECT count(*) FROM customers;`

1. Show transactions for Chennai market (market code for chennai is Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

1. Show distrinct product codes that were sold in chennai

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

1. Show transactions where currency is US dollars

    `SELECT * from transactions where currency="USD"`

1. Show transactions in 2020 join by date table

    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

1. Show total revenue in year 2020,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
1. Show total revenue in year 2020, January Month,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

1. Show total revenue in year 2020 in Chennai

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`


Data Analysis Using Power BI
============================

1. Formula to create norm_amount column

`= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)` 
