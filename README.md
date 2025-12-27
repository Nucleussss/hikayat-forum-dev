# 📜 Hikayat Forum – A Modern Microservices-Powered Community Forum

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

## 🏗️ Architecture Overview

```
┌──────────────────┐
│   Frontend       │  ← Next.js + React + Tailwind
│ (localhost:3000) │
└─────────┬────────┘
          │ REST (HTTP/JSON)
┌─────────▼────────┐
│   Forum Gateway  │  ← Go service (port 8080)
│  (public entry)  │
└─────────┬────────┘
          │ gRPC
┌─────────▼────────┐     ┌──────────────────┐
│  Auth Service    │     │   Post Service   │
│ (gRPC: 50051)    │     │ (gRPC: 50052)    │
└──────────────────┘     └──────────────────┘
```

> All services are containerized and managed via `docker-compose.yml`.

---

## 🚀 Quick Start

### Prerequisites
- Docker & Docker Compose
- Node.js ≥ 18
- Go ≥ 1.21 (if building backend from source)

### 1. Clone the Project
```bash
git clone https://github.com/your-username/hikayat-forum.git
cd hikayat-forum
```

### 2. Start Backend Services
```bash
# Build and run all microservices + gateway + DB
docker-compose up --build
```
> Services will be available at:
> - Gateway: `http://localhost:8080`
> - Auth gRPC: `localhost:50051`
> - Post gRPC: `localhost:50052`

### 3. Launch Frontend
```bash
cd hikayat-forum-frontend
npm install
npm run dev
```
> Visit: [http://localhost:3000](http://localhost:3000)

---

## 📂 Project Structure

```
hikayat-forum/
├── docker-compose.yml          # Orchestrates all services
├── forum-protos/               # Shared .proto contracts
├── hikayat-forum-auth-service/ # Go: user auth (gRPC)
├── hikayat-forum-post-service/ # Go: post management (gRPC)
├── hikayat-forum-gateway/      # Go: REST gateway (port 8080)
├── hikayat-forum-frontend/     # Next.js + React + Tailwind
│   ├── src/
│   │   ├── app/
│   │   │   ├── register/page.tsx
│   │   │   ├── login/page.tsx
│   │   │   └── api/auth/.../route.ts  # Secure API proxies
│   │   └── ...
│   └── ...
├── initdb/                     # Database initialization scripts
└── scripts/                    # Dev utility scripts
```

---

## 🔐 Authentication Flow

1. User registers via `/register` → frontend calls `/api/auth/register`
2. Next.js API route proxies to `forum-gateway`
3. Gateway validates → calls `auth-service` via gRPC
4. On success: returns JWT (stored securely via HTTP-only cookies or localStorage)
5. Subsequent requests include JWT → Gateway validates → routes to services

---

## 🛠️ Tech Stack

| Layer           | Technology                     |
|-----------------|-------------------------------|
| **Frontend**    | Next.js 14 (App Router), React, TypeScript, Tailwind CSS |
| **Backend**     | Go (Gin, gRPC, JWT, bcrypt)   |
| **API**         | REST (public), gRPC (internal)|
| **Infra**       | Docker, Docker Compose        |
| **Database**    | PostgreSQL (configurable)     |

---

## 📈 Roadmap (Planned)

- [ ] Comment service (gRPC)
- [ ] Notification service (email + in-app)
- [ ] User profiles & avatars
- [ ] Post voting & threading
- [ ] Production deployment guide (Nginx, TLS, env secrets)
- [ ] OpenAPI spec for gateway

---

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repo
2. Create a feature branch (`git checkout -b feature/xyz`)
3. Commit your changes (`git commit -am 'Add xyz'`)
4. Push to the branch (`git push origin feature/xyz`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

---

## 💬 Support

Built with ❤️ for developers exploring microservices and modern full-stack patterns.  
Have questions or feedback? Open an [issue](https://github.com/Nucleussss/hikayat-forum/issues)!

---
