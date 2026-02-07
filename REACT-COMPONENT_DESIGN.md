# React Component Design Checklist 
Execute this every time a component is built. 

## 1. Component Responsibility
- [ ] Component has one clear purpose (single UI concern)
- [ ] Name reflects intent, not implementation (e.g., `AssetList`, not `AssetDataFetcher`)
- [ ] Component does not mix unrelated domains or features
- [ ] Heavy logic is extracted into hooks or services

## 2. Data Fetching (`useQuery`)
- [ ] Component owns its own `useQuery` if it renders server data
- [ ] Query key is stable and deterministic
- [ ] Query parameters come from props or atoms, not hardcoded values
- [ ] `enabled` is used when query depends on prerequisites
- [ ] No side effects inside `queryFn`

## 3. Loading, Error, and Empty States
- [ ] Loading state is explicitly handled
- [ ] Error state is explicitly handled
- [ ] Empty or no-data state is explicitly handled
- [ ] UI states are mutually exclusive and readable
- [ ] Skeletons or spinners are used consistently across the app

**Expected flow**
- [ ] loading → error → empty → data

## 4. Jotai Atom Usage
- [ ] Component uses feature-scoped atoms, not global ones by default
- [ ] Atom represents shared UI or domain state (filters, selection, sort)
- [ ] Atom naming is explicit (`assetFilterAtom`, not `filterAtom`)
- [ ] Atom does not directly fetch data
- [ ] Atom updates do not cause unnecessary re-renders

## 5. Store Access (Global State)
- [ ] Global store access is read-only by default
- [ ] Store is used only for cross-feature or app-wide concerns
- [ ] Component does not mutate global store unless clearly justified
- [ ] Store selectors are used instead of pulling entire store objects
- [ ] No business logic lives inside the store selector

## 6. Side Effects (`useEffect`)
- [ ] Effects are minimal and intentional
- [ ] No data fetching inside `useEffect` (use `useQuery` instead)
- [ ] Dependency arrays are complete and correct
- [ ] Effect logic is extracted if it exceeds a few lines

## 7. Rendering and JSX
- [ ] JSX is readable and shallow
- [ ] Conditional rendering is clear and not deeply nested
- [ ] Inline logic is minimal
- [ ] Repeated UI is extracted into subcomponents
- [ ] Component returns early for loading or error states when possible

## 8. Performance
- [ ] `useMemo` and `useCallback` are used only when necessary
- [ ] Derived data is memoized if expensive
- [ ] Component does not re-render due to unrelated atom or store changes
- [ ] Lists have stable and meaningful keys

## 9. Props and API Design
- [ ] Props are minimal and explicit
- [ ] No prop drilling when atom or store is more appropriate
- [ ] Component does not accept unused or passthrough props
- [ ] Callback props have clear naming (`onSelect`, `onSubmit`)

## 10. Error Boundaries and Safety
- [ ] Component is safe to render with `undefined` or `null` data
- [ ] Assumptions about data shape are guarded
- [ ] Error boundary is used at page or feature root when applicable

## 11. Testability
- [ ] Component can be rendered in isolation
- [ ] Data fetching can be mocked
- [ ] UI states (loading, error, empty, data) are testable
- [ ] No hidden dependencies on global state without clear setup

## 12. File and Structure Hygiene
- [ ] Component file stays focused and small
- [ ] Hooks, atoms, and services are colocated by feature
- [ ] Naming and folder structure match the domain language
- [ ] No cross-feature imports without justification

## Quick Review Rule
If you cannot answer **yes** to why the component needs:
- [ ] its own `useQuery`
- [ ] an atom
- [ ] global store access

then it probably should redesign them.
