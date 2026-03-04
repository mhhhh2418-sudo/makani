# Database Schema Documentation for Makani Accounting System

## Entity Relationship Diagrams (ERD)
![ERD](path/to/your/erd-image.png) <!-- Path to your diagram -->

## Tables

### Users
- **user_id**: INT, PRIMARY KEY, AUTO_INCREMENT
- **username**: VARCHAR(50), UNIQUE, NOT NULL
- **password**: VARCHAR(255), NOT NULL
- **email**: VARCHAR(100), UNIQUE, NOT NULL
- **created_at**: DATETIME, DEFAULT CURRENT_TIMESTAMP

### Transactions
- **transaction_id**: INT, PRIMARY KEY, AUTO_INCREMENT
- **user_id**: INT, FOREIGN KEY REFERENCES Users(user_id)
- **amount**: DECIMAL(10, 2), NOT NULL
- **transaction_date**: DATETIME, NOT NULL

### Accounts
- **account_id**: INT, PRIMARY KEY, AUTO_INCREMENT
- **user_id**: INT, FOREIGN KEY REFERENCES Users(user_id)
- **account_name**: VARCHAR(100), NOT NULL
- **balance**: DECIMAL(10, 2), DEFAULT 0.00

## Indexes
- **Index on Transactions**: ON (user_id)
- **Index on Accounts**: ON (user_id)

## Relationships
- A user can have multiple transactions.
- A user can have multiple accounts.

## SQL Migration Scripts

```sql
CREATE TABLE Users (
    user_id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE Transactions (
    transaction_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT,
    amount DECIMAL(10, 2) NOT NULL,
    transaction_date DATETIME NOT NULL,
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
);

CREATE TABLE Accounts (
    account_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT,
    account_name VARCHAR(100) NOT NULL,
    balance DECIMAL(10, 2) DEFAULT 0.00,
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
);
```
