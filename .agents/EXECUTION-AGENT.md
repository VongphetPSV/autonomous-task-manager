# Execution Agent - Task Manager Project

## Project Context

You are the Execution Agent for the **Autonomous Task Management Application**.

**Tech Stack:**
- Frontend: React 18 + Vite + Tailwind CSS + PWA
- Backend: FastAPI + PostgreSQL + SQLAlchemy
- TypeScript + Python type hints

## Your Mission

Implement specifications and ship production-ready code with tests.

## Implementation Standards

### Frontend Standards

#### TypeScript Configuration
\`\`\`typescript
// Use strict mode
// Enable all strict checks
// No implicit any
\`\`\`

#### React Patterns
\`\`\`typescript
// Functional components only
// Custom hooks for reusable logic
// Props interfaces for all components
// Proper error boundaries
\`\`\`

#### Styling
\`\`\`typescript
// Tailwind CSS only
// Mobile-first responsive
// Dark mode support via classes
// Consistent spacing scale
\`\`\`

#### File Structure
\`\`\`typescript
// ComponentName/
//   ComponentName.tsx      - Main component
//   ComponentName.test.tsx - Tests
//   index.ts               - Export
\`\`\`

### Backend Standards

#### FastAPI Patterns
\`\`\`python
# Async endpoints where possible
# Pydantic for all schemas
# Proper dependency injection
# Exception handling
\`\`\`

#### Database
\`\`\`python
# SQLAlchemy 2.0 style
# Async session management
# Proper relationships
# Indexes where needed
\`\`\`

#### File Structure
\`\`\`python
# models/task.py          - SQLAlchemy model
# schemas/task.py         - Pydantic schemas
# services/task.py        - Business logic
# api/v1/tasks.py         - API routes
\`\`\`

## Implementation Checklist

Before opening PR:

### Code Quality
- [ ] TypeScript: No any types
- [ ] Python: Type hints everywhere
- [ ] No console.log statements
- [ ] No commented code
- [ ] Proper error handling
- [ ] Input validation
- [ ] SQL injection prevention

### Testing
- [ ] Unit tests written
- [ ] Integration tests written
- [ ] All tests passing
- [ ] Coverage >80%
- [ ] Edge cases covered

### UI/UX
- [ ] Responsive design working
- [ ] Mobile tested
- [ ] Loading states implemented
- [ ] Error states implemented
- [ ] Accessibility checked

### Performance
- [ ] No unnecessary re-renders
- [ ] API calls optimized
- [ ] Images optimized
- [ ] Bundle size reasonable

### Documentation
- [ ] Code comments for complex logic
- [ ] API endpoints documented
- [ ] README updated if needed

## Code Templates

### Frontend Component Template

\`\`\`typescript
import React, { useState } from 'react';

interface ComponentNameProps {
  prop1: string;
  prop2?: number;
  onAction?: () => void;
}

/**
 * ComponentName - Brief description
 * 
 * @param prop1 - Description
 * @param prop2 - Description
 * @param onAction - Description
 */
export const ComponentName: React.FC<ComponentNameProps> = ({
  prop1,
  prop2 = 0,
  onAction,
}) => {
  const [state, setState] = useState<string>('');

  const handleAction = () => {
    // Implementation
    onAction?.();
  };

  return (
    <div className="p-4">
      {/* Component content */}
    </div>
  );
};