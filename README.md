# Database_MidTerm

## Roles of Group Members:
Name | Role
--- | :---: 
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
