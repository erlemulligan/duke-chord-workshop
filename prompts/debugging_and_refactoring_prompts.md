# Debugging & Refactoring Prompts and Best Practices (Roocode‑Friendly)

This file contains concise, Roocode/Gemini 2.5–friendly prompts and best‑practice patterns derived from the "Debugging and Refactoring with LLMs" document. It is formatted as short, actionable prompt blocks and lists.

---

## 1. Bug Analysis Prompts (Ask Mode)

**General Bug Understanding**

* "Analyze this error message and explain root cause: `<error>`"
* "Identify where the failure occurs in this stack trace and why."
* "Explain the exact conditions that cause this bug."
* "Summarize what this failing function *currently* does before fixing."

**Common Bug Patterns**

* "Find all potential null/undefined accesses in this file."
* "Trace async execution and identify promise/race‑condition issues."
* "Analyze state updates and find incorrect or stale state usage."
* "Debug event handlers and find places where events might not fire."

**Systematic Bug Searching**

* "List possible edge cases this component does *not* handle."
* "Identify any race conditions, timing issues, or async hazards."
* "What happens if the API returns unexpected or malformed data?"

---

## 2. Refactoring Assessment Prompts (Architect Mode)

**Assess the Codebase**

* "Analyze this file and list code smells and maintainability problems."
* "Identify duplication, complexity, and inconsistent patterns."
* "Highlight any missing error handling or risky assumptions."
* "Explain which functions/components violate Single Responsibility Principle."

**Refactoring Strategy Planning**

* "Create a risk‑scored refactoring plan for this file (low → medium → high)."
* "Break refactor into small, safe, testable steps."
* "Describe low‑risk improvements that maintain existing behavior."
* "Create a dependency map for this component or module."

---

## 3. Refactoring Techniques (Prompts)

**Extract Function / Extract Component**

* "Break this long function into smaller focused functions."
* "Identify parts of this React component that should be split out."

**Eliminate Duplication**

* "Find duplicated logic and suggest reusable utilities/components."

**Improve Naming**

* "Propose clearer names for these variables and functions."

**Simplify Logic**

* "Flatten this deeply nested logic using early returns."
* "Refactor this conditional into a more readable pattern."

**Performance Refactoring**

* "Identify re‑render sources; suggest useMemo/useCallback/React.memo."
* "Find expensive calculations and propose memoization strategy."
* "Detect heavy dependencies and unused imports."

---

## 4. Test Creation Prompts

**Test Strategy Planning**

* "Create a prioritized test strategy for this component."
* "List the top behaviors that must be captured in tests first."

**Unit Test Generation**

* "Write unit tests covering normal cases, edge cases, and errors."
* "Generate snapshot and interaction tests for this React component."

**Test‑Driven Refactoring**

* "Before refactoring, generate tests that capture current behavior."
* "Confirm these tests reflect the existing logic before proceeding."

---

## 5. Orchestrator‑Friendly Implementation Tasks

**Example Task Format**

* "Task: Extract constants from lines X, Y, Z into a constants file."
* "Task: Add type safety (PropTypes or TypeScript interfaces)."
* "Task: Move data‑fetching to a custom hook; update component to use it."
* "Task: Add loading and error states with unified patterns."
* "Task: Replace duplicated logic in these files with a shared utility."

---

## 6. Performance Analysis Prompts

* "Analyze for unnecessary re‑renders and list causes."
* "Identify expensive operations and propose optimizations."
* "Review bundle size footprint and highlight large dependencies."

---

## 7. Advanced Debugging Prompts

* "Trace root cause instead of surface‑level fix; show causal chain."
* "Map data flow across interacting components to locate bug origin."
* "Identify timing issues or race conditions causing intermittent failures."

---

## 8. Production‑Readiness Prompts

* "Suggest improved error handling patterns for production safety."
* "Add logging/telemetry recommendations for easier debugging."
* "Describe how this component should gracefully degrade if dependencies fail."

---

## 9. Best‑Practice Rules

**Incrementalism**

* Always refactor in small, safe steps.
* Validate after each change.

**Testing**

* Write tests for current behavior *before* refactoring.
* Expand test coverage as code improves.

**Version Control**

* Commit frequently with descriptive messages.
* Make isolated, reversible changes.

**Documentation**

* Document reasoning for all structural changes.

**Measurement**

* Benchmark performance before/after major changes.

**Code Reviews**

* Use reviews to catch unintended changes and architectural drift.
