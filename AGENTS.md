# AGENTS.md: Instructions for Building the Web Component Flow Library

This document provides guidance for an AI agent to implement the Web Component-based flow library as specified in `TODO.md`.

## 1. Core Principle: Native Browser Implementation

**This is the most important rule:** The component library must be implemented using **only native browser features**.

-   **No 3rd-Party Runtime Libraries:** Do not use any third-party libraries like D3.js, Lit, or any other utility that is not a development tool. All rendering, state management, and interaction logic (zooming, dragging, etc.) must be built from scratch using standard Web APIs (e.g., Pointer Events, CSS Transforms, Custom Events).
-   **Development Tools are Allowed:** You may use `devDependencies` for tooling purposes, such as testing (Playwright), development servers (Vite.js), or formatters (Prettier). These tools are not part of the final component runtime code.

## 2. Project Structure

Organize the repository as follows:

```
/
├── .github/
│   └── workflows/
│       └── ci.yml
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
│   ├── drag-handler.js
│   ├── zoom-handler.js
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

## 3. Coding Conventions

(Unchanged from previous version - emphasizes modularity, Shadow DOM, and ES Modules)

## 4. Tooling and Development

-   **Dev Server:** Use Vite.js as a development server. Configure it in `package.json`.
-   **Testing:** Use Playwright for end-to-end testing.
-   **Formatting:** Use Prettier for consistent code formatting.

## 5. CI/CD and Automation

-   **GitHub Actions:** Implement a CI/CD pipeline using GitHub Actions.
-   **Workflow File:** The workflow should be defined in `.github/workflows/ci.yml`.
-   **Trigger:** The workflow must trigger on every pull request targeting the `main` branch.
-   **Jobs:** The workflow must include a job that:
    1.  Checks out the code.
    2.  Installs dependencies using `npm install`.
    3.  Runs all Playwright tests using `npm test`.
-   **Branch Protection:** The `main` branch must be protected, requiring the CI checks to pass before a pull request can be merged.

## 6. Programmatic Checks

(Unchanged from previous version - requires Playwright tests for rendering, interaction, events, and API)
