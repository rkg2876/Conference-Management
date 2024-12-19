PHP Conference Management System
Overview
The PHP Conference Management System is a web application that enables users to:

View conference details and schedules.
Register for conferences.
Provide feedback for attended conferences.
Admins can:

Add, edit, and delete conferences.
View and manage user registrations.
Review feedback submitted by users.
Features
User Dashboard:

View available conferences.
Register for conferences.
Submit feedback for attended conferences.
Admin Dashboard:

Add, edit, and delete conferences.
Manage user registrations.
View feedback submitted by users.
Authentication:

Secure login for both users and admins.
Passwords stored using secure hashing.
Database Management:

Data is stored in a MySQL database.
Supports CRUD operations for conferences and feedback.
Error Handling:

Rollback transactions for critical operations.
Validation for form inputs to prevent invalid entries.
Technologies Used
Frontend: HTML, CSS (without Bootstrap).
Backend: PHP.
Database: MySQL.
Server: XAMPP or any LAMP/WAMP stack.
Setup Instructions
Install Required Software:

XAMPP (Recommended).
PHP version 7.4+.
MySQL database.
Download the Project:

Clone or download the project files into your local machine.
Database Setup:

Open phpMyAdmin (via XAMPP or other tool).
Create a database named conference_management.
Import the conference_management.sql file into this database.
Configure the Database:

Open db.php in the project folder.
Update the following lines with your database credentials:
php
Copy code
$servername = "localhost";
$username = "root";
$password = ""; // Leave blank if no password
$dbname = "conference_management";
Run the Application:

Start the Apache and MySQL services in XAMPP.
Place the project folder in the htdocs directory (e.g., C:\xampp\htdocs\conference_management).
Open your browser and navigate to: http://localhost/conference_management.
Default Admin Credentials
To log in as an admin, use the following credentials:

Username: admin
Password: admin123
Note: Passwords are stored using hashing. If the default admin login doesn't work, you can manually insert the admin user into the database using the following code in PHP or directly in SQL:

php
Copy code
$password = password_hash('admin123', PASSWORD_DEFAULT);
$sql = "INSERT INTO users (username, password, role) VALUES ('admin', '$password', 'admin')";
$conn->query($sql);
Folder Structure
graphql
Copy code
project/
│
├── db.php                   # Database connection file.
├── index.php                # Home/login page.
├── register.php             # User registration page.
├── user_dashboard.php       # User dashboard (conference registration, feedback).
├── admin_dashboard.php      # Admin dashboard (manage conferences).
├── add_conference.php       # Admin page to add a conference.
├── edit_conference.php      # Admin page to edit a conference.
├── feedback.php             # User feedback submission.
├── css/
│   └── style.css            # Custom styles for the application.
├── sql/
│   └── conference_management.sql # SQL file for database schema and sample data.
└── README.md                # Project documentation.
Database Schema
Users Table (users):

id (Primary Key, Auto Increment).
username (Unique).
password (Hashed password).
role (user or admin).
Conferences Table (conferences):

id (Primary Key, Auto Increment).
title (Conference title).
description (Conference description).
date (Date and time of the conference).
location (Location of the conference).
Registrations Table (registrations):

id (Primary Key, Auto Increment).
user_id (Foreign Key referencing users.id).
conference_id (Foreign Key referencing conferences.id).
Feedback Table (feedback):

id (Primary Key, Auto Increment).
user_id (Foreign Key referencing users.id).
conference_id (Foreign Key referencing conferences.id).
feedback_text (User feedback).
How to Use the System
As a User:
Login: Use your credentials or register a new account.
View Conferences: Browse the list of available conferences.
Register for Conferences: Click the "Register" button for the desired conference.
Submit Feedback: Go to the "Feedback" section and provide feedback for attended conferences.
As an Admin:
Login: Use the admin credentials.
Manage Conferences: Add, edit, or delete conference details.
View Registrations: See which users have registered for each conference.
Review Feedback: View user feedback for each conference.
Key Functionalities
Add/Edit/Delete Conferences:

Admins can manage conference details from the admin dashboard.
Register for Conferences:

Users can register for available conferences from their dashboard.
Registration is stored in the registrations table.
Submit Feedback:

Users can submit feedback for conferences they've attended.
Feedback is stored in the feedback table.
Error Handling:

Invalid input is validated on both the client-side (HTML forms) and server-side (PHP).
Transactions are used for critical operations like registration and feedback submission.
Testing the System
Default Admin Login: Test the admin functionality using the default credentials.
User Registration and Login: Create a new user account and test user-specific features.
Conference Management: Test adding, editing, and deleting conferences as an admin.
Feedback Submission: Test submitting and viewing feedback for conferences.
Known Issues
Ensure proper date format is used in the conference form (YYYY-MM-DD HH:MM).
Ensure that users cannot register for the same conference multiple times (handled in SQL).
This README should provide you with the necessary steps and details to run and test the application. Let me know if you need further clarification or enhancements!
