# 🏦 Compte Client - Bank Account Management System

<div align="center">

![React](https://img.shields.io/badge/React-19.2.0-61DAFB?style=for-the-badge&logo=react&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5.7-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![H2 Database](https://img.shields.io/badge/H2-Database-4479A1?style=for-the-badge&logo=h2&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3.8-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white)

A modern full-stack web application for managing bank accounts (Comptes Bancaires) with a React frontend and Spring Boot REST API backend.

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Screenshots](#-screenshots)
- [Installation & Setup](#-installation--setup)
- [Project Structure](#-project-structure)
- [API Endpoints](#-api-endpoints)
- [Usage](#-usage)
- [Configuration](#-configuration)

---

## 🎯 Overview

**Compte Client** is a comprehensive bank account management application that allows users to:

- ✅ **Create** new bank accounts with balance, creation date, and account type
- 📊 **View** all accounts in a structured table format
- 🔄 **Update** existing account information
- 🗑️ **Delete** accounts from the system

The application follows a modern architecture with a **React** frontend communicating with a **Spring Boot REST API** backend, storing data in an **H2 in-memory database**.

---

## ✨ Features

### Frontend (React)
- 🎨 Modern, responsive UI with Bootstrap 5
- 📱 Mobile-friendly interface
- 🔄 Real-time data fetching and updates
- ✅ Form validation and error handling
- 🌐 CORS-enabled API communication

### Backend (Spring Boot)
- 🚀 RESTful API with JSON and XML support
- 💾 JPA/Hibernate ORM for database operations
- 🗄️ H2 in-memory database
- 🔒 CORS configuration for cross-origin requests
- 📝 Full CRUD operations

---

## 🛠️ Tech Stack

### Frontend
| Technology | Version | Purpose |
|------------|---------|---------|
| **React** | 19.2.0 | UI Framework |
| **Axios** | 1.13.1 | HTTP Client |
| **Bootstrap** | 5.3.8 | CSS Framework |
| **React Scripts** | 5.0.1 | Build Tools |

### Backend
| Technology | Version | Purpose |
|------------|---------|---------|
| **Spring Boot** | 3.5.7 | Backend Framework |
| **Spring Data JPA** | - | Database Operations |
| **H2 Database** | - | In-Memory Database |
| **Jackson** | - | JSON/XML Serialization |
| **Lombok** | - | Code Generation |

---

## 📸 Screenshots

### 1. Application Interface - Account List View

![Application Interface](Capture%20d'écran%20(951).png)

*The main application interface showing the account list with multiple accounts displayed in a table format.*

### 2. Success Notification - Account Added

![Success Notification](Capture%20d'écran%20(952).png)

*Confirmation popup displayed when a new account is successfully created, showing "Compte ajouté" (Account added) message.*

### 3. Database Console - H2 Database Management

![H2 Console](Capture%20d'écran%20(953).png)

*H2 Console interface displaying the database records, showing the stored account data with ID, balance, creation date, and account type.*

---

## 🚀 Installation & Setup

### Prerequisites

- **Node.js** (v14 or higher)
- **Java JDK** (v25 or compatible)
- **Maven** (v3.6 or higher)
- **npm** or **yarn**

### Backend Setup (Spring Boot)

1. **Navigate to the Spring Boot project:**
   ```bash
   cd spring
   ```

2. **Build the project:**
   ```bash
   mvn clean install
   ```

3. **Run the Spring Boot application:**
   ```bash
   mvn spring-boot:run
   ```

   The backend server will start on **http://localhost:8082**

4. **Access H2 Console:**
   - URL: `http://localhost:8082/h2-console`
   - JDBC URL: `jdbc:h2:mem:banque`
   - Username: `sa`
   - Password: (leave empty)

### Frontend Setup (React)

1. **Navigate to the React client:**
   ```bash
   cd compte-client
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start the development server:**
   ```bash
   npm start
   ```

   The application will open at **http://localhost:3000**

### Configuration

Make sure the API base URL in `src/config.js` matches your backend:

```javascript
const API_BASE_URL = "http://localhost:8082/banque";
```

---

## 📁 Project Structure

```
compte-client/
├── public/                 # Public assets
├── src/
│   ├── components/         # React components
│   │   ├── CompteForm.js   # Account creation form
│   │   └── CompteList.js   # Account list display
│   ├── config.js           # API configuration
│   ├── App.js              # Main app component
│   └── index.js            # Entry point
└── package.json            # Dependencies

spring/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── ma/rest/spring/
│   │   │       ├── controllers/    # REST controllers
│   │   │       ├── entities/      # JPA entities
│   │   │       └── repositories/   # Data repositories
│   │   └── resources/
│   │       └── application.properties  # Configuration
└── pom.xml                 # Maven dependencies
```

---

## 🔌 API Endpoints

The backend provides a RESTful API at base path `/banque`:

| Method | Endpoint | Description | Content-Type |
|--------|----------|-------------|--------------|
| `GET` | `/banque/comptes` | Get all accounts | JSON/XML |
| `GET` | `/banque/comptes/{id}` | Get account by ID | JSON/XML |
| `POST` | `/banque/comptes` | Create new account | JSON/XML |
| `PUT` | `/banque/comptes/{id}` | Update account | JSON/XML |
| `DELETE` | `/banque/comptes/{id}` | Delete account | - |

### Example API Request

**Create Account:**
```bash
POST http://localhost:8082/banque/comptes
Content-Type: application/json

{
  "solde": 300,
  "dateCreation": "2025-10-30",
  "type": "EPARGNE"
}
```

**Response:**
```json
{
  "id": 4,
  "solde": 300,
  "dateCreation": "2025-10-30",
  "type": "EPARGNE"
}
```

---

## 💻 Usage

### Adding a New Account

1. Fill in the form fields:
   - **Solde**: Enter the account balance (number)
   - **Date de Création**: Select the creation date
   - **Type**: Choose between:
     - `COURANT` (Current Account)
     - `EPARGNE` (Savings Account)

2. Click the **"Ajouter"** button

3. A success message will appear confirming the account creation

4. The account list will automatically refresh to show the new account

### Viewing Accounts

- All accounts are automatically displayed in the table below the form
- The table shows:
  - **ID**: Unique account identifier
  - **Solde**: Account balance
  - **Date de Création**: Account creation date
  - **Type**: Account type (COURANT or EPARGNE)

---

## ⚙️ Configuration

### Backend Configuration

**`spring/src/main/resources/application.properties`:**

```properties
spring.application.name=spring
spring.datasource.url=jdbc:h2:mem:banque
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
server.port=8082
spring.jpa.hibernate.ddl-auto=update
```

### Frontend Configuration

**`compte-client/src/config.js`:**

```javascript
const API_BASE_URL = "http://localhost:8082/banque";
export default API_BASE_URL;
```

### CORS Configuration

The backend includes CORS configuration to allow requests from the React frontend:

```java
@CrossOrigin(origins = "http://localhost:3000")
@RestController
@RequestMapping("/banque")
public class CompteController {
    // ...
}
```

---

## 🎓 Learning Resources

- [React Documentation](https://react.dev/)
- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [Bootstrap Documentation](https://getbootstrap.com/)
- [Axios Documentation](https://axios-http.com/)

---

## 📝 License

This project is part of an educational exercise (TP 9 : Client React pour API REST - Spring Boot).

---

## 👨‍💻 Author

Kazaz Mohammed
Developed as part of the Spring Boot REST API course.

---

<div align="center">

**Made with ❤️ using React and Spring Boot**

</div>
