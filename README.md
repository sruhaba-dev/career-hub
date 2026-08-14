Career Hub — Personalized Internship Platform

Career Hub is a web-based internship management platform designed to connect students with employers. Students can build their professional profiles, manage skills, certifications and projects, take domain-based quizzes, browse internships and submit applications. Employers can create company profiles, publish internship opportunities and review/manage student applications.

Features

Student Portal

Student registration and login

Profile management

Skills management

Certification management

Project portfolio management

Resume and profile-picture URL support

Skill-based quizzes

Quiz score tracking

Internship browsing

Internship applications

Cover letter and contact information during application

Application status tracking

Notifications and recent activity

Internship eligibility based on quiz performance

Employer Portal

Employer/company registration and login

Company profile management

Create and publish internship postings

Define internship domain, duration, stipend and required skills

View and manage published internships

View incoming applications

Review applicant quiz scores

View student profiles, projects and certifications

Accept or reject applications

Track application statistics

Quiz Domains

The platform includes quizzes for:

Python

PHP

Java

DBS (Database Systems)

A score of 80% or above is used as the qualification threshold for internship applications.

Technology Stack

Layer

Technology

Frontend

HTML5, CSS3, JavaScript

Backend

PHP

Database

MySQL

Database Access

PHP PDO

Authentication

PHP Sessions

Password Security

password_hash() / password_verify()

UI

Custom responsive CSS

Fonts

Google Fonts

Project Structure

career_hub8_fixed/
│
├── index.html
├── database.sql
├── migrate_applications.sql
│
├── css/
│   └── style.css
│
├── js/
│   ├── app.js
│   ├── student-dashboard.js
│   └── employer-dashboard.js
│
├── php/
│   ├── db.php
│   ├── auth.php
│   ├── student-api.php
│   └── employer-api.php
│
├── student/
│   ├── login.html
│   ├── signup.html
│   └── dashboard.html
│
└── employer/
    ├── login.html
    ├── signup.html
    └── dashboard.html

The project archive also contains a nested career-hub-dbms-project/ copy of the application. For normal use, run the main career_hub8_fixed project folder.

Requirements

Before running the project, install:

XAMPP or another local PHP/MySQL server

PHP with PDO MySQL support

MySQL

A modern web browser such as Chrome, Edge or Firefox

Installation & Setup

1. Install XAMPP

Install XAMPP and make sure the following services are available:

Apache

MySQL

Start both services from the XAMPP Control Panel.

2. Copy the Project

Copy the career_hub8_fixed folder into:

C:\xampp\htdocs\

The final location should look like:

C:\xampp\htdocs\career_hub8_fixed\

3. Create the Database

Open:

http://localhost/phpmyadmin

Select the Import option and import:

database.sql

The SQL script creates the career_hub database and all required tables.

Alternatively, the SQL file can be executed through the MySQL command line.

4. Configure Database Connection

Open:

php/db.php

The default configuration is:

$host = 'localhost';
$db   = 'career_hub';
$user = 'root';
$pass = '';

If your MySQL installation uses a different username or password, update these values accordingly.

5. Run the Application

Open the application through Apache:

http://localhost/career_hub8_fixed/

Do not normally open the PHP-based project by double-clicking index.html, because the application requires PHP sessions and database APIs.

Database Design

The main database tables are:

students — student accounts and profile information

employers — employer/company accounts

skills — student skills

certifications — student certifications

projects — student projects

quiz_scores — quiz results by domain

internships — internship postings

applications — student applications and their statuses

Main Relationships

Student
  │
  ├── Skills
  ├── Certifications
  ├── Projects
  ├── Quiz Scores
  └── Applications
          │
          ▼
      Internship
          │
          ▼
      Employer

Students can have multiple skills, certifications, projects and applications. Employers can publish multiple internships, and each internship can receive multiple applications.

Authentication

The backend uses PHP sessions to maintain logged-in users.

Student sessions use:

student_id

Employer sessions use:

employer_id

Passwords are not stored as plain text. Registration uses PHP's password hashing functionality, while login verifies passwords using password_verify().

Application Flow

Student Flow

Student Registration
        ↓
Student Login
        ↓
Complete Profile
        ↓
Add Skills / Certifications / Projects
        ↓
Take Domain Quiz
        ↓
Meet Qualification Requirement
        ↓
Browse Internships
        ↓
Apply
        ↓
Track Application Status

Employer Flow

Employer Registration
        ↓
Employer Login
        ↓
Complete Company Profile
        ↓
Post Internship
        ↓
Receive Applications
        ↓
Review Student Profile & Quiz Score
        ↓
Accept / Reject Application

Quiz System

The application contains domain-specific multiple-choice questions.

Supported domains:

Python
PHP
Java
DBS

Quiz scores are stored in the quiz_scores table and associated with the student's account and selected domain.

The application uses an 80% qualification threshold for internship eligibility.

API Structure

The PHP backend is divided into separate API files:

php/student-api.php

Handles student-related operations such as:

Getting/updating profile

Getting/adding/deleting skills

Getting/adding/deleting certifications

Getting/adding/deleting projects

Quiz score operations

Internship browsing

Applications

Student activity and notifications

php/employer-api.php

Handles employer-related operations such as:

Getting/updating company profile

Creating internship postings

Listing employer postings

Deleting postings

Viewing applications

Reviewing student information

Updating application status

php/auth.php

Handles:

Student registration

Employer registration

Student login

Employer login

Logout

Session checking

php/db.php

Provides:

PDO database connection

Session initialization

JSON response helper

Authentication checks

Security Considerations

The project includes several basic security practices:

Password hashing using password_hash()

Password verification using password_verify()

Prepared SQL statements through PDO

Session-based authentication

Authentication checks for student and employer APIs

Ownership checks before modifying records

For a production deployment, additional protections should be added, including CSRF protection, stricter input validation, secure session-cookie settings, HTTPS, rate limiting and stronger authorization controls.

Troubleshooting

Database connection failed

Check:

MySQL is running.

The database is named career_hub.

The username/password in php/db.php are correct.

PDO MySQL support is enabled in PHP.

PHP code is not running

Make sure Apache is running and access the project through:

http://localhost/career_hub8_fixed/

instead of opening the HTML file directly.

Login does not work

Check:

The database was imported successfully.

The students and employers tables exist.

Apache and MySQL are running.

Browser cookies/sessions are enabled.

API returns an unauthorized error

The relevant student/employer session may not exist. Log in again through the appropriate portal.

Future Improvements

Possible future enhancements include:

Email notifications

Advanced internship recommendation using skill matching

Admin panel

Resume file uploads instead of URLs

Profile picture uploads

More quiz domains

Advanced search and filtering

Pagination for internships and applications

Employer verification

Password reset functionality

CSRF protection

Production deployment support

Project Purpose

Career Hub was developed as an academic web/DBMS project to demonstrate practical implementation of:

Web application development

Frontend and backend integration

PHP and MySQL database connectivity

CRUD operations

Authentication and sessions

Relational database design

Student and employer workflows

Quiz-based qualification

Internship application management

License

This project is intended for educational and academic use. If you reuse or extend the project, update this section according to your institution's or team's requirements.

Author

Career Hub Project

Developed as an academic Software Engineering / DBMS project.
