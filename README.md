# Hikayat Forum – Microservices-Powered Community Forum

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

**Hikayat Forum** is a scalable, full-stack community forum built with **Go microservices** on the backend and a **Next.js + React + Tailwind CSS** frontend. Designed with clean architecture, gRPC communication, and secure authentication, it serves as a foundation for forums, Q&A platforms, or social communities.

---

## 🌟 Features

### Backend (Go Microservices)
- **Auth Service**: User registration, login, JWT issuance, password hashing (bcrypt)
- **Post Service**: CRUD operations for forum posts, categories, metadata
- **Gateway**: REST-to-gRPC translation, JWT validation, rate limiting
- **(Planned)** Comment & Notification Services
- **gRPC** for internal service communication (high performance, typed contracts)
- **Docker Compose** for unified local orchestration

### Frontend (Next.js 14 + App Router)
- Responsive, clean UI with **Tailwind CSS**
- User registration & login flows
- Post listing and creation
- Secure API communication via Next.js API routes (proxy to gateway)
- TypeScript, React Server Components, and client-side interactivity

---

## 🛠️ Tech Stack

| Layer           | Technology                     |
|-----------------|-------------------------------|
| **Frontend**    | Next.js 14 (App Router), React, TypeScript, Tailwind CSS |
| **Backend**     | Go (Gin, gRPC, JWT, bcrypt)   |
| **API**         | REST (public), gRPC (internal)|
| **Infra**       | Docker, Docker Compose        |
| **Database**    | PostgreSQL (configurable)     |

