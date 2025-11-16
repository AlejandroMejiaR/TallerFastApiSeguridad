# Grade Management System

A secure full-stack web application for academic grade management, developed as a final project for an Information Security course.

The application is deployed on AWS and can be accessed live at: **[https://mis-calificaciones-app.duckdns.org](https://mis-calificaciones-app.duckdns.org)**

---

## Application Views

Below are the main views of the application.

**Login Page**
![Login Page](Images/1.png)
_Authentication form for system access._

---

**Professor's Dashboard**
![Professor's View](Images/2.png)
_The professor's dashboard, which includes the form to add/update grades and the list of grades they have created._

---

**Student's Dashboard**
![Student's View](Images/3.png)
_The student's dashboard, displaying only the grades associated with their profile, with no access to editing functionalities._

---

## Architecture and Tech Stack

This project is built with a modern, decoupled, and containerized architecture, focusing on security and DevOps best practices.

- **Frontend:** Next.js (React)
- **Backend:** Python with FastAPI
- **Database:** AWS RDS (MySQL)
- **Containerization:** Docker and Docker Compose
- **Infrastructure:** AWS EC2
- **Reverse Proxy & SSL:** Nginx with Certbot (Let's Encrypt)

---

## Implemented Security Features

- **Secure Authentication:** Password hashing with `bcrypt` and session management using **JWTs (JSON Web Tokens)**.
- **Role-Based Authorization (RBAC):** Differentiated access for "professor" and "student" roles.
- **Server Hardening:** Nginx configuration with HTTP security headers (CSP, X-Frame-Options, etc.) to mitigate common attacks like XSS and Clickjacking.
- **Encrypted Communication:** All traffic is protected with **HTTPS**.
- **Component Isolation:** A dockerized architecture and an external database on AWS RDS to minimize the attack surface.
- **Secrets Management:** All sensitive credentials are managed through environment variables.

---

## How to Run the Project Locally

This project is fully containerized, making it very simple to run locally.

**Prerequisites:**

- Docker and Docker Compose installed.

**Steps:**

1.  Clone the repository:
    ```bash
    git clone [Your-Repo-URL]
    ```
2.  Navigate to the project root:
    ```bash
    cd TallerFastApiSeguridad
    ```
3.  Create a `.env` file with your local environment variables (you can use `.env.example` as a template if you created one).
4.  Build and run the containers:
    ```bash
    docker-compose up -d --build
    ```
5.  Access the application at `http://localhost`.
