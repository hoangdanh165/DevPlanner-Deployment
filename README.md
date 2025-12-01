# 🚀 DevPlanner – AI Project Planner

_Your intelligent assistant for planning, structuring, and documenting your own software projects._

DevPlanner is an AI-powered project planning platform that transforms a simple project idea into a complete, structured project blueprint — including sections, diagrams, technical designs, tasks, and exportable documents.  
Built with **Django**, **React**, **Celery**, **FastAPI**, and **Redis**, DevPlanner provides a scalable, modular architecture for generating consistent, reusable project plans.

---

## ✨ Features

### 🔮 AI-Driven Project Generation

- Turn one prompt into a fully structured project plan
- Automatic generation of:
  - Overview
  - Features
  - Technical Stack
  - Tasks / User Stories
  - Architecture Diagrams (Mermaid)
  - Database ERD
  - System Architecture
  - Sequence Diagrams
  - Documentation Sections

### 🧩 Modular Planning Structure

- Projects are divided into Sections
- Each section has multiple Versions (historical generations)
- Consistent cross-section reasoning using custom AI orchestration
- Saved plans can be reused as templates for future projects

### ⚙️ Backend (Django + Celery)

- RESTful APIs for project, sections, versions, diagrams, tasks
- Asynchronous AI generation tasks using Celery
- Redis for task queue + caching
- Long-running generation streaming updates through FastAPI WebSocket Server
- PostgreSQL with rich relational schema

### 🖥️ Frontend (Nuxt 3 / React UI)

- Clean, responsive UI
- Realtime progress streaming for AI generation
- Version selector for each section
- Diagram preview with zoom & pan
- Dark/light themes
- Export project as **PDF**, **DOCX**, or **Markdown**

### 🔌 Future Integrations

- GitHub
- Trello / Jira task export

---

## 🏗️ System Architecture

```mermaid
flowchart LR
    User((User))
    React[React Frontend]
    Django[Django API]
    Celery[Celery Workers]
    Redis[Redis Queue + Cache]
    FastAPI[FastAPI WebSocket Relay]
    DB[(PostgreSQL)]

    User --> Nuxt
    React --> Django
    Django --> DB
    Django --> Celery
    Celery --> Redis
    Django --> FastAPI
    FastAPI --> Nuxt
```

---

## 🧪 Requirements

```bash
Python 3.10+

Node.js 22+

PostgreSQL 16+

Redis 7+

Docker + Docker Compose (Recommended)
```

---

## 🔧 Local Development Setup

### 1️⃣ Clone Repository

```bash
git clone https://github.com/yourname/devplanner.git
cd devplanner
```

### 2️⃣ Backend Setup (Django)

```bash
cd backend
pip install -r requirements.txt
cp .env.example .env
python manage.py migrate
python manage.py runserver
```

### 3️⃣ Frontend Setup (Nuxt 3)

```bash
cd frontend
npm install
npm run dev
```

### 4️⃣ WebSocket Server (FastAPI)

```bash
cd websocket-relay
pip install -r requirements.txt
uvicorn main:app --reload --port 8001
```

### 5️⃣ Celery Worker

```bash
celery -A backend worker -l INFO
celery -A backend beat -l INFO
```

### 🐳 Run with Docker (Recommended)

```bash
docker compose up --build
```

## 📜 License

MIT License — free for personal & commercial use.
