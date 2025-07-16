# Realtime Dashboard

![Java](https://img.shields.io/badge/Java-17%2B-blue)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

A professional, full-featured Spring Boot application for managing personal productivity and analytics, including notes, tasks, metrics, reminders, and transactions. Built with security, extensibility, and modern best practices in mind.

---

## 🚀 Project Overview

The **Realtime Dashboard** is a backend REST API designed to help users track and manage:
- **Notes**
- **Tasks**
- **Metrics** (e.g., health, productivity)
- **Reminders** (with optional task linkage)
- **Transactions** (income/expense)

Authentication is handled via JWT, ensuring secure access to all protected endpoints.

---

## ✨ Features
- User registration and JWT-based authentication
- CRUD operations for notes, tasks, metrics, reminders, and transactions
- Relational data: link reminders to tasks
- PostgreSQL database integration
- Secure endpoints with Spring Security
- Professional code structure (controllers, services, repositories, models)
- Easy configuration via `application.properties`

---

## 🗂️ Detailed Folder Structure

```plaintext
realtime-dashboard/
├── pom.xml                          # Maven build configuration
├── README.md                        # Project documentation
├── CODE_OF_CONDUCT.md               # Code of conduct for contributors
├── CONTRIBUTING.md                  # Contribution guidelines
├── src/
│   └── main/
│       ├── java/
│       │   └── com/
│       │       └── example/
│       │           └── realtimedashboard/
│       │               ├── RealtimeDashboardApplication.java   # Main Spring Boot application entry point
│       │               ├── controller/                        # REST API controllers
│       │               │   ├── AuthController.java            # Authentication endpoints (login, signup)
│       │               │   ├── DashboardController.java       # Dashboard summary endpoints
│       │               │   ├── MetricController.java          # Metrics CRUD endpoints
│       │               │   ├── NoteController.java            # Notes CRUD endpoints
│       │               │   ├── ReminderController.java        # Reminders CRUD endpoints
│       │               │   ├── TaskController.java            # Tasks CRUD endpoints
│       │               │   └── TransactionController.java     # Transactions CRUD endpoints
│       │               ├── model/                             # JPA entity models
│       │               │   ├── Metric.java
│       │               │   ├── Note.java
│       │               │   ├── Reminder.java
│       │               │   ├── Task.java
│       │               │   ├── Transaction.java
│       │               │   └── User.java
│       │               ├── repository/                        # Spring Data JPA repositories
│       │               │   ├── MetricRepository.java
│       │               │   ├── NoteRepository.java
│       │               │   ├── ReminderRepository.java
│       │               │   ├── TaskRepository.java
│       │               │   ├── TransactionRepository.java
│       │               │   └── UserRepository.java
│       │               ├── security/                          # Security and JWT configuration
│       │               │   ├── JwtFilter.java                 # JWT authentication filter
│       │               │   ├── JwtUtil.java                   # JWT utility methods
│       │               │   └── SecurityConfig.java            # Spring Security configuration
│       │               └── service/                           # Business logic and user details service
│       │                   └── CustomerUserDetailsService.java
│       └── resources/
│           └── application.properties    # Main application configuration (DB, JWT, etc.)
└── target/                               # Compiled output and build artifacts (ignored by git)
```

### Directory/Component Descriptions

- **controller/**: Contains REST controllers that define API endpoints for each resource (notes, tasks, metrics, reminders, transactions, authentication, dashboard).
- **model/**: JPA entity classes representing the database tables.
- **repository/**: Spring Data JPA repositories for database CRUD operations.
- **security/**: All security-related code, including JWT utilities, filters, and Spring Security configuration.
- **service/**: Business logic and user details service for authentication.
- **resources/**: Application configuration files (e.g., database connection, JWT secret).
- **target/**: Maven build output (should be ignored in version control).

---

## 🛠️ Tech Stack
- **Java 17+**
- **Spring Boot**
- **Spring Security (JWT)**
- **Spring Data JPA**
- **PostgreSQL**
- **Maven**

---

## ⚡ Getting Started

### 1. Prerequisites
- Java 17 or higher
- Maven
- PostgreSQL (running and accessible)
- Git

### 2. Clone the Repository
```sh
git clone https://github.com/aadityakumar08/demo-application.git
cd demo-application
```

### 3. Configure the Database
Edit `src/main/resources/application.properties` with your PostgreSQL credentials:
```
spring.datasource.url=jdbc:postgresql://localhost:5432/dashboard_db
spring.datasource.username=postgres
spring.datasource.password=your_password
```

### 4. Build and Run
```sh
mvn clean install
mvn spring-boot:run
```

The app will start on `http://localhost:8080`.

---

## 🔐 Authentication
- Register via `/signup` (POST)
- Login via `/api/login` (POST) to receive a JWT token
- Use the JWT token in the `Authorization: Bearer <token>` header for all protected endpoints

---

## 🧩 Environment Variables

| Variable                      | Description                        | Example Value                  |
|-------------------------------|------------------------------------|-------------------------------|
| `spring.datasource.url`       | PostgreSQL JDBC URL                | jdbc:postgresql://localhost:5432/dashboard_db |
| `spring.datasource.username`  | Database username                  | postgres                      |
| `spring.datasource.password`  | Database password                  | your_password                 |
| `jwt.secret`                  | Secret key for JWT signing         | my-very-secret-key            |
| `jwt.expirationMs`            | JWT expiration in milliseconds     | 86400000                      |

---

## 📚 API Documentation (Sample)

### Register
```
POST /signup
Content-Type: application/json
{
  "username": "testuser",
  "email": "testuser@example.com",
  "password": "testpass"
}
```
**Response:**
```
201 Created
{
  "message": "User registered successfully!"
}
```

### Login
```
POST /api/login
Content-Type: application/json
{
  "username": "testuser",
  "password": "testpass"
}
```
**Response:**
```
200 OK
{
  "token": "<jwt-token>"
}
```

### Get Notes (Protected)
```
GET /api/notes
Authorization: Bearer <jwt-token>
```
**Response:**
```
200 OK
[
  {
    "id": 1,
    "title": "My First Note",
    "content": "This is a test note.",
    "createdAt": "2024-07-15T12:00:00"
  }
]
```

---

## 📚 API Endpoints (Sample)

| Resource      | Endpoint                        | Method | Description                |
|---------------|---------------------------------|--------|----------------------------|
| Auth          | `/signup`, `/api/login`         | POST   | Register / Login           |
| Dashboard     | `/api/dashboard/overview`       | GET    | Get dashboard summary      |
| Notes         | `/api/notes`                    | GET/POST/PUT/DELETE | Manage notes |
| Tasks         | `/api/tasks`                    | GET/POST/PUT/DELETE | Manage tasks |
| Metrics       | `/api/metrics`                  | GET/POST/PUT/DELETE | Manage metrics |
| Reminders     | `/api/reminders`                | GET/POST/PUT/DELETE | Manage reminders |
| Transactions  | `/api/transactions`             | GET/POST/PUT/DELETE | Manage transactions |

---

## 🧑‍💻 Contribution

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/YourFeature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/YourFeature`)
5. Open a Pull Request

See [`CONTRIBUTING.md`](CONTRIBUTING.md) for more details.

---

## 🤝 Code of Conduct

Please read and follow our [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md) to foster an open and welcoming community.

---

## ❓ Troubleshooting
- **Database connection errors:** Ensure PostgreSQL is running and credentials in `application.properties` are correct.
- **Port conflicts:** Make sure port 8080 is free or change it in `application.properties`.
- **JWT errors:** Double-check the `jwt.secret` value in your properties file.

---

## ❓ FAQ

**Q: How do I reset my password?**
A: Password reset is not implemented in this demo. You can add this feature in the future.

**Q: Can I use a different database?**
A: Yes, update the datasource properties in `application.properties` for your preferred database.

**Q: How do I add more fields to a model?**
A: Update the corresponding entity in `src/main/java/com/example/realtimedashboard/model/` and run migrations if needed.

---

## 📄 License

This project is licensed under the MIT License.

---

## 🙏 Acknowledgements
- Spring Boot & Spring Security teams
- PostgreSQL community
- [Your Name or Organization]

---

## 📬 Contact
For questions, suggestions, or support, please open an issue or contact [aadityakumar08](https://github.com/aadityakumar08). 