# Compound Components

The compound component pattern in React is a design approach where multiple, related components work together as a single, cohesive unit, sharing implicit state and logic. This pattern is a powerful way to build flexible, reusable, and maintainable user interfaces by delegating the control of structure to the user, similar to how <select> and <option> tags work in native HTML.

## How it Works

The pattern typically involves:

- **A Parent Component** that manages the core state and behavior.
- **Child Components** that consume and display the state provided by the parent, often using React's Context API to avoid "prop drilling" (passing props down multiple levels).
- **Attaching Child Components** as static properties of the parent component, which provides a clean and intuitive API for developers.

## Benefits

- **Flexibility:** Users can compose, reorder, or omit child components as needed, without the parent component needing to manage a long list of props or conditional logic.
- **Separation of Concerns:** The parent focuses on logic and state management, while children focus on rendering UI elements.
- **Clear API:** The nested structure in the JSX makes the relationship and composition of the components visually clear and easy to understand.
- **Reusability:** Individual child components can be reused elsewhere, and the compound structure itself can be used in different contexts.

---

# Observer Pattern

The **Observer pattern** is a behavioral design pattern used in React for managing state changes across multiple, decoupled components. It allows objects (observers) to subscribe to another object (subject/observable) and get automatically notified when the subject's state changes, which triggers a re-render in React.

## Core Concept

The pattern creates a one-to-many dependency:

- **Subject (Observable):** The object holding the state. It maintains a list of observers and has methods to subscribe, unsubscribe, and notify them of changes.
- **Observer (Subscriber):** The objects/components that want to be notified of state changes. They implement an update method or a callback function.

## Implementation in React

While React's core philosophy is a unidirectional data flow (props from parent to child), the observer pattern is implicitly or explicitly used in several scenarios:

- **State Management Libraries:** Popular libraries like Redux and MobX use the observer pattern. In Redux, the store is the subject, and components use `connect` or hooks to subscribe to specific parts of the state, re-rendering only when that slice of state changes.
- **Browser APIs:** Native browser APIs used in React like `addEventListener` and `IntersectionObserver` are implementations of the pattern.
- **Custom Hooks and External Stores:** You can implement the pattern manually for specific needs, such as synchronizing an external store (like an authentication token manager) with React components using the built-in `useSyncExternalStore` hook.
- **React Query:** This library uses a `MutationObserver` internally to manage and notify components about asynchronous data fetching states.
