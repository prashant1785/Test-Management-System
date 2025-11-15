📘 Test Management System (Spring Boot + MySQL)

A Spring Boot–based Test Management System designed to manage users, tests, questions, and test logs.
It supports admin & user roles, test assignment, random question generation, answer submission, verification, and result generation.

🚀 Features
🔐 Authentication

Username-based login

Validates password

Returns login status, user ID, and role

Handles cases:

Wrong username

Multiple accounts

Wrong password

📝 Question Management

Add new questions

Get all available questions

Random selection of questions for each test attempt

🧪 Test Management

Add new tests

View all created tests

Fetch only active tests based on current timestamp

Generates result summary: Pass / Fail for each user

🗂️ Test Attempt (Logs)

Create logs automatically when user attempts a test

Assigns random questions based on test question count

Update answers

Submit the test

Accept/Reject answers (verification process)

Fetch logs waiting for verification

🏗️ Project Architecture
Controller: Mycontroller.java
Repositories:
  - UserRepo
  - TestRepo
  - QuestionRepo
  - LogRepo

Entities:
  - User
  - Test
  - Question
  - Log

📡 API Endpoints
🔐 Login
POST /login{username}

Request Body: password (string)
Returns: [loginStatus, userId, role]

📝 Questions
POST /addQuestion

Add a question.

GET /givenQuestions

Get all questions.

🧪 Tests
POST /addTest

Add a new test.

GET /giveTests

Get all tests with pass/fail results.

GET /giveActiveTests

Get active tests based on start and end date.

🗂️ Test Logs
GET /givenMeTestLogs/{userId}/and/{testid}

Generates log entries if attempting first time

Returns logs for that test

POST /update{id}

Update answer.

POST /submit{id}

Submit the test attempt.

POST /acceptreject{id}

Verify (accept/reject) a submitted answer.

GET /getAllLogsForVerification

Fetch all pending logs:

submit = 1

verify = 0

🔧 Technologies Used
Layer	Technology
Backend	Spring Boot
Database	MySQL
ORM	Spring Data JPA
Language	Java
Build Tool	Maven
Tools	Postman / VS Code / IntelliJ Idea
📅 Test Logic (Important Details)

When a user attempts a test:

The system checks if logs already exist.

If not, it assigns random questions using findRandomQuestion().

The number of assigned questions = test.questionCount.

Verification:

Admin can approve/reject each answer.

Verification status stored in verify.

Result Calculation:

For each user:

Verified answers >= passingCount → Pass

Otherwise → Fail

🏁 Running the Project (Local System)

Clone the repository:

git clone https://github.com/prashant1785/Test-Management-System.git


Configure MySQL:

create database test_management;


Update application.properties:

spring.datasource.url=jdbc:mysql://localhost:3306/test_management
spring.datasource.username=root
spring.datasource.password=yourpassword
spring.jpa.hibernate.ddl-auto=update


Run the Spring Boot application:

mvn spring-boot:run

📜 Author

Prashant Domkawale
Java Developer | Spring Boot | MySQL | Full-Stack Development
