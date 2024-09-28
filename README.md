- 👋 Hi, I’m @Kacouake
- 👀 I’m interested in landing career in Data Analysis
- 🌱 I’m currently learning SQL
- 💞️ I’m looking to collaborate on SQL projects and learn from others on this platform
- 📫 How to reach me on here 
- 😄 Pronouns: He/Him
- ⚡ Fun fact: I am a midfielder on the soccer pitch!

<!---
Kacouake/Kacouake is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
# Sales Database Project

This project provides a sample SQL schema for a simple sales system. The system includes three main tables: `Customers`, `Products`, and `Sales`. It stores customer information, product inventory, and sales records, along with several query examples for retrieving sales-related statistics.

## Database Structure

### Tables

1. **Customers**
   - Stores information about customers, including their ID, name, age, and location.
   - `customer_id` is the primary key.

2. **Products**
   - Contains details about products such as product ID, name, category, and price.
   - `product_id` is the primary key.

3. **Sales**
   - Records all sales transactions, linking customers and products with information on quantity, sales date, and total price.
   - `sales_id` is the primary key.
   - Foreign keys reference the `customer_id` and `product_id` from the `Customers` and `Products` tables.

## Sample Data

The script includes insert statements for:
- **10 Customers** across various locations.
- **9 Products** spanning multiple categories like Electronics, Appliances, and Furniture.
- **25 Sales Transactions**, each associated with a customer and a product.

## SQL Queries

Several sample queries are provided to demonstrate how to retrieve information from the database:

1. **Total number of customers:**
  
   SELECT COUNT(*) AS total_customers FROM Customers;
   
2. **Top 5 customers by total sales**

SELECT c.name, SUM(s.total_price) AS total_sales
FROM Sales s
JOIN Customers c ON s.customer_id = c.customer_id
GROUP BY c.name
ORDER BY total_sales DESC
LIMIT 5;

3. **Most popular products by quantity sold**

SELECT p.name, SUM(s.quantity) AS total_sold
FROM Sales s
JOIN Products p ON s.product_id = p.product_id
GROUP BY p.name
ORDER BY total_sold DESC;

4. **Monthly sales totals**

SELECT MONTH(sales_date) AS month, SUM(total_price) AS total_sales
FROM Sales
GROUP BY month;


