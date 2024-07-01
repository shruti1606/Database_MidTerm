# Database_MidTerm

## Roles of Group Members:
Name | Role
--- | :---
Shruti Patel | Database & Tables Creation
Pratham Parekh | CRUD Operations
Manish Koladiya | Requirements Execution
Vansh Palkhiwala | Typescript Interface
## SQL Query for the Creation of __Customers__ Table
CREATE TABLE Customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    total_spent DECIMAL(10,2),
    created_at TIMESTAMP);
## Customers Table Output 
No | Name | Type | Null | Default
--- | :--- | :--- | :---: | :---: 
1 | customer_id | int(11) | No | None
2 | name | varchar(100) | Yes | NULL
3 | email | varchar(100) | Yes | NULL
4 | total_spent | decimal(10,2) | Yes | NULL
5 | created_at | timestamp | No | current_timestamp()
## SQL Query for the Creation of __Authors__ Table
CREATE TABLE Authors (
    author_id INT PRIMARY KEY,
    name VARCHAR(100),
    biography TEXT);    
## Authors Table Output 
No | Name | Type | Null | Default
--- | :--- | :--- | :---: | :---: 
1 | author_id | int(11) | No | None
2 | name | varchar(100) | Yes | NULL
3 | biography | text | Yes | NULL
## SQL Query for the Creation of __Publishers__ Table
CREATE TABLE Publishers (
    publisher_id INT PRIMARY KEY,
    name VARCHAR(100),
    address VARCHAR(255));
## Publishers Table Output 
No | Name | Type | Null | Default
--- | :--- | :--- | :---: | :---: 
1 | publisher_id | int(11) | No | None
2 | name | varchar(100) | Yes | NULL
3 | address | varchar(255) | Yes | NULL
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
## Books Table Output 
No | Name | Type | Null | Default
--- | :--- | :--- | :---: | :---: 
1 | book_id | int(11) | No | None
2 | title | varchar(255) | Yes | NULL
3 | genre | varchar(50) | Yes | NULL
4 | format | varchar(20) | Yes | NULL
5 | author_id | int(11) | Yes | NULL
6 | publisher_id | int(11) | Yes | NULL
7 | publish_date | date | Yes | NULL
8 | price | decimal(10,2) | Yes | NULL
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
## Reviews Table Output 
No | Name | Type | Null | Default
--- | :--- | :--- | :---: | :---: 
1 | review_id | int(11) | No | None
2 | customer_id | int(11) | Yes | NULL
3 | book_id | int(11) | Yes | NULL
4 | rating | int(11) | Yes | NULL
5 | review_text | text | Yes | NULL
6 | review_date | timestamp | No | current_timestamp()
## SQL Query for the Creation of __Sales__ Table
CREATE TABLE Sales (
    sale_id INT PRIMARY KEY,
    customer_id INT,
    book_id INT,
    sale_date TIMESTAMP,
    amount DECIMAL(10,2),
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id),
    FOREIGN KEY (book_id) REFERENCES Books(book_id));
## Sales Table Output 
No | Name | Type | Null | Default
--- | :--- | :--- | :---: | :---: 
1 | sale_id | int(11) | No | None
2 | customer_id | int(11) | Yes | NULL
3 | book_id | int(11) | Yes | NULL
4 | sale_date | timestamp | No | current_timestamp()
5 | amount | decimal(10,2) | Yes | NULL
## CRUD Operations on the **Books** Table
## Insert Operation 
INSERT INTO Books (book_id, title, genre, format, author_id, publisher_id, publish_date, price) VALUES
(1, 'Rich Dad poor Dad', 'Personal Finance', 'Physical', 1, 1, '01-04-2000', 23.99),
(2, '1984', 'Dystopian', 'E-Book', 2, 2, '1949-06-08', 8.99);

INSERT INTO Books (book_id, title, genre, format, author_id, publisher_id, publish_date, price) VALUES
(3, 'To Kill a Mockingbird', 'Fiction', 'Audiobook', 3, 3, '1960-07-11', 12.99);

INSERT INTO Books (book_id, title, genre, format, author_id, publisher_id, publish_date, price) VALUES
(4, 'The Silent Patient', 'Thriller', 'Physical', 2, 1, '2019-02-05', 29.99);

INSERT INTO Books (book_id, title, genre, format, author_id, publisher_id, publish_date, price) VALUES
(5, 'Becoming', 'Biography', 'Physical', 3, 2, '2018-11-13', 32.50);

INSERT INTO Books (book_id, title, genre, format, author_id, publisher_id, publish_date, price) VALUES
(6, 'Educated', 'Memoir', 'Ebook', 4, 3,'2018-02-20', 28.00);

INSERT INTO Books (book_id, title, genre, format, author_id, publisher_id, publish_date, price) VALUES
(7, 'Where the Crawdads Sing', 'Mystery', 'Physical', 5, 4, '2018-08-14', 25.99);

INSERT INTO Books (book_id, title, genre, format, author_id, publisher_id, publish_date, price) VALUES
(8, 'Normal People', 'Romance', 'Physical', 6, 5, '2019-04-16', 27.99);
## Read Operation
SELECT * FROM Books WHERE book_id = 3;

SELECT * FROM Books WHERE author_id = 1;

SELECT * FROM Books WHERE genre = 'Biography';

SELECT * FROM Books WHERE price < 30.00;
## Update Operation
UPDATE Books SET price = 6.99 WHERE book_id = 2;
## Delete Operation
DELETE FROM Books WHERE book_id = 3;

## Power Writers
SELECT author_id, name
FROM Authors
WHERE TotalBooks > 3 AND BooksByGenre['fiction'] > 3 AND BooksLast5Years > 2001;

## Loyal Customers
SELECT customer_id, name
FROM Customers
WHERE TotalSpent > 30.00;

## Well Reviewed Books
SELECT book_id, title
FROM Books
WHERE Rating > (SELECT AVG(Rating) FROM Books);

## Most Popular Genre by Sales
SELECT Genre, SUM(Amount) AS TotalSales
FROM Books B
JOIN Sales ON Books.book_id = Sales.book_id
GROUP BY Genre
ORDER BY TotalSales DESC
LIMIT 1;


## TypeScript Interface for Modifying 'Books' Table
interface Book {
    book_id: number;
    title: string;
    genre: string;
    publish_date: Date;
    author_id: number;
    publisher_id: number;
    price: number;
    format: string;
}

## Create a new Node.js project to run the project: 
mkdir bookstore
cd bookstore
npm init -y
npm install express pg

## Creating Server file to connect with DB:

const express = require('express');
const { Pool } = require('pg');

const app = express();
const pool = new Pool({
    user: 'your_username',
    host: 'localhost',
    database: 'bookstore',
    password: 'your_password',
    port: 5432,
});

app.use(express.json());

app.get('/books', async (req, res) => {
    try {
        const result = await pool.query('SELECT * FROM books');
        res.json(result.rows);
    } catch (err) {
        res.status(500).json({ error: err.message });
    }
});

// More endpoints for CRUD operations

app.listen(3000, () => {
    console.log('Server is running on port 3000');
});
