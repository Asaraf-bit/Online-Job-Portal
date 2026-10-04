# JobPortal Management 🚀

[![Java](https://img.shields.io/badge/Java-17%2B-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.3.4-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![Spring Security](https://img.shields.io/badge/Spring%20Security-6.x-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white)](https://spring.io/projects/spring-security)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](LICENSE)

An enterprise-ready, role-based Job Portal Platform built with **Spring Boot 3**, **Spring Security 6**, **Thymeleaf**, and **Bootstrap 5**, connecting students, companies, and administrators in a streamlined hiring lifecycle.

---

## 🌟 Key Features

### 🎓 For Students
- **Smart Recommendations:** AI-inspired skill-matching algorithm comparing student profile skills against job requirements with match percentages.
- **Advanced Job Search:** Filter opportunities by keywords, location, employment type (Full-time, Internship, Contract), and minimum salary.
- **Application Lifecycle Tracking:** Monitor status across `APPLIED`, `UNDER_REVIEW`, `SHORTLISTED`, `INTERVIEW`, `SELECTED`, `OFFER_ACCEPTED`, and `REJECTED`.
- **Resume Management:** Upload, preview, and replace PDF/Word resumes with local or cloud storage support.
- **Saved / Favorite Jobs:** Bookmark positions to review and apply later.
- **Interview Hub:** View scheduled interview dates, times, formats, and virtual meeting links.
- **Company Reviews:** Submit ratings and reviews for organizations worked with or interviewed at.
- **In-App Notifications:** Real-time notifications for application progress and interview schedules.

### 🏢 For Companies
- **Job Management:** Post, edit, close, and reactivate listings with rich skill requirements and compensation details.
- **Candidate Pipeline:** Review applicant profiles, download candidate resumes, and update application stages.
- **Interview Scheduling:** Schedule interviews directly with candidate email and meeting link dispatch.
- **Recruitment Analytics:** Dashboard metrics on job reach, application volume, shortlists, and candidate conversion rates.
- **Reputation Management:** View and monitor student feedback and platform ratings.

### 🛡️ For Administrators
- **Executive Dashboard:** Live metrics on platform-wide students, companies, job listings, and active applications.
- **Job Moderation:** One-click toggling of job statuses across the entire platform.
- **User Oversight:** Directory of registered student candidates and employer accounts.

### 🔌 Developer & API Features
- **Public REST API:** JSON endpoints for integration (`/api/jobs`, `/api/jobs/{id}`) with CORS support.
- **Automated Database Migrations:** Versioned schema management and sample data seeding via **Flyway**.
- **Observability:** Production-grade health checks and application metrics via **Spring Boot Actuator** (`/actuator/health`).
- **Comprehensive Test Suite:** 100+ unit and integration tests covering security, controllers, repositories, and services.

---

## 👥 Demo Accounts

The platform automatically migrates and seeds demo accounts on startup:

| Role | Email | Password | Access |
| :--- | :--- | :--- | :--- |
| **Student** | `aditi.rao@example.com` | `password123` | Student Dashboard & Job Search |
| **Company** | `hr@technova.com` | `password123` | Recruiter Dashboard & Job Posting |
| **Admin** | `admin@jobportal.local` | `admin123` | Admin Dashboard & Moderation |

---

## 🛠️ Technology Stack

- **Backend:** Java 17, Spring Boot 3.3.4
- **Security:** Spring Security 6 (BCrypt hashing, role-based authorization, CSRF protection, brute-force login protection)
- **Persistence:** Spring Data JPA, Hibernate 6, Flyway Migrations
- **Databases:**
  - **H2 In-Memory Database** (Default zero-config profile for instant local run)
  - **MySQL 8.x** (Production profile)
- **Frontend / UI:** Thymeleaf, Bootstrap 5.3, Bootstrap Icons, Plus Jakarta Sans typography
- **Testing:** JUnit 5, Mockito, Spring Security Test, Spring Boot Test (100+ tests)
- **Build Tool:** Maven 3.9+

---

## 🚀 Getting Started

### Prerequisites
- **JDK 17** or newer
- **Maven 3.9** or newer (or use included Maven wrapper if configured)

### 1. Clone the Repository
```bash
git clone https://github.com/faheed001/JobPortal-Management.git
cd JobPortal-Management
```

### 2. Run with H2 In-Memory Database (Zero-Config)
No database installation needed! Run:
```bash
mvn spring-boot:run
```
Once started, access the application at:
👉 **[http://localhost:8080](http://localhost:8080)**

- **H2 Console:** `http://localhost:8080/h2-console` *(JDBC URL: `jdbc:h2:mem:jobportal`)*
- **Actuator Health:** `http://localhost:8080/actuator/health`

### 3. Run with MySQL (Production Profile)
To use MySQL instead of H2:
1. Create a MySQL database and update `src/main/resources/application-mysql.properties` with your credentials.
2. Run with the `mysql` profile active:
```bash
mvn spring-boot:run -Dspring-boot.run.profiles=mysql
```

### 4. Run with Docker Compose
```bash
docker-compose up --build
```

---

## 🧪 Running Tests

To run the complete test suite:
```bash
mvn test
```

---

## 📡 REST API Reference

| Method | Endpoint | Description | Auth Required |
| :--- | :--- | :--- | :--- |
| `GET` | `/api/jobs` | Get all active jobs (optional search parameters: `title`, `location`) | No |
| `GET` | `/api/jobs/{id}` | Get detailed JSON information for a specific job | No |
| `GET` | `/actuator/health` | Application health and status check | No |

---

## 🔒 Security Highlights

- **BCrypt Password Hashing:** Automatically hashes passwords with adaptive work factor.
- **CSRF Tokens:** Embedded on all mutating state forms.
- **Brute Force Defense:** Failed login attempt throttling.
- **Role Isolation:** Strict endpoint boundaries enforced via method and URL security rules.
- **Open Session in View (OSIV) + EntityGraphs:** Optimized query execution preventing N+1 queries and lazy initialization exceptions.

---

## 📄 License

This project is open-source and licensed under the [MIT License](LICENSE).
