# Cashew - Expense Tracker App

**Cashew** is a comprehensive and secure expense tracker application designed to help you manage your finances effectively. Built with Spring Boot for a robust backend, Cashew focuses on user authentication, efficient data handling, and an intuitive user experience.

## Problem Statement

The **Auth Service** is responsible for authentication and authorization of incoming requests from the **Templatisation Service** and **API Gateway**.

## Functional Requirements

- **User Sign-up and Login**: Users should be able to register and login to the application.
- **Session Management**: Users should not be required to log in every time they open the app.
- **Encrypted Password Storage**: Passwords should be encrypted before being stored in the database.
- **Access and Refresh Tokens**: Both access tokens and refresh tokens should be allotted for session management.
- **Secure Token Transmission**: Tokens should be transmitted over HTTPS requests for security.
- **Fault Tolerance**: Events published to the **userService** should be recoverable and fault-tolerant.

## Non-Functional Requirements

- **Fast Authentication**: Authentication should be optimized to avoid delays, minimizing lag during app launch.
- **Efficient Database Design**: The database should be structured to avoid complex operations and ensure low response times (LRQ).

## Features

- **User Authentication**: Secure login and registration using JWT tokens to ensure privacy and data integrity.
- **Expense Management**: Track your expenses effortlessly. Add, update, delete, and categorize transactions, helping you stay on top of your finances.
- **Category-Based Tracking**: Organize expenses into categories to gain insights into your spending habits.
- **User-Friendly Endpoints**: RESTful API endpoints to interact with expenses, users, and authentication seamlessly.
- **Spring Boot Backend**: Built with Spring Boot for efficient backend management, ensuring speed, reliability, and scalability.
- **Detailed Expense Reports**: Generate detailed reports to analyze spending patterns.
- **Visual Insights**: Graphs and charts to help visualize spending trends over time.

## Technologies Used

- **Java & Spring Boot**: Provides a stable and scalable backend framework.
- **MySQL**: Used for persistent storage of user data and expenses.
- **JWT**: Ensures secure user sessions through token-based authentication.
- **Maven**: Dependency management to keep the project clean and organized.
- **Lombok**: Reduces boilerplate code with annotations for getters, setters, and constructors.
- **Spring Security**: Enhances application security for authentication and authorization.

## Security Components

- **SecurityConfig**: This class creates Beans for applying filters that incoming requests must go through before reaching the controllers. It defines the **AuthenticationProvider** and other related beans.
- **JWTFilter**: This filter is applied to all requests, except those explicitly bypassed in the **SecurityConfig** class, such as `/auth/v1/refreshToken`, `/auth/v1/signup`, and `/auth/v1/login`.
- **AuthController**: Contains endpoints such as `/auth/v1/signup`, `/auth/v1/login`, and `/ping` for user registration, login, and health checks.
- **JwtService**: Responsible for generating tokens, validating tokens, and using claims to extract user information, including username and expiration.
- **RefreshTokenService**: Handles the creation and validation of refresh tokens to ensure session continuity.
- **UserDetailsServiceImpl**: Manages user sign-up, loading, and fetching of user details. Extends **UserDetailsService** from the `org.springframework.security.core.userdetails` package.
- **AuthenticationManager**: Comes from Spring Boot's security package and handles user authentication based on username and password.

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Ankitkmm/Cashew.git


  Navigate to the project directory:

cd Cashew

Set up MySQL Database: Create a database named cashew_db.

Configure Application Properties: Update src/main/resources/application.properties with your MySQL credentials.

spring.datasource.url=jdbc:mysql://localhost:3306/cashew_db
spring.datasource.username=YOUR_MYSQL_USERNAME
spring.datasource.password=YOUR_MYSQL_PASSWORD

Build the project:

mvn clean install

Run the application:

mvn spring-boot:run

Usage

Signup & Login: Use /api/auth/signup and /api/auth/login endpoints for user registration and login.

Manage Expenses: Use endpoints like /api/expenses to add, update, and delete expenses.

Token-based Security: Access secure endpoints with JWT tokens obtained during login.

Categorize Expenses: Group expenses by categories like food, travel, and utilities to better manage your finances.

Visualize Spending: Access spending graphs to track trends over time.

API Endpoints Overview

Authentication

POST /api/auth/signup - Register a new user.

POST /api/auth/login - Login and get a JWT token.

Expense Management

GET /api/expenses - Retrieve all expenses for the logged-in user.

POST /api/expenses - Add a new expense.

PUT /api/expenses/{id} - Update an existing expense.

DELETE /api/expenses/{id} - Delete an expense.

GET /api/expenses/category/{category} - Retrieve expenses by category.

Project Structure

src/main/java: Contains the Java source files for controllers, services, entities, and security configurations.

controller: Defines RESTful APIs for user and expense management.

service: Implements the business logic for authentication and expense operations.

repository: Interfaces for data access with MySQL.

security: Configures JWT and Spring Security.

src/main/resources: Includes application configuration files.

pom.xml: Contains the project dependencies and plugin configurations.

Contributing

Feel free to submit pull requests to improve the project. Contributions are always welcome!

Diagrams

Sequence UML Diagram: <img width="1396" alt="Untitled" src="https://github.com/user-attachments/assets/6be74e2f-b756-4797-94ba-edd1836809f4">

ER Diagram: <img width="1230" alt="Untitled (1)" src="https://github.com/user-attachments/assets/302877f5-8000-434a-9c87-dba519c89165"
