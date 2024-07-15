# Bank_management_java
### Bank Management System - Java Project

#### Description

This project is a Bank Management System developed in Java, using Swing for the graphical user interface and MySQL for the database. The application allows users to perform various banking operations such as account creation, deposit, withdrawal, and balance inquiry. It provides a simple yet comprehensive interface for managing bank accounts and transactions.

#### Features

1. **User Authentication**: Secure login and signup system for users.
2. **Account Management**: Create, update, and delete accounts.
3. **Transaction Management**: Perform deposit, withdrawal, and transfer transactions.
4. **Balance Inquiry**: Check account balances.
5. **Transaction History**: View the history of all transactions made.

#### Technologies Used

- **Java**: The core programming language used for developing the application.
- **Swing**: Used for creating the graphical user interface.
- **MySQL**: Database used for storing user and transaction data.
- **JDBC**: Java Database Connectivity API used for connecting and executing queries on the MySQL database.

#### Setup and Installation

1. **Prerequisites**:
   - JDK (Java Development Kit) - Latest version
   - MySQL Server
   - IDE (Integrated Development Environment) like IntelliJ IDEA, Eclipse, or NetBeans

2. **Database Setup**:
   - Install MySQL and create a database named `bank_management`.
   - Execute the following SQL script to create the necessary tables:

     ```sql
     CREATE DATABASE bank_management;

     USE bank_management;

     CREATE TABLE users (
         id INT AUTO_INCREMENT PRIMARY KEY,
         username VARCHAR(50) NOT NULL UNIQUE,
         password VARCHAR(50) NOT NULL,
         fullname VARCHAR(100),
         email VARCHAR(100),
         role ENUM('USER', 'ADMIN') DEFAULT 'USER'
     );

     CREATE TABLE accounts (
         id INT AUTO_INCREMENT PRIMARY KEY,
         user_id INT,
         account_number VARCHAR(20) UNIQUE,
         balance DECIMAL(15, 2) DEFAULT 0.00,
         FOREIGN KEY (user_id) REFERENCES users(id)
     );

     CREATE TABLE transactions (
         id INT AUTO_INCREMENT PRIMARY KEY,
         account_id INT,
         type ENUM('DEPOSIT', 'WITHDRAWAL', 'TRANSFER'),
         amount DECIMAL(15, 2),
         transaction_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
         FOREIGN KEY (account_id) REFERENCES accounts(id)
     );
     ```

3. **Project Setup**:
   - Clone the repository to your local machine.
   - Open the project in your IDE.
   - Add the MySQL JDBC driver to your project's classpath.
   - Configure the database connection settings in the `DBConnection` class:

     ```java
     public class DBConnection {
         private static final String URL = "jdbc:mysql://localhost:3306/bank_management";
         private static final String USER = "root"; // replace with your MySQL username
         private static final String PASSWORD = "password"; // replace with your MySQL password

         public static Connection getConnection() throws SQLException {
             return DriverManager.getConnection(URL, USER, PASSWORD);
         }
     }
     ```

4. **Running the Application**:
   - Run the `Login` class to start the application.
   - Use the application interface to register, login, and manage bank accounts and transactions.

#### JDK Used

- **JDK Version**: OpenJDK 17 (Latest LTS version as of the latest update)

#### Future Enhancements

- Adding more robust security measures for user authentication.
- Implementing additional features such as loan management, interest calculation, and more detailed reports.
- Enhancing the user interface for a better user experience.

#### Contributions

Contributions are welcome! Feel free to fork the repository and submit pull requests.

#### Contact

For any questions or suggestions, please contact Srivamsi Magapu at srivamsimagapu@gmail.com or connect on [LinkedIn](https://www.linkedin.com/in/srivamsimagapu/).

---

This readme file provides an overview of the Bank Management System project, detailing the features, setup instructions, and future enhancements. It aims to give a clear understanding of how to set up and run the project, as well as provide a starting point for further development.
