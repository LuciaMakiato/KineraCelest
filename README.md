# KineraCelest
TuplokTuplok raman kaha

To run the tkinter-based application with MySQL integration and the updated design, follow these steps:

1. Set Up Your Environment
Ensure Python is installed on your machine (version 3.6 or later is recommended).
Install the required Python libraries:
bash
pip install mysql-connector-python werkzeug
2. Set Up Your MySQL Database
Open your MySQL client or use a GUI tool like phpMyAdmin or MySQL Workbench.

Create a database for the project:

SQL
CREATE DATABASE todo_app;
Create the necessary tables:

SQL
USE todo_app;

-- Admins table
CREATE TABLE admins (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(255) NOT NULL,
    password VARCHAR(255) NOT NULL
);

-- Users table
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(255) NOT NULL,
    password VARCHAR(255) NOT NULL
);

-- Tasks table
CREATE TABLE tasks (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    task TEXT NOT NULL,
    completed BOOLEAN DEFAULT FALSE,
    deadline DATE,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
Insert a test admin user:

SQL
INSERT INTO admins (username, password) VALUES ('admin', '<hashed_password>');
Replace <hashed_password> with a hashed password generated using generate_password_hash() in Python. For example:

Python
from werkzeug.security import generate_password_hash
print(generate_password_hash("admin123"))
3. Run the Application
Save the provided Python script to a file, e.g., todo_system.py.
Open a terminal or command prompt, navigate to the directory containing the file, and run:
bash
python todo_system.py
4. Login to the Application
Use the admin credentials (username: admin, password: admin123) to log in as an admin.
Add users, manage tasks, and explore the features.
5. Troubleshooting
MySQL Connection Issues: Ensure the database credentials (host, user, password) in the get_db_connection() function are correct.
Dependencies Missing: If any library is missing, use pip install <library-name> to install it.
Error During Execution: Share the error message, and I can help debug it.
Let me know if you need further guidance!
