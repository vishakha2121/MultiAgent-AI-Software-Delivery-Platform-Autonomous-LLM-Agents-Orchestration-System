# 🚀 Multi-Agent AI Software Delivery Platform

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-18+-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-5+-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/TailwindCSS-3+-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-3+-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![Gemini](https://img.shields.io/badge/Google_Gemini-API-4285F4?style=for-the-badge&logo=google&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

### 🤖 Six AI Agents. One Pipeline. Full Software Delivery — Autonomously.

*An autonomous, agent-driven platform that simulates and automates the complete Software Development Life Cycle (SDLC) — from raw requirement gathering to final deployment — using a team of six specialized AI agents powered by Google's Gemini API.*

[Features](#-features) • [Architecture](#-system-architecture) • [Setup](#-installation--setup) • [Usage](#-usage) • [API](#-api-endpoints) • [Roadmap](#-roadmap)

</div>

---

## 📖 Table of Contents

1. [Overview](#-overview)
2. [The Core Idea](#-the-core-idea)
3. [Features](#-features)
4. [The Six AI Agents](#-the-six-ai-agents)
5. [System Architecture](#-system-architecture)
6. [Agent Workflow Pipeline](#-agent-workflow-pipeline)
7. [Tech Stack](#-tech-stack)
8. [Project Structure](#-project-structure)
9. [Database Schema](#-database-schema)
10. [Installation & Setup](#-installation--setup)
11. [Environment Variables](#-environment-variables)
12. [Usage](#-usage)
13. [API Endpoints](#-api-endpoints)
14. [Screenshots](#-screenshots)
15. [Roadmap](#-roadmap)
16. [Learning Outcomes](#-learning-outcomes)
17. [Contributing](#-contributing)
18. [License](#-license)
19. [Author](#-author)

---

## 🌟 Overview

**Multi-Agent AI Software Delivery Platform** is a full-stack, agentic AI system designed to demonstrate how multiple Large Language Models (LLMs) can collaborate like a real software engineering team to deliver end-to-end software solutions.

Unlike traditional AI coding assistants where a single model handles everything, this platform distributes responsibilities across **six specialized autonomous agents**, each acting as a domain expert. Every agent consumes the previous agent's output and produces a structured artifact, forming a **sequential, collaborative pipeline**.

The result? A complete software delivery flow:

```
User Idea → Requirements → Architecture → Code → Tests → Security → Deployment
```

All orchestrated automatically, all visible in a beautiful real-time React dashboard.

---

## 💡 The Core Idea

In traditional AI coding assistants, one model handles everything — requirements, design, coding, testing, deployment. This leads to shallow, inconsistent output.

This project solves that problem by **splitting the SDLC into six autonomous agents**, each with:

- Its own **role** and **responsibility**
- Its own **prompt template** engineered specifically for that task
- Its own **input** from the previous agent
- Its own **output** stored as a structured artifact
- Its own **status** tracked in the database and streamed to the UI

Every agent is **modular and replaceable**, allowing future extension (e.g., adding a "Documentation Agent" or "Code Review Agent").

The orchestration is built **from scratch without heavy frameworks like LangChain** — proving deep understanding of agent coordination, prompt chaining, state management, and pipeline design.

---

## ✨ Features

### 🎯 Core Features
- ✅ **6 Specialized AI Agents** — Requirement, Architecture, Coding, Testing, Security, DevOps
- ✅ **Autonomous Sequential Pipeline** — Each agent consumes previous agent's output
- ✅ **Powered by Google Gemini API** — Fast, free-tier friendly, CPU-compatible
- ✅ **Real-time Pipeline Visualization** — Watch agents work live in the dashboard
- ✅ **Live Log Streaming** — Terminal-style logs updated in real-time
- ✅ **Artifact Storage** — All generated outputs stored and downloadable
- ✅ **JWT Authentication** — Secure user login/signup
- ✅ **Project Management** — Create, track, and manage multiple projects

### 🎨 UI/UX Features
- ✅ **Modern Dark Theme** — Gradient accents (purple → blue → cyan)
- ✅ **Animated Pipeline Visualizer** — Framer Motion powered
- ✅ **Responsive Design** — Works on desktop, tablet, mobile
- ✅ **Toast Notifications** — Smooth user feedback
- ✅ **Beautiful Dashboards** — Stats cards, activity feeds, project lists

### 🧠 Technical Features
- ✅ **No LangChain Dependency** — Pure Python orchestration from scratch
- ✅ **Async FastAPI Backend** — Fast, modern, auto-documented API
- ✅ **SQLAlchemy ORM** — Clean DB abstraction
- ✅ **SQLite Database** — Zero setup, CPU-friendly
- ✅ **Modular Architecture** — Easy to extend, test, and maintain
- ✅ **REST API + Polling/WebSocket** — For live updates

---

## 🤖 The Six AI Agents

| # | Agent | Role | Input | Output |
|---|-------|------|-------|--------|
| 1️⃣ | 📋 **Requirement Agent** | Business Analyst | Raw user idea | SRS, user stories, acceptance criteria |
| 2️⃣ | 🏗️ **Architecture Agent** | System Architect | Requirements doc | System architecture, module breakdown, tech stack |
| 3️⃣ | 💻 **Coding Agent** | Software Engineer | Architecture doc | Boilerplate code, folder structure, implementation |
| 4️⃣ | 🧪 **Testing Agent** | QA Engineer | Generated code | Unit tests, integration tests, QA report |
| 5️⃣ | 🔒 **Security Review Agent** | Security Engineer | Code + tests | Vulnerability report (OWASP Top 10), fixes |
| 6️⃣ | 🚀 **DevOps Agent** | DevOps Engineer | All artifacts | Dockerfile, CI/CD pipeline, deploy scripts |

Each agent is implemented as a Python class inheriting from a common `BaseAgent`, and uses prompt templates stored in `prompt_templates.py`.

---

## 🏛️ System Architecture

```
┌───────────────────────────────────────────────────────────────┐
│                    FRONTEND (React + Vite)                    │
│   ┌─────────┐  ┌──────────┐  ┌───────────┐  ┌────────────┐    │
│   │ Landing │  │Dashboard │  │ Pipeline  │  │ Artifacts  │    │
│   └─────────┘  └──────────┘  └───────────┘  └────────────┘    │
│         │            │              │              │          │
└─────────┼────────────┼──────────────┼──────────────┼──────────┘
          │            │              │              │
          │      REST API + WebSocket (Axios + WS)   │
          │            │              │              │
┌─────────▼────────────▼──────────────▼──────────────▼──────────┐
│                    BACKEND (FastAPI + Python)                 │
│  ┌──────────┐  ┌──────────────┐  ┌─────────────────────────┐  │
│  │ API      │─▶│ Orchestrator │─▶│  Agent Registry         │  │
│  │ Routes   │  │  Pipeline    │  │  ┌──────────────────┐   │  │
│  └──────────┘  └──────────────┘  │  │ Requirement      │   │  │
│                                   │  │ Architecture     │   │  │
│  ┌──────────┐  ┌──────────────┐  │  │ Coding           │   │  │
│  │ Services │─▶│ Gemini API   │  │  │ Testing          │   │  │
│  │ Layer    │  │  Service     │  │  │ Security         │   │  │
│  └──────────┘  └──────────────┘  │  │ DevOps           │   │  │
│                                   │  └──────────────────┘   │  │
│  ┌──────────┐  ┌──────────────┐  └─────────────────────────┘  │
│  │ Models   │─▶│ SQLite DB    │                               │
│  └──────────┘  └──────────────┘                               │
└───────────────────────────────────────────────────────────────┘
          │
          ▼
┌───────────────────────────────────────────────────────────────┐
│              STORAGE (Generated Artifacts)                    │
│  requirements/ | architecture/ | code/ | tests/ | security/   │
└───────────────────────────────────────────────────────────────┘
```

---

## 🔄 Agent Workflow Pipeline

```
                    ┌─────────────────────────┐
                    │  👤 User submits idea   │
                    └────────────┬────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │  📋 Requirement Agent   │
                    │  → SRS + user stories   │
                    └────────────┬────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │  🏗️ Architecture Agent  │
                    │  → System design        │
                    └────────────┬────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │  💻 Coding Agent        │
                    │  → Source code          │
                    └────────────┬────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │  🧪 Testing Agent       │
                    │  → Test cases + report  │
                    └────────────┬────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │  🔒 Security Agent      │
                    │  → Vulnerability report │
                    └────────────┬────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │  🚀 DevOps Agent        │
                    │  → Deploy scripts       │
                    └────────────┬────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │  📦 Final Deliverables  │
                    └─────────────────────────┘
```

Each step's output is:
- ✅ Stored in SQLite (`agent_runs` + `artifacts` tables)
- ✅ Saved as file in `backend/storage/`
- ✅ Streamed live to frontend logs

---

## 🛠️ Tech Stack

### Backend
| Tech | Purpose |
|------|---------|
| **Python 3.10+** | Core language |
| **FastAPI** | Web framework (async, fast, auto-docs) |
| **Uvicorn** | ASGI server |
| **SQLAlchemy** | ORM |
| **SQLite** | Database (no setup needed) |
| **Pydantic** | Data validation |
| **python-jose** | JWT tokens |
| **passlib[bcrypt]** | Password hashing |
| **google-generativeai** | Gemini API SDK |
| **python-dotenv** | Environment variables |
| **WebSockets** | Live updates |

### Frontend
| Tech | Purpose |
|------|---------|
| **React 18** | UI library |
| **Vite** | Build tool (super fast) |
| **React Router DOM** | Routing |
| **TailwindCSS** | Styling |
| **Framer Motion** | Animations |
| **Axios** | HTTP client |
| **React Hot Toast** | Notifications |
| **Lucide React** | Icons |

### Database
| Tech | Purpose |
|------|---------|
| **SQLite** | Main database |
| **SQLAlchemy** | ORM layer |

### AI
| Tech | Purpose |
|------|---------|
| **Google Gemini API** | LLM for all agents |
| **Custom Prompts** | Engineered in `prompt_templates.py` |

---

## 📁 Project Structure

```
multi-agent-ai-platform/
│
├── README.md
├── .gitignore
├── .env.example
├── docker-compose.yml
│
├── backend/                          # 🐍 FastAPI Backend
│   ├── main.py                       # Entry point
│   ├── config.py                     # Settings
│   ├── requirements.txt
│   ├── .env
│   │
│   ├── app/
│   │   ├── api/                      # API routes
│   │   │   ├── routes_auth.py
│   │   │   ├── routes_projects.py
│   │   │   ├── routes_agents.py
│   │   │   ├── routes_pipeline.py
│   │   │   ├── routes_artifacts.py
│   │   │   └── routes_health.py
│   │   │
│   │   ├── agents/                   # ⭐ Core agents
│   │   │   ├── base_agent.py
│   │   │   ├── requirement_agent.py
│   │   │   ├── architecture_agent.py
│   │   │   ├── coding_agent.py
│   │   │   ├── testing_agent.py
│   │   │   ├── security_agent.py
│   │   │   └── devops_agent.py
│   │   │
│   │   ├── orchestrator/             # Pipeline coordination
│   │   │   ├── pipeline.py
│   │   │   ├── state_manager.py
│   │   │   └── agent_registry.py
│   │   │
│   │   ├── services/                 # Business logic
│   │   │   ├── gemini_service.py
│   │   │   ├── prompt_templates.py
│   │   │   ├── project_service.py
│   │   │   ├── artifact_service.py
│   │   │   └── auth_service.py
│   │   │
│   │   ├── models/                   # DB models
│   │   ├── schemas/                  # Pydantic schemas
│   │   ├── db/                       # DB setup
│   │   ├── core/                     # Security, logger
│   │   └── utils/
│   │
│   ├── database/                     # SQL files
│   │   ├── schema.sql
│   │   ├── seed_data.sql
│   │   └── migrations/
│   │
│   ├── tests/
│   ├── storage/                      # Generated artifacts
│   └── logs/
│
├── frontend/                         # ⚛️ React Frontend
│   ├── package.json
│   ├── vite.config.js
│   ├── tailwind.config.js
│   ├── index.html
│   │
│   └── src/
│       ├── main.jsx
│       ├── App.jsx
│       ├── api/                      # API calls
│       ├── components/               # Reusable UI
│       │   ├── common/
│       │   ├── agents/
│       │   ├── pipeline/
│       │   ├── projects/
│       │   └── dashboard/
│       ├── pages/                    # Screens
│       ├── layouts/
│       ├── routes/
│       ├── context/
│       ├── hooks/
│       ├── services/
│       └── utils/
│
├── docs/                             # Documentation
│   ├── PROJECT_OVERVIEW.md
│   ├── ARCHITECTURE_DIAGRAM.md
│   ├── AGENT_WORKFLOW.md
│   ├── API_DOCUMENTATION.md
│   ├── SETUP_GUIDE.md
│   └── screenshots/
│
└── scripts/                          # Helper scripts
    ├── start_backend.sh
    ├── start_frontend.sh
    ├── setup_db.sh
    └── run_all.sh
```

---

## 🗄️ Database Schema

### Tables

| Table | Purpose | Key Columns |
|-------|---------|-------------|
| `users` | User accounts | id, username, email, hashed_password, created_at |
| `projects` | Software projects | id, user_id, title, description, status, created_at |
| `agent_runs` | Each agent execution | id, project_id, agent_name, status, started_at, finished_at |
| `artifacts` | Generated files | id, project_id, agent_run_id, type, file_path, content |
| `pipeline_logs` | Live logs for UI | id, project_id, agent_name, message, level, timestamp |
| `api_usage` | Gemini API tracking | id, user_id, tokens_used, timestamp |

### Relationships

```
users (1) ──< projects (N)
projects (1) ──< agent_runs (N)
agent_runs (1) ──< artifacts (N)
projects (1) ──< pipeline_logs (N)
```

---

## 🚀 Installation & Setup

### Prerequisites

- ✅ Python 3.10 or higher
- ✅ Node.js 18+ and npm
- ✅ Git
- ✅ Google Gemini API Key ([Get it free here](https://aistudio.google.com/app/apikey))

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/vishakha2121/MultiAgent-AI-Software-Delivery-Platform-Autonomous-LLM-Agents-Orchestration-System.git
cd MultiAgent-AI-Software-Delivery-Platform-Autonomous-LLM-Agents-Orchestration-System
```

### 2️⃣ Backend Setup

```bash
cd backend

# Create virtual environment
python -m venv venv

# Activate (Windows)
venv\Scripts\activate

# Activate (Mac/Linux)
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

### 3️⃣ Environment Variables

Create `backend/.env` file:

```env
GEMINI_API_KEY=your_gemini_api_key_here
SECRET_KEY=your_super_secret_jwt_key_here
DATABASE_URL=sqlite:///./multi_agent.db
ACCESS_TOKEN_EXPIRE_MINUTES=60
```

Create `frontend/.env` file:

```env
VITE_API_URL=http://localhost:8000
```

### 4️⃣ Initialize Database

```bash
cd backend
python app/db/init_db.py
```

### 5️⃣ Run Backend

```bash
uvicorn main:app --reload --port 8000
```

Backend running at: **http://localhost:8000**  
API docs at: **http://localhost:8000/docs** 🎉

### 6️⃣ Frontend Setup

Open a **new terminal**:

```bash
cd frontend
npm install
npm run dev
```

Frontend running at: **http://localhost:5173** 🚀

---

## 🔐 Environment Variables

| Variable | Description | Where |
|----------|-------------|-------|
| `GEMINI_API_KEY` | Your Google Gemini API key | backend/.env |
| `SECRET_KEY` | JWT signing secret | backend/.env |
| `DATABASE_URL` | SQLite DB path | backend/.env |
| `ACCESS_TOKEN_EXPIRE_MINUTES` | JWT expiry | backend/.env |
| `VITE_API_URL` | Backend URL | frontend/.env |

⚠️ **Never commit `.env` files to GitHub!**

---

## 📖 Usage

### 1. Sign Up / Login
Open `http://localhost:5173` → Register a new account.

### 2. Create a New Project
Click **"New Project"** → Enter your software idea:
> *"Build a task management app with user auth, task CRUD, and deadline reminders."*

### 3. Start the AI Pipeline
Click **"Run Pipeline"** → Watch 6 agents work in sequence:
- 📋 Requirement → SRS generated
- 🏗️ Architecture → System design
- 💻 Coding → Source code
- 🧪 Testing → Test cases
- 🔒 Security → Vulnerability report
- 🚀 DevOps → Deployment scripts

### 4. View Artifacts
Click **"Artifacts"** → Download all generated files.

### 5. Monitor Live Logs
Watch agents "think" in real-time via the **Live Logs** panel.

---

## 🔌 API Endpoints

### 🔐 Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | Register new user |
| POST | `/api/auth/login` | Login and get JWT |
| GET | `/api/auth/me` | Get current user |

### 📁 Projects
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/projects` | List user's projects |
| POST | `/api/projects` | Create project |
| GET | `/api/projects/{id}` | Get project details |
| DELETE | `/api/projects/{id}` | Delete project |

### 🤖 Agents
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/agents` | List all agents |
| GET | `/api/agents/{name}` | Get agent details |
| POST | `/api/agents/{name}/run` | Run single agent |

### 🔄 Pipeline
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/pipeline/start/{project_id}` | Start full pipeline |
| GET | `/api/pipeline/status/{project_id}` | Get pipeline status |
| GET | `/api/pipeline/logs/{project_id}` | Get live logs |
| WS | `/ws/pipeline/{project_id}` | WebSocket for live updates |

### 📦 Artifacts
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/artifacts/{project_id}` | List all artifacts |
| GET | `/api/artifacts/download/{id}` | Download artifact |

### ❤️ Health
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/health` | Health check |

Full API docs: **http://localhost:8000/docs**

---

## 📸 Screenshots

### 🏠 Landing Page
![Landing Page](docs/screenshots/home.png)

### 📊 Dashboard
![Dashboard](docs/screenshots/agents.png)

### 🔄 Pipeline Visualizer
![Pipeline](docs/screenshots/pipeline.png)

---

## 🗺️ Roadmap

### ✅ Phase 1 — Foundation (Done)
- [x] Project structure setup
- [x] FastAPI backend skeleton
- [x] React frontend skeleton
- [x] SQLite + SQLAlchemy setup
- [x] JWT authentication

### 🚧 Phase 2 — Agents (In Progress)
- [ ] Base agent class
- [ ] 6 specialized agents
- [ ] Prompt templates for each
- [ ] Gemini API integration

### 📅 Phase 3 — Orchestration
- [ ] Pipeline engine
- [ ] State manager
- [ ] Live log streaming
- [ ] Artifact persistence

### 📅 Phase 4 — Frontend Polish
- [ ] Animated pipeline visualizer
- [ ] Real-time logs
- [ ] Artifact viewer
- [ ] Dark/light theme toggle

### 🔮 Phase 5 — Future Enhancements
- [ ] **Feedback Loop Agent** — Re-run failed tests automatically
- [ ] **Parallel agent execution** — For speed
- [ ] **GitHub PR automation** — Auto-commit generated code
- [ ] **Multi-LLM support** — Gemini + OpenAI + Claude
- [ ] **Vector DB memory** — Long-term agent memory
- [ ] **Code Review Agent** — 7th agent for peer review

---

## 🎓 Learning Outcomes

By building this project, developers learn:

### 🧠 AI & LLM Engineering
- Multi-agent system design
- Prompt engineering & chaining
- LLM orchestration from scratch (no LangChain)
- Context passing between agents
- Handling API rate limits & errors

### 🐍 Backend Engineering
- Async FastAPI development
- REST API design
- JWT authentication
- SQLAlchemy ORM
- Database design & relationships
- WebSocket for real-time communication

### ⚛️ Frontend Engineering
- React 18 hooks & context
- React Router v6
- TailwindCSS theming
- Framer Motion animations
- Axios API integration
- Polling & WebSocket handling

### 🏗️ System Design
- Modular architecture
- Separation of concerns
- State management
- Error handling
- File storage strategy

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👩‍💻 Author

**Vishakha**

- 🐙 GitHub: [@vishakha2121](https://github.com/vishakha2121)
- 💼 Project Link: [Multi-Agent AI Software Delivery Platform](https://github.com/vishakha2121/MultiAgent-AI-Software-Delivery-Platform-Autonomous-LLM-Agents-Orchestration-System)

---

## 🙏 Acknowledgements

- [Google Gemini API](https://ai.google.dev/) — For powering the agents
- [FastAPI](https://fastapi.tiangolo.com/) — For the amazing backend framework
- [React](https://react.dev/) — For the frontend
- [TailwindCSS](https://tailwindcss.com/) — For the beautiful styling
- [Vite](https://vitejs.dev/) — For the blazing fast build tool

---

<div align="center">

### ⭐ If you like this project, please give it a star! ⭐

**Built with ❤️ by Vishakha**

*"Where AI agents don't just code — they ship."*

</div>