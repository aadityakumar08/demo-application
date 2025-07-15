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

## 🗂️ Folder Structure

```
realtime-dashboard/
├── pom.xml
├── src/
│   └── main/
│       ├── java/
│       │   └── com/example/realtimedashboard/
│       │       ├── controller/         # REST controllers (API endpoints)
│       │       ├── model/              # JPA entities (data models)
│       │       ├── repository/         # Spring Data JPA repositories
│       │       ├── security/           # JWT and security configuration
│       │       └── service/            # Business logic and user details service
│       └── resources/
│           └── application.properties  # Main configuration file
├── target/                             # Build output (ignored by git)
└── README.md
```

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