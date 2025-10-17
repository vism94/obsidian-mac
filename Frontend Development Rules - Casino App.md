## Tech Stack
- **React** 19.1+ with TypeScript 5.8+
- **Fastify-vite** 8.2+ with @fastify/react for SSR
- **React Router** 7.9+ for client-side routing
- **CSS Modules** for styling
- **Native fetch** for data fetching
- **Zod** for validation with fastify-type-provider-zod
- **SWC** for bundling and transpilation
- **react-hook-form** with @hookform/resolvers for forms

## Code Style

### TypeScript
- Use TypeScript strict mode (extends @rtdlab/ts-config)
- Use explicit return types for functions
- Avoid `any`, use `unknown` when type is truly unknown
- Define interfaces for all component props named `Properties`
- Use type imports with `import type` syntax
- Place types in dedicated `/types` directory
- Use path aliases: `@/` for client, `@server/` for server, `#` for types

### React
- Use functional components with hooks
- Prefer **function declarations** for page components: `export default function PageName() {}`
- Prefer **const arrow functions with named exports** for reusable components: `export const ComponentName = () => {}`
- Keep components small and focused (< 200 lines)
- Extract custom hooks for reusable logic with `use` prefix
- Use explicit prop types via `Properties` interface
- Always type generic components properly (e.g., form components)

### Naming Conventions
- **Components**: PascalCase files and exports (e.g., `GameCard.tsx`, `Button.tsx`)
- **Pages**: `page.tsx` convention in feature folders
- **Layouts**: lowercase with `.tsx` (e.g., `default.tsx`, `games.tsx`)
- **Hooks**: camelCase with `use` prefix (e.g., `useMenuMode.ts`)
- **Types**: camelCase files in `/types` (e.g., `game.ts`, `context.ts`)
- **Utilities**: camelCase files and exports (e.g., `comparator.ts`, `getProviderTitle.ts`)
- **Constants**: UPPER_SNAKE_CASE for values, camelCase for files
- **Props interface**: Always name it `Properties`
- **Boolean props/variables**: use `is`, `has`, `should` prefix

### File Organization
```
apps/casino/
├── src/
│   ├── server.ts              # Fastify server entry
│   ├── api/                   # API client functions
│   ├── bff/                   # Backend for Frontend
│   ├── plugins/               # Fastify plugins
│   ├── routes/                # Server routes
│   ├── types/                 # Shared TypeScript types
│   └── client/
│       ├── index.ts           # Client entry
│       ├── root.tsx           # Root component
│       ├── context.ts         # Context state & actions
│       ├── components/        # Reusable UI components
│       │   ├── Button/
│       │   │   ├── Button.tsx
│       │   │   ├── index.ts
│       │   │   └── styles.module.css
│       │   └── GameCard/
│       │       ├── GameCard.tsx
│       │       ├── index.ts
│       │       ├── styles.module.css
│       │       └── icons/
│       ├── pages/             # Route pages
│       │   ├── main/
│       │   │   ├── page.tsx
│       │   │   └── styles.module.css
│       │   └── games/
│       ├── layouts/           # Layout components
│       │   ├── default.tsx
│       │   └── games.tsx
│       ├── hooks/             # Custom hooks
│       ├── utilities/         # Utility functions
│       ├── types/             # Client-only types
│       └── constants/         # Constants and configs
```

### Component Structure
- Co-locate related files in component folders
- Always include `index.ts` for clean exports
- Place styles as `styles.module.css` in same folder
- Store component-specific assets (icons, images) in subfolder
- Export component from `index.ts`: `export { ComponentName } from './ComponentName'`

## Best Practices

### Performance
- Use `React.memo()` for expensive pure components
- Lazy load routes with dynamic imports
- Use `useCallback` for functions passed to memoized children
- Use `useMemo` for expensive computations
- Leverage Fastify-vite SSR for optimal initial load

### State Management
- Use Fastify-react context for global state (`useRouteContext`)
- Define state in `context.ts` with `state()` initializer
- Define actions for state mutations in `actions` export
- Use `useState` for local component state
- Keep state as close to where it's used as possible
- Never store derived state - compute it

### Data Fetching
- Use native `fetch` API with async/await
- Define API functions in `/api` directory
- Always type request and response interfaces
- Handle errors with try-catch blocks
- Use BFF pattern for complex data orchestration
- Implement proper loading states in components
- Leverage `getData()` export in pages for SSR data fetching

### Forms
- Use react-hook-form for all forms
- Validate with Zod schemas using @hookform/resolvers
- Create generic form components typed with `FieldValues`
- Show inline validation errors
- Disable submit during submission
- Use `register` pattern for form fields
- Merge refs when needed for complex input components

### Routing
- Use file-based routing with `page.tsx` convention
- Export default function from page components
- Export `getData()` for server-side data fetching
- Use dynamic routes with `[id]` folder naming
- Leverage layouts for shared UI structure
- Use `useRouteContext` for accessing route data and state

### API Layer
- Place API functions in `/api` directory organized by domain
- Always type parameters and return values
- Use `qs` for query string serialization
- Define default headers and options as constants
- Handle authentication with Bearer tokens
- Return `undefined` on errors, log to console
- Use proper HTTP methods (GET, POST, etc.)

### Styling
- Use CSS Modules exclusively (`.module.css`)
- Import as `import styles from './styles.module.css'`
- Use `clsx` for conditional class names
- Define global styles in `base.css`
- Use CSS variables in `variables.scss` for theming
- Follow BEM-like naming within modules
- Keep styles co-located with components
- Use `:global` pseudo-class when needed (configured in stylelint)

### Accessibility
- Use semantic HTML elements
- Include proper `aria-label` and `aria-disabled` attributes
- Ensure keyboard navigation works (`popoverTarget`, etc.)
- Provide alt text for images
- Maintain proper heading hierarchy
- Test with screen readers
- Use proper color contrast ratios

### Server-Side (Fastify)
- Register plugins before routes
- Use Zod schemas for validation with `fastify-type-provider-zod`
- Use `setSerializerCompiler` and `setValidatorCompiler`
- Implement proper error handling with try-catch
- Use fastify-plugin for reusable plugins
- Leverage Fastify decorators for shared functionality
- Use proper TypeScript types with `ZodTypeProvider`

## Code Quality

### Error Handling
- Use try-catch for all async operations
- Log errors to console (server) or user-friendly messages (client)
- Return `undefined` from API functions on errors
- Implement Error Boundaries for component errors
- Handle loading and error states in components
- Provide recovery actions when possible
- Check response.ok in fetch calls

### Type Safety
- Type everything in TypeScript
- Use path aliases for imports (`@/`, `@server/`, `#`)
- Define interfaces in `/types` directory
- Use `import type` for type-only imports
- Leverage Fastify type providers
- Use generic types for reusable components
- Avoid type assertions (`as`) when possible

### Comments
- Write self-documenting code
- Use JSDoc for public APIs
- Explain "why", not "what"
- Add TODO comments with context
- Document complex algorithms
- Keep comments up to date
- Remove commented-out code before committing

### Code Organization
- One component per file
- Group related functionality in folders
- Use index.ts for clean exports
- Separate concerns (API, UI, business logic)
- Keep server and client code separated
- Use consistent folder structure across features

## Project-Specific Patterns

### Context Pattern
```typescript
// context.ts exports
export function state(): ContextState {
  return { /* initial state */ };
}

export default async (ctx: Context) => {
  // Server-side context initialization
};

export const actions = {
  actionName(state: ContextState, payload: Payload) {
    // Mutate state
  },
};
```

### Page Pattern
```typescript
// page.tsx
import type { PageData } from './types';

export async function getData(ctx: Context): Promise<PageData> {
  // Server-side data fetching
  return { /* data */ };
}

export default function PageName() {
  const { data, state, actions } = useRouteContext<PageData, ContextState>();
  // Component logic
}
```

### Component Pattern
```typescript
// Component.tsx
import { clsx } from 'clsx';
import type { ReactNode } from 'react';
import styles from './styles.module.css';

interface Properties {
  children?: ReactNode;
  isActive?: boolean;
  onClick?: () => void;
}

export const Component = ({ children, isActive, onClick }: Properties) => {
  return (
    <div className={clsx(styles.wrapper, { [styles.active!]: isActive })}>
      {children}
    </div>
  );
};
```

### API Pattern
```typescript
// api/domain.ts
export const fetchData = async ({
  baseUrl,
  token,
}: RequestParams): Promise<ResponseData | undefined> => {
  const url = `${baseUrl}/endpoint`;
  const headers = { Authorization: `Bearer ${token}` };
  
  try {
    const response = await fetch(url, { headers });
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    return await response.json() as ResponseData;
  } catch (error) {
    console.error(error);
  }
};
```

## Build & Development

### Scripts
- `pnpm dev` - Development with hot reload
- `pnpm build` - Build both server and client
- `pnpm start` - Production server
- `pnpm lint` - ESLint check
- `pnpm stylelint` - Style linting
- `pnpm typecheck` - TypeScript validation

### Configuration
- Use workspace shared configs (@rtdlab/eslint-config, @rtdlab/ts-config, @rtdlab/stylelint)
- Configure path aliases in both vite.config.ts and tsconfig.json
- Use `.swcrc` for SWC configuration
- Define environment variables with `CLIENT_` prefix for client-side access

## Don't
- ❌ Use `var` - always use `const` or `let`
- ❌ Mutate state directly - use actions
- ❌ Use index as key in lists
- ❌ Import CSS without `.module.css` suffix
- ❌ Forget to cleanup effects
- ❌ Create massive components (split them)
- ❌ Ignore TypeScript errors
- ❌ Skip error handling in async functions
- ❌ Commit console.logs to production
- ❌ Use Tailwind classes (use CSS Modules)
- ❌ Mix server and client imports incorrectly
- ❌ Forget to export from index.ts
- ❌ Use anonymous default exports (name your functions)

## Always
- ✅ Type everything in TypeScript
- ✅ Handle loading and error states
- ✅ Use CSS Modules for styling
- ✅ Export components from index.ts
- ✅ Co-locate styles and assets with components
- ✅ Use path aliases for imports
- ✅ Name props interface `Properties`
- ✅ Use `clsx` for conditional classes
- ✅ Validate with Zod schemas
- ✅ Return undefined from API errors
- ✅ Use `useRouteContext` for state access
- ✅ Follow SSR patterns with getData()
- ✅ Keep server and client code separated
- ✅ Use function declarations for pages
- ✅ Use arrow functions for reusable components
- ✅ Check response.ok in fetch calls

## Git Practices
- Write clear, descriptive commit messages
- Keep commits atomic and focused
- Use feature branches
- Run linters before committing
- Review your own code first
- Test both client and server builds