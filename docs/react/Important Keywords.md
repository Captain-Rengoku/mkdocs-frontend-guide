---
date: 
  created: 2025-02-08
---

# React Ecosystem – Comprehensive Keywords List

## React Core Concepts

### 1.1 Virtual DOM & Rendering

**Virtual DOM** – A lightweight copy of the real DOM that React updates efficiently.

**Diffing Algorithm** – Compares Virtual DOM trees to identify changes.

**Reconciliation** – Process of updating the real DOM based on Virtual DOM changes.

**React Fiber** – React's reconciliation engine for incremental, interruptible rendering (shipped in React 16).

**Hydration** – Merging server-rendered HTML with client-side React.

**React Concurrent Features / Rendering** – Lets React work on rendering updates without blocking the main thread. (The experimental "Concurrent Mode" name was dropped; React 18 ships these as opt-in concurrent features via `createRoot`, `startTransition`, etc.)

**Asynchronous Rendering** – React prioritizes UI updates for a smoother user experience.

### 1.2 Component-Based Architecture

**Functional Components** – Components that use functions instead of classes.

**Class Components** – Components defined using ES6 classes with lifecycle methods.

**Stateless Components** – Components that do not manage their own state.

**Stateful Components** – Components that hold and manage state.

**Higher-Order Components (HOC)** – Functions that take a component and return an enhanced version.

**Controlled Components** – Form elements whose state is controlled by React.

**Uncontrolled Components** – Form elements that store their state in the DOM.

### 1.3 Component Lifecycle (Class Components)

Mounting Phase
**constructor** – Initializes state and binds methods.

**componentDidMount** – Runs after the component is added to the DOM.

Updating Phase
**shouldComponentUpdate** – Determines whether a re-render is needed.

**componentDidUpdate** – Runs after a component updates.

**getDerivedStateFromProps** – Updates state based on props before re-render.

**getSnapshotBeforeUpdate** – Captures the previous DOM state before updates.

Unmounting Phase
**componentWillUnmount** – Cleanup operations like event listeners or timers.

Error Handling
**Error Boundaries** – Special components that catch UI errors.

## React Hooks (Function Components Lifecycle)

### 2.1 Basic Hooks

**useState** – Manages component-level state.

**useEffect** – Runs side effects like fetching data or subscriptions.

**useContext** – Accesses global values without prop drilling.

### 2.2 Performance Optimization Hooks

**useMemo** – Caches computed values to prevent unnecessary calculations.

**useCallback** – Caches functions to prevent re-renders.

**React.memo** – Prevents unnecessary re-renders of functional components.

### 2.3 Advanced Hooks

**useReducer** – Manages complex state logic using a reducer function.

**useRef** – Creates a reference to store mutable values without triggering re-renders.

**useLayoutEffect** – Runs synchronously after all DOM updates.

### 2.4 Concurrent Rendering Hooks

**useTransition** – Defers updates for better responsiveness.

**useDeferredValue** – Postpones non-urgent value updates.

**useId** – Generates unique IDs for accessibility.

## React Performance Optimization

### 3.1 Rendering Optimizations

**Event Delegation** – Uses a single event listener for multiple child elements.

**Lazy Loading** – Loads components only when needed (React.lazy).

**Code Splitting** – Divides code into smaller chunks to improve load times.

**Tree Shaking** – Removes unused JavaScript code for optimization.

### 3.2 Avoiding Re-renders

**React.memo** – Prevents re-rendering if props remain the same.

**useMemo** – Avoids re-computation of expensive calculations.

**useCallback** – Prevents function recreation on every render.

**shouldComponentUpdate** – Controls whether a component should re-render.

### 3.3 Browser Rendering Optimizations

**Repaints** – Redrawing visible elements when styles change.

**Reflows** – Layout recalculations when elements change position.

**Virtualization** – Renders only visible elements to improve performance.

## React State Management

### 4.1 React Built-in State Management

**useState** – Local state within a component.

**useReducer** – Manages complex state changes.

**useContext** – Shares state globally across components.

### 4.2 Redux (External State Management)

Core Concepts
**Redux Store** – Centralized state container.

**Actions** – Describe state changes.

**Reducers** – Pure functions that take the current state and an action and return a **new** state (they never mutate the existing state).

**Dispatch** – Sends actions to the reducer.

**Selectors** – Extracts specific data from the Redux store.

Middleware & Enhancers
**Redux Thunk** – Handles async operations in Redux.

**Redux Saga** – Uses generator functions for managing side effects.

**Redux Logger** – Logs dispatched actions and state changes.

Redux Toolkit (RTK)
**createSlice** – Combines reducers and actions in a single function.

**createAsyncThunk** – Simplifies async logic in Redux.

**configureStore** – Sets up a Redux store with default middleware.

### 4.3 Context API

**React Context** – Shares state without prop drilling.

**Provider & Consumer** – Provides and consumes shared state.

### 4.4 Other State Management Libraries

**Zustand** – Simple, minimalistic state management.

**Recoil** – An atom-based state management library from Meta. Note: it was archived (deprecated) by Meta in 2025; consider Jotai, Zustand, or Redux Toolkit instead.

**Jotai** – Atom-based state management.

**MobX** – Reactive state management with observables.

## React Routing (React Router)

### 5.1 Routing Essentials

**BrowserRouter** – Enables routing in React apps.

**HashRouter** – Uses URL hash for routing.

**MemoryRouter** – Stores routes in memory (useful for testing).

**StaticRouter** – Predefined routes for server-side rendering.

### 5.2 Navigation

**Route** – Defines a route and its component.

**Link & NavLink** – Navigates between routes.

**Redirect** – Redirects to another route. (This is the React Router **v5** API; in **v6+** use the `<Navigate />` component, or `redirect()` inside loaders/actions.)

**useNavigate** – Programmatically navigates users.

### 5.3 Dynamic Routing

**useParams** – Retrieves URL parameters.

**useLocation** – Gets the current URL path.

## Next.js (React Framework)

### 6.1 Rendering Strategies

**SSR (Server-Side Rendering)** – Fetches and renders pages on the server per request.

**CSR (Client-Side Rendering)** – Renders content dynamically in the browser.

**SSG (Static Site Generation)** – Pre-builds pages for performance.

**ISR (Incremental Static Regeneration)** – Updates static pages without full re-builds.

### 6.2 Data Fetching

**getServerSideProps** – Fetches data on each request (SSR).

**getStaticProps** – Fetches data at build time (SSG).

**getStaticPaths** – Generates dynamic paths for static pages.

### 6.3 API Routes

**API Middleware** – Runs logic before serving requests.

**Middleware Functions** – Handles authentication and logging.

## React Forms & User Input Handling

### 7.1 Controlled Components

**onChange Event** – Updates state whenever an input value changes.

**value Attribute** – Controls the input field value using state.

### 7.2 Uncontrolled Components

**useRef for Form Handling** – Directly accesses form elements without React state.

### 7.3 Form Libraries

**React Hook Form** – Lightweight form library with built-in validation.

**Formik** – Form management library with validation support.

**Yup** – Schema validation library for form data.

## React APIs for UI Enhancements

### 8.1 Context API

**React.createContext** – Creates a shared context for global state.

**useContext** – Consumes context data in functional components.

### 8.2 Portals

**ReactDOM.createPortal** – Renders child components outside the parent hierarchy (useful for modals).

### 8.3 Suspense & Lazy Loading

**React.lazy** – Loads components dynamically when needed.

**Suspense** – Displays fallback UI while a component is loading.

**Fallback UI** – A loading indicator or placeholder displayed during component fetch.

### 8.4 Fragments (< >...</ >)

**Shorthand Fragment** – Groups multiple elements without adding an extra DOM node.

## React UI Libraries & Tools

### 9.1 UI Component Libraries

**Material UI** – A popular React UI framework with ready-made components.

**Ant Design** – Enterprise-level UI design framework for React.

**Chakra UI** – A flexible and accessible component library.

**Tailwind CSS** – Utility-first CSS framework for styling React components.

**Bootstrap** – CSS framework with React support for responsive design.

### 9.2 State & Data Handling

**Apollo Client (GraphQL)** – Manages state with GraphQL queries and mutations.

**SWR (Stale-While-Revalidate)** – Fetches, caches, and revalidates data automatically.

**React Query** – Data-fetching and state management library for asynchronous operations.

### 9.3 Testing in React

**Jest** – JavaScript testing framework for unit and integration testing.

**React Testing Library** – Utility for testing React components in a real-world scenario.

**Cypress** – End-to-end testing framework for React applications.

## Advanced React Concepts

### 10.1 Server-Side Rendering (SSR) vs Client-Side Rendering (CSR)

**Server Components** – Components that render on the server and do not require client-side JavaScript.

**Client Components** – Components that execute in the browser and handle user interactions.

**Hydration** – Process of attaching event handlers to server-rendered HTML.

### 10.2 React Concurrent Rendering Features

**Time-Slicing** – Breaks rendering tasks into small chunks to improve responsiveness.

**Suspense for Data Fetching** – Handles asynchronous data fetching with fallback UI.

### 10.3 Deployment & Optimization

**Webpack** – Bundles JavaScript files for production.

**Babel** – Transpiles modern JavaScript (ES6+) to older browser-compatible versions.

**Code Minification** – Removes unnecessary characters to reduce file size and improve performance.

## Miscellaneous React Concepts

### 11.1 Event Handling

**Synthetic Events** – React’s wrapper around native browser events for cross-browser compatibility.

**Event Pooling** – A legacy optimization where React reused synthetic event objects. **Removed in React 17**, so events are no longer nullified and `event.persist()` is now a no-op.

**Event Delegation** – Uses a single event listener to manage multiple child events.

### 11.2 Render Props Pattern

**Render Props** – Passes a function as a prop to share logic between components.

### 11.3 Prop Drilling vs Context API

**Prop Drilling** – Passing props through multiple nested components.

**Context API** – Avoids prop drilling by providing global state management.

### 11.4 Web Components & React

**Custom Elements** – HTML elements that can be used inside React components.

**Shadow DOM** – Encapsulates styles and structure in web components.

## Important React Development Patterns

### 12.1 Higher-Order Components (HOC)

**Definition** – A function that takes a component and returns an enhanced version.

**Example** – Used for authentication, logging, or modifying props dynamically.

### 12.2 Compound Components Pattern

**Definition** – A pattern where multiple components work together (e.g., a Tabs component).

### 12.3 Render Props Pattern

**Definition** – Uses a function prop to share logic across multiple components.

### 12.4 Controlled vs Uncontrolled Components

**Controlled Components** – Form inputs controlled by React state.

**Uncontrolled Components** – Form inputs controlled by the DOM using refs.

## Progressive Web Apps (PWA) in React

### 13.1 PWA Features in React

**Service Workers** – Caches files for offline usage.

**Web App Manifest** – Defines metadata like app name, icons, and colors.

**IndexedDB & Cache API** – Stores data in the browser for offline access.

### 13.2 React Libraries for PWA

**Workbox** – Simplifies service worker implementation.

**Next.js PWA Plugin** – Adds PWA support to Next.js projects.

## Security & Authentication in React

### 14.1 Common Security Best Practices

**Cross-Site Scripting (XSS) Prevention** – Avoids injecting malicious scripts into the app.

**Cross-Site Request Forgery (CSRF) Protection** – Prevents unauthorized actions on behalf of a user.

**Content Security Policy (CSP)** – Restricts script execution to prevent XSS attacks.

### 14.2 Authentication & Authorization

**JWT (JSON Web Token)** – Token-based authentication system.

**OAuth** – Secure authentication standard using third-party providers (Google, Facebook, GitHub).

**Firebase Authentication** – Google’s authentication solution for React apps.

**Auth0** – Authentication-as-a-service provider for React applications.

## React Native (For Mobile Development)

### 15.1 Core React Native Components

**View** – Equivalent to < div> in web applications.

**Text** – Renders text elements (like < p>).

**ScrollView** – Enables scrolling content.

**FlatList** – Optimized for rendering long lists.

### 15.2 React Native APIs

**AsyncStorage** – Local storage API for persisting data.

**Camera & Location APIs** – Accessing device hardware features.

**Gesture Handling** – Detecting touch gestures and interactions.

### 15.3 Navigation in React Native

**React Navigation** – Library for routing and navigation in React Native apps.

**Stack Navigator** – Manages screens in a stack-based navigation.

**Drawer Navigator** – Creates side menu navigation.

**Tab Navigator** – Implements bottom tab navigation.
