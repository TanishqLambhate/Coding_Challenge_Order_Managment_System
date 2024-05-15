# Setup
 
 
## Virtual ENV
 
```bash
python -m venv myenv
```
 
## Activate
 
```sh
.\myenv\Scripts\Activate.ps1
```
## Create Schema
```sql
CREATE DATABASE Coding_Challenge

USE Coding_Challenge

CREATE TABLE Products
(
    productId INT PRIMARY KEY,
    productName NVARCHAR(255),
    description NVARCHAR(MAX),
    price FLOAT,
    quantityInStock INT,
    type NVARCHAR(50)
);


CREATE TABLE Users
(
    userId INT PRIMARY KEY,
    username NVARCHAR(255),
    password NVARCHAR(255),
    role NVARCHAR(50) CHECK (role IN ('Admin', 'User'))
);


CREATE TABLE [Order]
(
    OrderId INT IDENTITY(1,1) PRIMARY KEY,
    UserId INT,
    FOREIGN KEY (UserId) REFERENCES Users(UserId)
);



CREATE TABLE OrderProduct
(
    OrderId INT,
    ProductId INT,
    Quantity INT,
    PRIMARY KEY (OrderId, ProductId),
    FOREIGN KEY (OrderId) REFERENCES [Order](OrderId),
    FOREIGN KEY (ProductId) REFERENCES Products(ProductId)
);
```
## Start Project
```bash
python main.py
```