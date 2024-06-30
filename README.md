# Database_MidTerm


## SQL Query for Creation of Customers Table
CREATE TABLE Customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    total_spent DECIMAL(10,2),
    created_at TIMESTAMP);
