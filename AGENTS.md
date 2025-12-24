# AGENTS.md: Instructions for Building the Web Component Flow Library

This document provides guidance for an AI agent to implement the Web Component-based flow library as specified in `TODO.md`.

## 1. Project Structure

Organize the repository as follows:

```
/
├── components/
│   ├── flow-graph.js
│   ├── flow-node.js
│   ├── flow-edge.js
│   ├── flow-minimap.js
│   ├── flow-controls.js
│   └── flow-background.js
├── styles/
│   ├── main.css
│   └── theme.css
├── utils/
│   ├── d3-drag-wrapper.js
│   ├── d3-zoom-wrapper.js
│   └── state-manager.js
├── examples/
│   ├── index.html
│   └── main.js
├── tests/
│   └── playwright/
│       └── *.spec.js
├── TODO.md
├── AGENTS.md
└── package.json
```

## 2. Coding Conventions

### Web Components
-   **Naming:** Use custom element names with a prefix, e.g., `<flow-graph>`, `<flow-node>`. The filename should match the component name (e.g., `flow-graph.js` defines `<flow-graph>`).
-   **Modularity:** Each component should be in its own file.
-   **API:** Use attributes for configuration and custom events for communication.
-   **Styling:** Use a Shadow DOM for encapsulation. Define styles in a `<style>` tag within the component's template. Use CSS Custom Properties for theming, defined in `styles/theme.css`.

### JavaScript
-   **ES Modules:** Use ES Modules (`import`/`export`) for all JavaScript files.
-   **No Build Step:** Write code that can run directly in modern browsers without a build or transpilation step.
-   **Formatting:** Use Prettier for consistent code formatting.

## 3. Tooling

### Development
-   **Web Server:** Use a simple, no-configuration web server for local development. The `web-dev-server` is a good choice. Add it as a dev dependency in `package.json`.
-   **Testing:** Use Playwright for end-to-end testing. Tests should cover all major user interactions and verify that components render correctly.

## 4. Dependencies

-   **D3:** The original Reactflow library uses `d3-zoom` and `d3-drag`. For this project, you should create thin wrapper modules around these libraries (`d3-drag-wrapper.js`, `d3-zoom-wrapper.js`) to manage them as dependencies. This avoids re-implementing complex zoom and drag logic from scratch.

## 5. Programmatic Checks

After implementing the core components and features, you must write and run a series of programmatic checks to verify the implementation. These checks should be implemented as Playwright tests.

### Verification Script (`tests/playwright/verify.spec.js`)
-   **Test 1: Core Rendering:**
    -   Verify that the `<flow-graph>` component renders without errors.
    -   Verify that nodes and edges are rendered correctly within the graph.
-   **Test 2: Interaction:**
    -   Verify that zooming and panning work as expected.
    -   Verify that nodes can be dragged and selected.
-   **Test 3: Events:**
    -   Verify that custom events (`node-click`, `connect`, etc.) are dispatched correctly.
-   **Test 4: API:**
    -   Verify that the programmatic API (`fitView()`, `zoomTo()`) works as expected.

You must run these tests and ensure they pass before submitting the final implementation.
