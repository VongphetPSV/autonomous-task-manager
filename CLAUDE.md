# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Autonomous Task Manager - A task management application with a unique autonomous AI development workflow where GitHub issues can be automatically implemented by AI agents.

**Tech Stack:**
- Frontend: React 18 + Vite + TypeScript + Tailwind CSS + PWA (Workbox)
- Backend: FastAPI + PostgreSQL + SQLAlchemy + Alembic
- Deployment: Vercel (frontend) + Railway (backend)

## Development Commands

### Frontend (in `frontend/` directory)
```bash
npm install              # Install dependencies
npm run dev             # Start dev server (Vite)
npm run build           # Build for production
npm run preview         # Preview production build
npm run test            # Run tests (Jest/Vitest)
npm run lint            # Run ESLint
npm run type-check      # TypeScript type checking
```

### Backend (in `backend/` directory)
```bash
python -m venv venv                              # Create virtual environment
source venv/bin/activate                         # Activate venv (Linux/Mac)
# venv\Scripts\activate                          # Activate venv (Windows)
pip install -r requirements.txt                  # Install dependencies
uvicorn app.main:app --reload                    # Start dev server
pytest                                           # Run tests
pytest --cov=app --cov-report=html              # Run tests with coverage
ruff check .                                     # Run linter
mypy app                                         # Type checking
alembic revision --autogenerate -m "message"    # Create migration
alembic upgrade head                             # Apply migrations
```

## Architecture

### Autonomous Development System

This project uses a **two-agent autonomous workflow** for feature development:

1. **Strategic Agent** (`.agents/STRATEGIC-AGENT.md`)
   - Transforms GitHub issues (labeled `auto-implement`) into detailed specifications
   - Creates comprehensive technical blueprints with file structure, code examples, tests
   - Assesses complexity (simple/medium/complex) and auto-merge eligibility
   - Uses Claude Sonnet with higher temperature (0.7) for creative planning

2. **Execution Agent** (`.agents/EXECUTION-AGENT.md`)
   - Implements specifications created by Strategic Agent
   - Writes production-ready code following project standards
   - Ensures tests, accessibility, responsiveness, and quality gates
   - Uses Claude Sonnet with lower temperature (0.3) for precise implementation
   - Quality gates: TypeScript, ESLint, Ruff, MyPy, tests, build

**Auto-merge criteria** (from `.ai-config/agent-config.json`):
- Complexity: Simple or Medium
- No breaking changes, no architectural changes
- No new security implications
- Standard patterns used

### Project Structure

```
frontend/
  src/
    components/     # Reusable UI components (ComponentName/ folder pattern)
    pages/          # Page components
    hooks/          # Custom React hooks
    services/       # API integration services
    types/          # TypeScript type definitions
    utils/          # Utility functions

backend/
  app/
    api/v1/         # API routes (versioned)
    models/         # SQLAlchemy ORM models
    schemas/        # Pydantic schemas for validation
    services/       # Business logic layer
    core/           # Core configuration

.agents/            # AI agent instruction files
.ai-config/         # Agent configuration (models, thresholds, quality gates)
```

## Code Standards

### Frontend Conventions

**Component Pattern:**
```typescript
// Functional components with TypeScript interfaces
// File structure: ComponentName/ComponentName.tsx, ComponentName.test.tsx, index.ts
// Strict TypeScript - no 'any' types
// Tailwind CSS for all styling (mobile-first, dark mode support)

interface ComponentProps {
  prop1: string;
  onAction?: () => void;
}

export const Component: React.FC<ComponentProps> = ({ prop1, onAction }) => {
  // Implementation
};
```

**State Management:**
- Local state: `useState`
- Server state: React Query
- Global state: Context API (when needed)

**Routing:** React Router v6

**Testing:** Jest/React Testing Library with >80% coverage requirement

### Backend Conventions

**API Pattern:**
```python
# Async FastAPI endpoints
# RESTful structure with versioning (/api/v1/...)
# Pydantic schemas for all validation
# SQLAlchemy 2.0 async style
# Proper dependency injection

# models/task.py - SQLAlchemy model
# schemas/task.py - Pydantic schemas (Create, Update, Response)
# services/task.py - Business logic
# api/v1/tasks.py - API routes
```

**Database:**
- Use UUIDs for primary keys
- Include timestamps: `created_at`, `updated_at`
- Soft deletes where appropriate
- Alembic for migrations (required for schema changes)

**Error Handling:**
- Use `HTTPException` with proper status codes
- Clear, user-friendly error messages
- Frontend: Toast notifications for errors

**Testing:** pytest with >80% coverage requirement

## Quality Standards

All code must meet these criteria before PR:

**Code Quality:**
- TypeScript: strict mode, no `any` types
- Python: type hints everywhere
- No console.log or commented code
- Proper error handling and input validation
- SQL injection prevention

**Testing:**
- Unit tests + integration tests
- All tests passing
- Coverage >80%
- Edge cases covered

**UI/UX:**
- Responsive design (mobile-first)
- Loading states and error states
- Accessibility: WCAG 2.1 AA compliance
- Performance: <3s load time

**Performance Targets:**
- Lighthouse score: >90
- Bundle size: <500KB
- API response time: <200ms

## Development Workflow

### Standard Development
```bash
git checkout -b feature/your-feature
# Make changes, commit, push
git push origin feature/your-feature
# Create PR
```

### Autonomous Development (via AI Agents)
1. Create GitHub issue with label `auto-implement`
2. Strategic Agent creates specification (~3 min)
3. Execution Agent implements feature (~15 min)
4. Auto-deploys to production (~5 min)

## Important Notes

- **PWA Support:** This app has offline support via Workbox - be mindful of service worker caching
- **Database Migrations:** Always create Alembic migrations for schema changes
- **Type Safety:** Both TypeScript (frontend) and Python type hints (backend) are required
- **No Backend Yet:** As of initial setup, backend structure is planned but not yet created
- **Agent-First Development:** This project is designed for autonomous AI development - follow the patterns in `.agents/` when implementing features
