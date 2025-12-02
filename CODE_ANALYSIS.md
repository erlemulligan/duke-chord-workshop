# Codebase Analysis: Project Structure Overview

This document provides an overview of the "Duke & Chord Music" application's project structure, detailing the purpose of major directories, key files, and identified architectural patterns.

## 1. Overall Project Structure

The project follows a modular and component-based structure, typical for a Single Page Application (SPA) built with JavaScript. The separation of concerns is evident across directories for front-end assets (HTML, CSS, JS, audio, images), API data, and configuration files.

## 2. Major Directories and their Purpose

*   [`api/`](api/):
    *   **Purpose**: Contains data for the mock REST API.
    *   **Key File**: [`database.json`](api/database.json) serves as the data store for `json-server`, simulating a backend database for users, instruments, and classes.
*   [`prompts/`](prompts/):
    *   **Purpose**: Stores various prompt libraries for AI-assisted development, categorized by use-case (best practices, code analysis, debugging, feature addition). These are reference files for guiding AI interactions.
    *   **Key Files**:
        *   [`ai_development_best_practices_prompts.md`](prompts/ai_development_best_practices_prompts.md)
        *   [`code_analysis_prompts.md`](prompts/code_analysis_prompts.md)
        *   [`debugging_and_refactoring_prompts.md`](prompts/debugging_and_refactoring_prompts.md)
        *   [`feature_addition_prompts.md`](prompts/feature_addition_prompts.md)
*   [`src/`](src/):
    *   **Purpose**: Houses all front-end source code and assets for the Single Page Application.
    *   **Subdirectories**:
        *   [`src/audio/`](src/audio/): Contains audio samples for various instruments, used for previews in the marketplace.
        *   [`src/images/`](src/images/): Stores image assets, including instrument pictures and UI elements.
        *   [`src/scripts/`](src/scripts/): The core JavaScript logic for the application, further divided into functional modules:
            *   [`src/scripts/auth/`](src/scripts/auth/): Handles user authentication (login, registration).
            *   [`src/scripts/classes/`](src/scripts/classes/): Manages music class-related components and logic.
            *   [`src/scripts/data/`](src/scripts/data/): Contains custom state management modules. These are critical for the application's functionality.
            *   [`src/scripts/employees/`](src/scripts/employees/): Manages employee-related components (e.g., directory).
            *   [`src/scripts/instruments/`](src/scripts/instruments/): Manages instrument-related components (lists, details, forms).
            *   [`src/scripts/nav/`](src/scripts/nav/): Contains components related to application navigation (header, navbar).
        *   [`src/styles/`](src/styles/): Contains all CSS stylesheets, organized by component or view.

## 3. Key Files and their Role (at Root and within `src/`)

*   [`README.md`](README.md): Provides a comprehensive overview of the project, including its purpose, features, architecture, and instructions for setup and running.
*   [`PROJECT_NOTES.md`](PROJECT_NOTES.md): A document for internal project notes, learnings, challenges, and reflections on AI assistance.
*   [`package.json`](package.json) / [`package-lock.json`](package-lock.json): Node.js project configuration and dependency management files.
*   [`server.js`](server.js): The custom Node.js server that handles both static file serving for the front-end and proxies API requests to `json-server`. This is the primary entry point for running the application with `npm start`.
*   [`src/index.html`](src/index.html): The main entry point of the Single Page Application, where all JavaScript and CSS are loaded.
*   [`src/scripts/main.js`](src/scripts/main.js): Likely the primary JavaScript file that initializes the application, sets up event listeners, and manages the initial rendering based on the `ViewStateManager`.
*   [`src/scripts/DukeChord.js`](src/scripts/DukeChord.js): Given the project name, this file likely serves as the main application component or orchestrator for rendering different views based on the `ViewStateManager`.
*   [`src/scripts/Home.js`](src/scripts/Home.js): The component responsible for rendering the home view of the application.

## 4. Architectural Patterns Identified

*   **Single Page Application (SPA)**: The application is designed as an SPA with client-side routing managed through URL query parameters (e.g., `?view=store`). This allows for dynamic content loading without full page reloads.
*   **Custom State Management**: The application utilizes a custom, event-driven state management system. Dedicated "StateManager" modules ([`UserStateManager.js`](src/scripts/data/UserStateManager.js), [`InstrumentsStateManager.js`](src/scripts/data/InstrumentsStateManager.js), [`ClassStateManager.js`](src/scripts/data/ClassStateManager.js), [`ViewStateManager.js`](src/scripts/data/ViewStateManager.js)) manage specific data domains. State changes dispatch custom `stateChanged` events, which components listen to for re-rendering.
*   **Component-Based Architecture**: UI is composed of individual JavaScript modules that render HTML strings, handle their own events, and interact with the state management system. This promotes modularity and reusability.
*   **Mock API / JSON-Server Backend**: For development and demonstration, `json-server` is used as a mock REST API. This allows the front-end to interact with a simulated backend with full CRUD capabilities without needing a complex server-side implementation.
*   **Modular JavaScript**: The [`src/scripts/`](src/scripts/) directory is highly modular, with subdirectories organizing code by feature or concern (e.g., `auth`, `classes`, `instruments`, `nav`, `data`).