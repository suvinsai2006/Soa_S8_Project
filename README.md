# Scholar360 – Digital Scholarship Management Platform

[![Course](https://img.shields.io/badge/Course-24SDCS03%20SOA%20%26%20Microservices-blue)](https://)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2.5-brightgreen)](https://spring.io/projects/spring-boot)
[![Spring Cloud](https://img.shields.io/badge/Spring%20Cloud-2023.0.1-green)](https://spring.io/projects/spring-cloud)
[![React](https://img.shields.io/badge/React.js-18.3-61dafb)](https://react.dev)
[![Status](https://img.shields.io/badge/Review--2-Fully%20Implemented-success)](https://)

> **Course:** SOA PROGRAMMING AND MICROSERVICES (24SDCS03) — A.Y. 2026 - 2027  
> **Platform:** Scholar360 Digital Scholarship Management Platform  

---

## 1. Technology Stack

- **Backend:** Java 21, Java Spring Boot 3.2.5
- **Distributed Architecture:** Spring Cloud 2023.0.1 (Netflix Eureka Server & Spring Cloud Gateway)
- **Microservices Pattern:** Service Discovery, API Gateway routing, Independent Domain Services
- **Frontend:** React.js 18.3, Vite, Lucide React
- **Data Persistence:** Spring Data JPA with In-Memory Relational Database (H2)
- **Communication:** RESTful APIs (JSON over HTTP)

---

## 2. Microservices Architecture & Port Registry

```
                         React.js Frontend (Port 3000)
                                      │
                                      ▼ (REST APIs)
                        Spring Cloud Gateway (Port 8080)
                                      │
              ┌───────────────────────┴───────────────────────┐
              ▼                                               ▼
Spring Cloud Eureka Server (:8761)              Distributed Microservices
(Service Discovery Registry)                                  │
                                ┌─────────────────────────────┼─────────────────────────────┐
                                ▼                             ▼                             ▼
                        User Service                  Scholarship Service           Application Service
                           (:8081)                          (:8082)                       (:8083)
                                │                             │                             │
                                └─────────────────────────────┼─────────────────────────────┘
                                                              ▼
                                ┌─────────────────────────────┼─────────────────────────────┐
                                ▼                             ▼                             ▼
                        Document Service              Notification Service          Admin & Monitoring
                           (:8084)                          (:8085)                       (:8086)
                                                              │
                                                              ▼
                                                  Relational Database (H2)
```

| Component | Port | Technology | Purpose |
|---|---|---|---|
| **Eureka Server** | `8761` | Spring Cloud Netflix Eureka | Dynamic service registration & discovery |
| **API Gateway** | `8080` | Spring Cloud Gateway | Centralized routing and load balancing to microservices |
| **User Service** | `8081` | Spring Boot + JPA | Student and administrator profile management & auth |
| **Scholarship Service** | `8082` | Spring Boot + JPA | Scholarship programs catalog & criteria rules engine |
| **Application Service** | `8083` | Spring Boot + JPA | Application submission, lifecycle tracking & reviewer remarks |
| **Document Service** | `8084` | Spring Boot + JPA | Supporting certificate uploads & verification |
| **Notification Service** | `8085` | Spring Boot + JPA | Real-time notifications and alerts |
| **Admin Service** | `8086` | Spring Boot + JPA | Aggregated reporting, system health & audit trails |
| **React Frontend** | `3000` | React.js + Vite | Interactive web portal for Students and Administrators |

---

## 3. How to Run

### Method 1: Quick 1-Click Launch (Recommended for Lab / Viva)
Double-click `start-all.bat` or run in PowerShell:
```powershell
.\start-all.ps1
```
- Starts the Spring Boot Microservices Backend on `http://localhost:8080`
- Opens the React.js web interface on `http://localhost:3000`

---

### Method 2: Full Distributed Cluster Launch (Eureka + Gateway + Microservices)
To launch all individual microservice terminals independently:
```bat
start-microservices.bat
```
or in PowerShell:
```powershell
.\start-microservices.ps1
```
- **Eureka Dashboard:** `http://localhost:8761` (View all microservice registrations)
- **Spring Cloud Gateway:** `http://localhost:8080`
- **React.js Frontend:** `http://localhost:3000`

---

## 4. Pre-seeded Demo Profiles

You can toggle between profiles with 1 click in the top navbar:

| User | Role | University ID / Roll | CGPA | Category | Notes |
|---|---|---|---|---|---|
| **Student 1** | Student | `2420030115` | **8.92** | OBC | High Merit Profile |
| **Student 2** | Student | `2420030128` | **9.15** | General | Top Ranker Profile |
| **Student 3** | Student | `2420030124` | **8.45** | EWS | Need-cum-Merit Profile |
| **Faculty Administrator** | Admin | `FAC-CSE-104` | — | Faculty | Approval Authority |

---

## 5. Main Features

- **Student Portal**:
  - Browse scholarships with real-time **Check Eligibility** feedback.
  - 1-Step **Apply Now** modal to submit applications and attach documents.
  - **9-Stage Lifecycle Tracker** with progress bar and reviewer notes.
- **Admin Portal**:
  - Metric summary cards (Total Applications, Approved Grants, Disbursed Funds).
  - Application evaluation table with instant **"Approve"** and **"Reject"** buttons.
  - Publish new scholarship schemes.
- **SOA Architecture View**:
  - Live visual map of the 3-Tier Microservices Architecture and 9-stage workflow matching Review-2 Slide 4, 5 & 11.
