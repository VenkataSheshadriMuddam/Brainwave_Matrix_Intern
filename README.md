# Brainwave_Matrix_Intern
# Java ATM Interface

A fully functional ATM interface built using Java and MySQL. This command-line application allows users to register, log in, and perform basic banking operations like deposit, withdrawal, fund transfer, checking balance, and viewing transaction history.

# Features
-  User Registration with validations
-  Secure Login with 4-digit PIN
-  Deposit & Withdraw
-  Transfer funds to other users
-  Check Account Balance
-  View detailed Transaction History
-  JDBC + MySQL-based data persistence

# Technologies Used
- Java (JDK 17 or above)
- JDBC (Java Database Connectivity)
- MySQL
- IntelliJ IDEA (for development, optional)

# Create the MySQL Database
Login to MySQL and run:

# Create databse
CREATE DATABASE ATMINTERFACE;

# Use database
USE ATMINTERFACE;

# USERS TABLE

CREATE TABLE users (
    user_id VARCHAR(50) PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    pin VARCHAR(10) NOT NULL,
    balance DECIMAL(10,2) DEFAULT 0.00
);

ALTER TABLE users ADD CONSTRAINT unique_name UNIQUE(name);

# TRANSACTIONS TABLE

CREATE TABLE transactions (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id VARCHAR(50),
    type VARCHAR(20),
    amount DECIMAL(10,2),
    recipient VARCHAR(100),
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);

SELECT 
    t.timestamp,
    t.type,
    t.amount,
    t.user_id AS sender_id,
    s.name AS sender_name,
    t.recipient AS recipient_id,
    r.name AS recipient_name
FROM 
    transactions t
LEFT JOIN 
    users r ON t.recipient = r.user_id   
LEFT JOIN 
    users s ON t.user_id = s.user_id    
ORDER BY 
    t.timestamp DESC;

# Output Screens

![Screenshot 2025-04-09 111348](https://github.com/user-attachments/assets/0f9c9204-d118-4b71-9ff4-b246e692c9c1)
![Screenshot 2025-04-09 111412](https://github.com/user-attachments/assets/5eeff636-156f-4008-b281-f4bc004adbb0)
![Screenshot 2025-04-09 111431](https://github.com/user-attachments/assets/322094d2-2d52-4f98-87ee-ce44f754d6e1)
![Screenshot 2025-04-09 111443](https://github.com/user-attachments/assets/b82da286-1fd4-48da-8003-cadf95de6682)




