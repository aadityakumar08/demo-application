# Realtime Dashboard

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

## 🛠️ Tech Stack
- **Java 17+**
- **Spring Boot**
- **Spring Security (JWT)**
- **Spring Data JPA**
- **PostgreSQL**
- **Maven**

---

## ⚡ Getting Started

### 1. Clone the Repository
```sh
git clone https://github.com/aadityakumar08/demo-application.git
cd demo-application
```

### 2. Configure the Database
Edit `src/main/resources/application.properties` with your PostgreSQL credentials:
```
spring.datasource.url=jdbc:postgresql://localhost:5432/dashboard_db
spring.datasource.username=postgres
spring.datasource.password=your_password
```

### 3. Build and Run
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

---

## 📄 License

This project is licensed under the MIT License.

---

## 🙏 Acknowledgements
- Spring Boot & Spring Security teams
- PostgreSQL community
- [Your Name or Organization] 