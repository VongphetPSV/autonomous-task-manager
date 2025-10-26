# Autonomous Task Manager

A fully autonomous task management application built with React PWA, FastAPI, and PostgreSQL.

## Features

- ✅ Create, edit, delete tasks
- 🏷️ Categories and priorities
- 🔍 Search and filter
- 📱 PWA with offline support
- 🤖 Autonomous AI development workflow
- 🚀 Auto-deployment pipeline

## Tech Stack

**Frontend:**
- React 18
- Vite
- Tailwind CSS
- PWA (Workbox)

**Backend:**
- FastAPI
- PostgreSQL
- SQLAlchemy
- Alembic

**DevOps:**
- GitHub Actions
- Autonomous AI Agents
- Docker
- Vercel (Frontend) / Railway (Backend)

## Quick Start

### Prerequisites
- Node.js 18+
- Python 3.11+
- PostgreSQL 14+

### Installation

#### Frontend
\`\`\`bash
cd frontend
npm install
npm run dev
\`\`\`

#### Backend
\`\`\`bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload
\`\`\`

## Development Workflow

### Autonomous Feature Development

1. **Create Issue** with label `auto-implement`
2. **Strategic Agent** creates specification (~3 min)
3. **Execution Agent** implements feature (~15 min)
4. **Auto-Deploy** to production (~5 min)

### Manual Development

\`\`\`bash
# Create feature branch
git checkout -b feature/your-feature

# Make changes
# Commit and push
git push origin feature/your-feature

# Create PR
\`\`\`

## Project Structure

\`\`\`
autonomous-task-manager/
├── .github/workflows/      # GitHub Actions
├── .agents/                # AI agent instructions
├── frontend/               # React app
├── backend/                # FastAPI app
├── database/               # DB migrations
├── docs/                   # Documentation
└── infrastructure/         # Deployment configs
\`\`\`

## Documentation

- [API Documentation](docs/api/README.md)
- [User Guide](docs/USER-GUIDE.md)
- [Development Guide](docs/DEVELOPMENT.md)
- [Agent Workflow](docs/AGENT-WORKFLOW.md)

## License

MIT

## Contributors

Built with autonomous AI agents 🤖
EOF