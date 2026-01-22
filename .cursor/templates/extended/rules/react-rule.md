<!-- Template: Used by /create-frontend-rules → .cursor/rules/react/RULE.md -->
---
description: React patterns for scalable frontend development
globs:
  - "**/*.tsx"
  - "**/*.jsx"
---

# React Patterns

## Philosophy

Build components that are **predictable, composable, and testable**. Prefer composition over inheritance. Keep components focused on a single responsibility.

## Component Structure

```typescript
// 1. Imports (external, then internal)
import { useState } from 'react';
import { Button } from '@/components/ui';

// 2. Types
interface UserCardProps {
  user: User;
  onEdit?: (user: User) => void;
}

// 3. Component
export function UserCard({ user, onEdit }: UserCardProps) {
  // 3a. Hooks
  const [isExpanded, setIsExpanded] = useState(false);
  
  // 3b. Derived state
  const fullName = `${user.firstName} ${user.lastName}`;
  
  // 3c. Handlers
  const handleEdit = () => onEdit?.(user);
  
  // 3d. Render
  return <div>...</div>;
}
```

## Component Sizing

- Max ~150 lines per component
- Extract reusable logic into custom hooks
- Extract repeated UI into smaller components

## State Management

### {{STATE_APPROACH}}

- **Local state first**: Start with `useState`
- **Lift when needed**: When siblings need same state
- **Server state**: Use React Query/TanStack Query
- **Global state**: Context or Zustand for truly global

## Custom Hooks

Extract when:
- Logic is reused across components
- Logic obscures component's purpose
- Logic needs independent testing

```typescript
function useAuth() {
  return { user, isAuthenticated, login, logout };
}
```

## Performance

Use sparingly and measure first:
- `useMemo` for expensive calculations
- `useCallback` for stable references to children
- `React.memo` for components with same props

## Server vs Client Components (Next.js)

Default to Server Components. Use `'use client'` only when needed:
- Interactivity (onClick, onChange)
- Browser APIs
- State (useState, useEffect)

## Accessibility

- Semantic HTML elements
- `aria-label` for icon buttons
- Keyboard navigation
- Focus management for modals

<!-- ================================================================
     PROJECT-SPECIFIC ADDITIONS
     ================================================================ -->

## Project-Specific Patterns

<!-- Add your team's patterns here -->
