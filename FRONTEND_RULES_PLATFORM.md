# Frontend Development Rules - Platform App

## Tech Stack
- React 19.1+ with TypeScript 5.8+
- Vite 6+ for bundling with SWC for fast compilation
- @tanstack/react-router 1.130+ for client-side routing
- @tanstack/react-query 5.83+ for data fetching and caching
- @reatom/core for atomic state management
- Zod 4+ for validation and type inference
- i18next 25+ with react-i18next for internationalization
- SCSS with CSS Modules for styling
- clsx for conditional class names
- @tanstack/react-virtual for virtualization

## Architecture

### Feature-Sliced Design (FSD)
The codebase follows Feature-Sliced Design methodology with strict layer separation:

```
src/
├── app/              # Application initialization, providers, global config
├── pages/            # Route pages with routing groups
├── widgets/          # Complex, self-contained UI blocks
├── features/         # User scenarios and feature logic
├── entities/         # Business entities with model/api/hooks
└── shared/           # Reusable utilities, UI components, config, types
```

### Layer Rules
- **app/**: Application entry point, global providers (QueryClient, Router, i18n), global configuration
- **pages/**: Page components, route-specific logic. Use routing groups with parentheses `(groupName)/`
- **widgets/**: Composed UI blocks (e.g., Betslip, Navigation, SportLines). Can use entities, features, and shared
- **features/**: Isolated feature logic (e.g., favorite-sports, system-calculator). Can use entities and shared
- **entities/**: Business logic and data models. Structure: `entity-name/model/`, `entity-name/api/`, `entity-name/hooks/`
- **shared/**: No imports from other layers. Contains: `ui/`, `hooks/`, `utilities/`, `config/`, `types/`, `store/`, `constants/`

### Import Rules
```typescript
// ✅ Correct: Import from lower layers
// In widgets:
import { SportIcon, Button } from '@/shared';
import { selectedOutcomesStore } from '@/entities/Outcome';
import { updateEventsCoefficients } from '@/features/events';

// ❌ Wrong: Never import from same or higher layers
// In entities: ❌ import from widgets or features
// In shared: ❌ import from any other layer
```

## Code Style

### TypeScript
- Use TypeScript strict mode (extends `@rtdlab/ts-config/frontend`)
- Use explicit return types for all functions
- Avoid `any`, use `unknown` when type is truly unknown
- Use `type` for unions/intersections, `interface` for object shapes
- Define interfaces for all component props named `Properties`
- Use type imports: `import type { FC, ReactNode } from 'react'`
- Place types in dedicated `types.ts` or `/types` directory
- Use Zod for runtime validation and type inference with `z.infer<typeof schema>`
- Use path alias `@/` for all imports from `src/`

```typescript
// ✅ Good
import type { FC } from 'react';
import type { ButtonProperties } from './types';

export const Component: FC<Properties> = ({ prop }) => {
  const result: string = transform(prop);
  return <div>{result}</div>;
};

// ❌ Bad
import { FC } from 'react'; // Don't import types as values
export const Component = ({ prop }: any) => { // Never use any
  const result = transform(prop); // Missing type annotation
  return <div>{result}</div>;
};
```

### React
- Use functional components with hooks exclusively
- Prefer named exports: `export const ComponentName: FC = () => {}`
- Use `forwardRef` when component needs to expose a ref
- Keep components small and focused (< 200 lines)
- Extract custom hooks for reusable logic with `use` prefix
- Always use `FC` or explicit prop types via `Properties` interface
- Use `useMemo` for expensive computations and derived state
- Use `useCallback` for functions passed to memoized children
- Always provide `displayName` for components created with `forwardRef`

```typescript
// ✅ Component with props
import type { FC, ReactNode } from 'react';
import clsx from 'clsx';
import styles from './Component.module.scss';

interface Properties {
  children: ReactNode;
  isActive?: boolean;
  variant?: 'primary' | 'secondary';
}

export const Component: FC<Properties> = ({ 
  children, 
  isActive = false,
  variant = 'primary' 
}) => {
  return (
    <div className={clsx(styles.wrapper, styles[variant], isActive && styles.active)}>
      {children}
    </div>
  );
};

// ✅ Component with forwardRef
import { forwardRef } from 'react';

export const Button = forwardRef<HTMLButtonElement, ButtonProperties>(
  ({ children, ...rest }, ref) => {
    return (
      <button ref={ref} {...rest}>
        {children}
      </button>
    );
  }
);

Button.displayName = 'Button';
```

### Naming Conventions
- **Components**: PascalCase files and exports (e.g., `Button.tsx`, `SportIcon.tsx`)
- **Pages**: PascalCase with page suffix (e.g., `SportsPage.tsx`)
- **Routing groups**: Use parentheses `(groupName)/` for route organization
- **Styles**: `ComponentName.module.scss` co-located with component
- **Hooks**: camelCase with `use` prefix (e.g., `useDebounce.ts`, `useElementSize.ts`)
- **Utilities**: camelCase files and exports (e.g., `dateLocalString.ts`, `parseFromStorage.ts`)
- **Stores**: camelCase with `Store` suffix (e.g., `globalConfiguration`, `betslipStore`)
- **Types**: camelCase files (e.g., `types.ts`, `event.ts`, `competitor.ts`)
- **Constants**: UPPER_SNAKE_CASE for values, kebab-case for files (e.g., `betslip-constants.ts`)
- **Props interface**: Always name it `Properties`
- **Boolean props/variables**: use `is`, `has`, `should` prefix (e.g., `isActive`, `hasError`)

### File Organization

#### Entity Structure
```
entities/
└── EntityName/
    ├── index.ts           # Public API exports
    ├── model/             # State, stores, types
    │   ├── entity-store.ts
    │   ├── entity-constants.ts
    │   ├── types.ts
    │   └── index.ts
    ├── api/               # API calls
    │   ├── use-fetch-entity.ts
    │   └── index.ts
    ├── hooks/             # Entity-specific hooks
    │   └── use-entity-logic.ts
    └── utilities.ts       # Entity-specific utilities
```

#### Widget Structure
```
widgets/
└── WidgetName/
    ├── index.ts
    ├── WidgetName.tsx
    ├── WidgetName.module.scss
    ├── components/        # Widget-internal components
    │   ├── SubComponent/
    │   │   ├── index.ts
    │   │   ├── SubComponent.tsx
    │   │   └── SubComponent.module.scss
    │   └── index.ts
    └── constants.tsx      # Widget-specific constants
```

#### Shared UI Component Structure
```
shared/ui/
└── ComponentName/
    ├── index.ts                    # Clean exports
    ├── ComponentName.tsx           # Component implementation
    ├── ComponentName.module.scss   # Styles
    └── types.ts                    # Component-specific types (optional)
```

#### Component Export Pattern
```typescript
// ComponentName/ComponentName.tsx
export const ComponentName: FC<Properties> = () => { ... };
export type { Properties as ComponentNameProperties };

// ComponentName/index.ts
export { ComponentName } from './ComponentName';
export type { ComponentNameProperties } from './ComponentName';
```

## Best Practices

### Performance
- Use `React.memo()` for expensive pure components
- Implement virtualization with `@tanstack/react-virtual` for long lists
- Use `useMemo` for expensive computations
- Use `useCallback` for stable function references in dependencies
- Lazy load routes with React.lazy and Suspense
- Use SimpleBar for custom scrollbars with performance optimization

### State Management
- Use **@reatom/core** for global state with atoms
- Define atoms with descriptive names and optional labels: `atom(initialValue, 'atomLabel')`
- Use `.actions()` for derived getters and mutations
- Use `.subscribe()` for side effects (e.g., localStorage sync)
- Use `useState` for local component state
- Never store derived state - compute it with `useMemo`
- Keep state as close to where it's used as possible
- For complex form state, consider react-hook-form

```typescript
// ✅ Reatom store pattern
import { atom } from '@reatom/core';
import { z } from 'zod';

const schema = z.object({
  count: z.number(),
  name: z.string(),
});

type State = z.infer<typeof schema>;

export const myStore = atom<State>(
  { count: 0, name: '' },
  'myStore'
).actions((target) => ({
  increment: () => target((state) => ({ ...state, count: state.count + 1 })),
  setName: (name: string) => target((state) => ({ ...state, name })),
}));

// Subscribe for side effects
myStore.subscribe((state) => {
  localStorage.setItem('myStore', JSON.stringify(state));
});

// ✅ Usage in component
import { useAtom } from '@reatom/react';

export const Component: FC = () => {
  const [state, actions] = useAtom(myStore);
  
  return (
    <button onClick={actions.increment}>
      Count: {state.count}
    </button>
  );
};
```

### Data Fetching
- Use **@tanstack/react-query** for all API calls
- Define query keys as constants: `const QUERY_KEYS = { users: 'users' }`
- Use `useSuspenseQuery` for critical data with Suspense boundaries
- Use `useQuery` for optional data with loading states
- Implement proper error boundaries
- Use React Query devtools in development
- Return typed responses from API functions
- Handle errors gracefully with try-catch

```typescript
// ✅ API function pattern
export const fetchSportStructure = async (
  params: FetchParams
): Promise<SportStructure | undefined> => {
  try {
    const response = await fetch(`${params.baseUrl}/structure`, {
      headers: { Authorization: `Bearer ${params.token}` },
    });
    
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    
    return await response.json() as SportStructure;
  } catch (error) {
    console.error('Failed to fetch sport structure:', error);
    return undefined;
  }
};

// ✅ Query hook pattern
export const useSportStructure = () => {
  return useQuery({
    queryKey: ['sportStructure'],
    queryFn: () => fetchSportStructure({ baseUrl, token }),
    staleTime: 5 * 60 * 1000, // 5 minutes
  });
};
```

### Forms
- Use `react-hook-form` for complex forms with multiple fields
- Validate with Zod schemas using integration
- Show inline validation errors
- Disable submit during submission
- Use `register` pattern for form fields
- Provide clear success/error feedback

### Internationalization
- Use i18next with react-i18next
- Create namespaced translation hooks in `shared/hooks/`
- Define namespace keys with TypeScript for type safety
- Load translations asynchronously
- Use translation keys with proper namespacing: `t('common:buttonLabel')`

```typescript
// ✅ Translation hook pattern
import { useTranslation } from 'react-i18next';
import type { NamespaceKeys } from '../config/i18nConfig';

const useNamespacedTranslation = <Namespace extends NamespaceKeys>(
  namespace: Namespace
) => {
  const { t, i18n, ready } = useTranslation(namespace);
  return { t, i18n, ready };
};

export const useBetslipTranslation = () => useNamespacedTranslation('betslip');

// ✅ Usage
const { t } = useBetslipTranslation();
return <button>{t('submitBet')}</button>;
```

### Routing
- Use `@tanstack/react-router` for type-safe routing
- Define routes in `shared/config/routerConfig/`
- Use routing groups with parentheses for organization: `(sports)/`, `(dashboard)/`
- Access route params with `useParams({ strict: false })`
- Use contexts for sharing data across route tree
- Implement proper 404 page in `pages/notFound/`

### Styling
- Use **SCSS with CSS Modules** exclusively
- File naming: `ComponentName.module.scss`
- Import styles: `import styles from './Component.module.scss'`
- Use `clsx` for conditional class names
- Define global styles in `app/ui/global.scss`
- Use SCSS variables in `shared/styles/variables.scss`
- Responsive breakpoints: use mixins from `shared/styles/resp.scss`
- Keep styles co-located with components
- Never use inline styles except for dynamic values (e.g., dimensions)

```scss
// ✅ SCSS Module pattern
@import '@/shared/styles/variables';

.wrapper {
  display: flex;
  padding: var(--spacing-md);
  
  &.active {
    background-color: var(--color-primary);
  }
  
  @include resp(tablet) {
    padding: var(--spacing-lg);
  }
}

.button {
  &Primary {
    background: var(--color-primary);
  }
  
  &Secondary {
    background: var(--color-secondary);
  }
}
```

```typescript
// ✅ Usage in component
import clsx from 'clsx';
import styles from './Component.module.scss';

export const Component: FC<Properties> = ({ isActive, variant }) => {
  return (
    <div className={clsx(
      styles.wrapper,
      isActive && styles.active
    )}>
      <button className={styles[`button${variant}`]}>
        Click me
      </button>
    </div>
  );
};
```

### Accessibility
- Use semantic HTML elements (`<button>`, `<nav>`, `<main>`, `<section>`)
- Include proper ARIA labels (`aria-label`, `aria-labelledby`)
- Ensure keyboard navigation works
- Provide alternative text for images
- Maintain proper heading hierarchy (h1 → h2 → h3)
- Use proper color contrast ratios (WCAG AA minimum)
- Test with keyboard-only navigation

## Code Quality

### Error Handling
- Implement Error Boundaries for component errors
- Use try-catch for all async operations
- Log errors with context: `console.error('Context:', error)`
- Show user-friendly error messages
- Return `undefined` from API functions on errors (never throw)
- Provide recovery actions when possible

### Type Safety
- Type everything explicitly in TypeScript
- Use Zod schemas for runtime validation
- Infer types from Zod schemas: `type User = z.infer<typeof userSchema>`
- Use path alias `@/` for all imports
- Define interfaces in `/types` or `types.ts` files
- Use `import type` for type-only imports
- Leverage type inference from React Query
- Avoid type assertions (`as`) when possible - prefer type guards

### Comments
- Write self-documenting code with clear names
- Use JSDoc for public APIs and complex functions
- Explain "why", not "what"
- Add TODO comments with context and owner
- Document complex algorithms and business logic
- Keep comments up to date with code changes
- Remove commented-out code before committing

### Project-Specific Patterns

#### Reatom Atom Pattern
```typescript
import { atom } from '@reatom/core';
import { z } from 'zod';

const schema = z.object({ value: z.string() });
type State = z.infer<typeof schema>;

export const myAtom = atom<State>(
  { value: '' },
  'myAtomLabel'
).actions((target) => ({
  setValue: (value: string) => 
    target((state) => ({ ...state, value })),
  reset: () => 
    target({ value: '' }),
}));
```

#### Query Hook Pattern
```typescript
import { useQuery, useSuspenseQuery } from '@tanstack/react-query';

// For optional data
export const useOptionalData = () => {
  return useQuery({
    queryKey: ['data'],
    queryFn: fetchData,
    staleTime: 5 * 60 * 1000,
  });
};

// For critical data with Suspense
export const useRequiredData = () => {
  return useSuspenseQuery({
    queryKey: ['data'],
    queryFn: fetchData,
  });
};
```

#### Component with Context Pattern
```typescript
import { useContext } from 'react';
import type { FC } from 'react';

import { MyContext } from '@/shared/contexts';

export const Component: FC = () => {
  const contextData = useContext(MyContext);
  
  // Use context data
  return <div>{contextData.value}</div>;
};
```

## Build & Development

### Scripts
- `pnpm dev` - Development server with hot reload
- `pnpm build` - Production build with type checking
- `pnpm preview` - Preview production build
- `pnpm lint` - ESLint check
- `pnpm stylelint` - SCSS linting
- `pnpm typecheck` - TypeScript validation without emit

### Configuration
- Use workspace shared configs (`@rtdlab/eslint-config`, `@rtdlab/ts-config`, `@rtdlab/stylelint`)
- Configure path alias `@/` in both `vite.config.ts` and `tsconfig.json`
- Use Vite for fast builds and HMR
- Configure SCSS with global imports via `additionalData`
- Use vite-plugin-svgr for importing SVGs as React components
- Enable gzip compression with vite-plugin-compression

## Don't
❌ Use `var` - always use `const` or `let`  
❌ Import from higher FSD layers (e.g., entities importing from widgets)  
❌ Import from same FSD layer  
❌ Store derived state - compute it with `useMemo`  
❌ Use index as key in lists - use stable unique IDs  
❌ Forget to cleanup effects and subscriptions  
❌ Create massive components (split into smaller ones)  
❌ Ignore TypeScript errors  
❌ Skip error handling in async functions  
❌ Commit console.logs to production  
❌ Use inline styles (except for dynamic values)  
❌ Mix server and client logic  
❌ Forget to export from `index.ts`  
❌ Use anonymous exports  
❌ Import types as values  
❌ Mutate state directly in Reatom actions  

## Always
✅ Type everything in TypeScript with explicit return types  
✅ Use FSD architecture and respect layer boundaries  
✅ Handle loading and error states in components  
✅ Use CSS Modules (`.module.scss`) for all styling  
✅ Export components from `index.ts` for clean imports  
✅ Co-locate styles and types with components  
✅ Use path alias `@/` for all imports  
✅ Name props interface `Properties`  
✅ Use `clsx` for conditional class names  
✅ Validate with Zod schemas  
✅ Return `undefined` from API errors  
✅ Use `useAtom` from @reatom/react for atom consumption  
✅ Use React Query for all data fetching  
✅ Implement proper TypeScript strict mode  
✅ Use i18next for all user-facing text  
✅ Provide displayName for forwardRef components  
✅ Use `import type` for type-only imports  
✅ Keep components focused and under 200 lines  
✅ Write accessible HTML with semantic elements  
✅ Test both client and type checking before committing  

## Git Practices
- Write clear, descriptive commit messages
- Keep commits atomic and focused on single concern
- Use feature branches for new development
- Run linters and type checking before committing
- Review your own code first before requesting reviews
- Test in browser before pushing

