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

## 4. Application Architecture Reconstruction (for New Developers)

Welcome to Duke & Chord Music! This application is a dynamic web platform for music enthusiasts, combining an instrument marketplace and a music education hub. It's built as a Single Page Application (SPA), meaning the entire app loads once, and content changes dynamically without full page reloads. We achieve this through client-side routing using URL parameters and a custom event-driven state management system.

### Major Layers

1.  **Presentation Layer (UI Components)**:
    *   **Location**: Primarily found within [`src/scripts/`](src/scripts/), organized into subdirectories like [`src/scripts/auth/`](src/scripts/auth/), [`src/scripts/instruments/`](src/scripts/instruments/), [`src/scripts/classes/`](src/scripts/classes/), and [`src/scripts/nav/`](src/scripts/nav/).
    *   **Purpose**: These are JavaScript modules that generate HTML strings to display information to the user. They also contain event listeners to capture user interactions (e.g., clicks, form submissions).
    *   **Examples**: [`Home.js`](src/scripts/Home.js) renders the landing page, [`InstrumentList.js`](src/scripts/instruments/InstrumentList.js) displays available instruments, and [`Login.js`](src/scripts/auth/Login.js) handles user authentication forms.

2.  **Application Logic Layer (State Managers)**:
    *   **Location**: Exclusively within [`src/scripts/data/`](src/scripts/data/).
    *   **Purpose**: This is the heart of our application's business logic and data management. Each `*StateManager.js` file is responsible for a specific domain of data (e.g., users, instruments, classes, application view). They hold the application's state, fetch data from the API, and dispatch custom events when their state changes.
    *   **Examples**:
        *   [`UserStateManager.js`](src/scripts/data/UserStateManager.js): Manages user login, registration, and user data.
        *   [`InstrumentsStateManager.js`](src/scripts/data/InstrumentsStateManager.js): Handles instrument data, including fetching from the API and filtering logic.
        *   [`ViewStateManager.js`](src/scripts/data/ViewStateManager.js): Controls which "view" (e.g., 'store', 'classes', 'login') is currently displayed to the user based on URL parameters.

3.  **Data Access Layer (API Integration)**:
    *   **Location**: While direct API calls are encapsulated within the State Managers, the data source is in [`api/database.json`](api/database.json), and the API server itself is typically run via `json-server` (either directly or proxied through [`server.js`](server.js)).
    *   **Purpose**: State Managers communicate with our mock REST API (powered by `json-server`) to perform CRUD (Create, Read, Update, Delete) operations on users, instruments, and classes.
    *   **Note**: For development, [`server.js`](server.js) acts as a custom Node.js server that serves our front-end files and proxies requests to `json-server`, simplifying the setup.

### Data Flow and Component Interaction

The application uses an event-driven architecture for data flow:

1.  **User Interaction**: A user performs an action (e.g., clicks a button, submits a form) in a UI component.
2.  **Component Event Handler**: The UI component's event listener captures this action.
3.  **State Manager Update**: The component's event handler calls a method on the relevant `*StateManager` to update the application's state or fetch new data.
4.  **`stateChanged` Event Dispatch**: After the `*StateManager` updates its internal state (and potentially interacts with the API), it dispatches a custom `stateChanged` event (e.g., `dispatchEvent(new CustomEvent("stateChanged"))`).
5.  **Component Re-rendering**: Other UI components that are listening for this `stateChanged` event react by re-rendering themselves to reflect the updated data. This ensures the UI is always in sync with the application's state.

**Example Data Flow (Viewing Instruments):**

*   User clicks "Instruments" on the navigation bar.
*   [`NavBar.js`](src/scripts/nav/NavBar.js) event handler updates [`ViewStateManager.js`](src/scripts/data/ViewStateManager.js) to set the current view to 'store'.
*   `ViewStateManager` dispatches a `stateChanged` event.
*   The main application component ([`DukeChord.js`](src/scripts/DukeChord.js) or [`main.js`](src/scripts/main.js)) listens for this event, sees the view has changed, and calls the [`InstrumentsStateManager.js`](src/scripts/data/InstrumentsStateManager.js) to ensure instrument data is loaded.
*   [`InstrumentsStateManager.js`](src/scripts/data/InstrumentsStateManager.js) fetches instrument data from `api/database.json` (via `json-server`).
*   [`InstrumentsStateManager.js`](src/scripts/data/InstrumentsStateManager.js) dispatches its own `stateChanged` event once data is ready.
*   [`InstrumentList.js`](src/scripts/instruments/InstrumentList.js) (or similar component) listens for this, retrieves the instrument data from the `InstrumentsStateManager`, and renders the list of instruments on the page.

### Key Design Patterns

The application employs several key design patterns to manage its complexity and provide a modular architecture:

*   **Single Page Application (SPA)**: Provides a fluid user experience by dynamically updating content, avoiding full page reloads.
*   **Client-Side Routing**: Navigation is managed by URL query parameters, with the [`ViewStateManager.js`](src/scripts/data/ViewStateManager.js) interpreting these to render appropriate components.
*   **Custom Event-Driven State Management (Observer/Publish-Subscribe)**: `*StateManager` modules act as "publishers" of state changes, while UI components "subscribe" to these events, updating themselves accordingly. This promotes decoupling between data and presentation.
*   **Component-Based UI**: The user interface is constructed from modular, reusable JavaScript components, improving maintainability and scalability.
*   **Modular JavaScript**: Code is logically organized into modules and subdirectories (e.g., `auth`, `classes`, `instruments`), enhancing code organization and readability.
*   **Modular JavaScript**: The [`src/scripts/`](src/scripts/) directory is highly modular, with subdirectories organizing code by feature or concern (e.g., `auth`, `classes`, `instruments`, `nav`, `data`).
*   **Mock API / JSON-Server Backend**: Facilitates rapid development and testing by simulating a backend REST API for CRUD operations.
*   **Mock API / JSON-Server Backend**: For development and demonstration, `json-server` is used as a mock REST API. This allows the front-end to interact with a simulated backend with full CRUD capabilities without needing a complex server-side implementation.

## 5. Summary of Overall Functionality

The application is a web platform with the following core features:

*   **User Authentication**: Handles user login and registration, maintaining sessions using `localStorage`.
*   **Instrument Marketplace**: Allows users to view a list of musical instruments for sale (Store view) and offers functionality to list instruments for sale (Sell view).
*   **Music Classes**: Displays available music classes (Classes view) and provides detailed information for individual classes.
*   **Instrument/Class Details**: Provides detailed views for individual instruments and classes.
*   **About Us Section**: Likely includes information about employees or musicians associated with the platform.

