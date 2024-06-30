# Database_MidTerm


## SQL Query for the Creation of __Customers__ Table
CREATE TABLE Customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    total_spent DECIMAL(10,2),
    created_at TIMESTAMP);    
## SQL Query for the Creation of __Authors__ Table
CREATE TABLE Authors (
    author_id INT PRIMARY KEY,
    name VARCHAR(100),
    biography TEXT);    
## SQL Query for the Creation of __Publishers__ Table
CREATE TABLE Publishers (
    publisher_id INT PRIMARY KEY,
    name VARCHAR(100),
    address VARCHAR(255));
## SQL Query for the Creation of __Books__ Table
CREATE TABLE Books (
    book_id INT PRIMARY KEY,
    title VARCHAR(255),
    genre VARCHAR(50),
    format VARCHAR(20),
    author_id INT,
    publisher_id INT,
    publish_date DATE,
    price DECIMAL(10,2),
    FOREIGN KEY (author_id) REFERENCES Authors(author_id),
    FOREIGN KEY (publisher_id) REFERENCES Publishers(publisher_id));
## SQL Query for the Creation of __Reviews__ Table
CREATE TABLE Reviews (
    review_id INT PRIMARY KEY,
    customer_id INT,
    book_id INT,
    rating INT,
    review_text TEXT,
    review_date TIMESTAMP,
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id),
    FOREIGN KEY (book_id) REFERENCES Books(book_id));
## SQL Query for the Creation of __Sales__ Table
CREATE TABLE Sales (
    sale_id INT PRIMARY KEY,
    customer_id INT,
    book_id INT,
    sale_date TIMESTAMP,
    amount DECIMAL(10,2),
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id),
    FOREIGN KEY (book_id) REFERENCES Books(book_id));

