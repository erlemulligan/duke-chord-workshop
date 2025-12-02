# Enhanced Code Analysis Prompt Library (Optimized for RooCode + Gemini 2.5)

This library integrates best practices from professional codebase onboarding, AI-assisted analysis, and Ask-mode workflows. Prompts are grouped by purpose and designed for high signal-to-noise clarity when working with legacy or modern codebases.

---

# A. High‑Level Codebase Understanding

## 1. **Project Structure Overview**
“Analyze the entire project structure. Explain the purpose of each major directory, key files, and how the folders relate to core features. Identify any architectural patterns.”

## 2. **Architecture Reconstruction**
“Reconstruct the application’s architecture. Describe major layers, components, data flow, and key design patterns. Summarize the system as if onboarding a new developer.”

## 3. **Entry Point & Main Flow Tracing**
“Trace the application startup process beginning from the entry point (e.g., index.js, main.go, app.ts). Explain how control flows into the main parts of the system.”

## 4. **Component / Module Relationship Mapping**
“Generate a diagram-style explanation of how components/modules interact. Identify parent-child relationships, shared state, and communication pathways.”

---

# B. Data Flow, State, and Business Logic

## 5. **Follow the Data (Data Flow Mapping)**
“Trace the full data flow for the following feature: ____. Start from user action → UI handlers → state/store → API calls → database (if applicable) → response → UI update.”

## 6. **State Management Analysis**
“Explain how the application manages state. Identify global stores, reducers, contexts, or other patterns. Describe what data is stored where and why.”

## 7. **API Integration Patterns**
“List all API endpoints the application interacts with. Explain how API calls are structured, where they are located, and how responses are processed.”

## 8. **Business Logic Location Finder**
“Identify where the business logic for feature X is implemented. Summarize the key functions and rules. Explain the reasoning behind their design if evident.”

---

# C. Patterns, Conventions, and Team Practices

## 9. **Coding Conventions Discovery**
“Identify the coding conventions used throughout the project (naming, file structure, error handling patterns, architectural standards).”

## 10. **Component/Function Pattern Recognition**
“Analyze the patterns used for components or functions. Describe consistency, deviations, and recommended improvements.”

## 11. **Error Handling Pattern Audit**
“Explain how errors are typically handled. Identify any inconsistencies, missing edge case handling, or risky patterns.”

---

# D. Deep Investigation Prompts

## 12. **Feature Deep‑Dive**
“Perform a deep-dive on the __ feature. Identify all involved files, components, functions, and data flow paths. Explain edge cases and potential failure points.”

## 13. **Failure Path & Error Mode Simulation**
“Simulate possible failure paths for this feature. What happens if dependencies fail? What errors surface to users? Identify silent failures or missing checks.”

## 14. **Security Concern Scan**
“Identify potential security vulnerabilities, unsanitized inputs, insecure patterns, unsafe dependencies, or OWASP-related risks.”

## 15. **Performance Bottleneck Hunt**
“Analyze this code for performance inefficiencies. Identify slow operations, unnecessary computations, suboptimal queries, or heavy renders.”

---

# E. Legacy Code Modernization

## 16. **Legacy Modernization Assessment**
“Evaluate how legacy this code is. Identify outdated patterns, risky dependencies, tight coupling, and migration blockers. Suggest modernization strategies.”

## 17. **Minimal-Safe Refactor Plan**
“Propose the smallest set of refactors that improve readability, testability, and maintainability without altering functionality.”

## 18. **Backward Compatibility Analysis**
“If we modernize this module, what breaks? Identify all public interfaces, implicit contracts, and downstream dependencies.”

---

# F. Testing, Quality, and Maintainability

## 19. **Test Coverage Analysis**
“Identify current test patterns and gaps. Suggest what should be tested and how. Recommend areas where tests are missing entirely.”

## 20. **Maintainability Heatmap**
“Rank the maintainability of the major modules from 1–5. Provide justification and recommended actions.”

## 21. **Code Smell & Anti‑Pattern Scanner**
“List all code smells and anti-patterns in this module. Provide:  
- why it's a problem  
- severity  
- minimal fix  
- ideal fix”

---

# G. Documentation & Developer Onboarding

## 22. **Generate a Developer Onboarding Guide**
“Create an onboarding guide for this codebase that explains architecture, project structure, coding conventions, and key workflows.”

## 23. **Rewrite Analysis as Documentation**
“Convert everything we’ve learned into a structured README section intended for new developers joining the project.”

## 24. **Component Documentation Template**
“Generate reusable documentation templates for components, modules, or services in this codebase.”

---

# H. Multi‑Angle AI Reasoning Prompts

## 25. **Multi‑Agent Code Investigation**
“Simulate three expert agents:  
- Agent 1: Summarizes intent and architecture  
- Agent 2: Identifies risks, bugs, smells  
- Agent 3: Suggests improvements and refactors  
Provide a synthesized final answer.”

## 26. **Layered Understanding Prompt**
“Explain this code in layers:  
1. High-level intent  
2. Architectural role  
3. Flow of data  
4. Edge cases  
5. Opportunities for improvement”

## 27. **Behavioral Reconstruction (Without Executing)**
“Reconstruct what this code does at runtime through all branches: normal, edge, and error paths.”

---

# I. Red Flag Detection

## 28. **Codebase Risk Audit**
“Identify red flags: code smells, inconsistent patterns, missing tests, unclear ownership, architectural drift, security issues, unused dependencies.”

## 29. **Refactor Priority List**
“Rank areas of the codebase by urgency of refactoring. Explain risks and recommended sequencing.”

## 30. **Hidden Complexity Detector**
“Identify parts of the codebase where complexity is concealed inside helpers, utilities, or nested logic.”

---

This prompt library incorporates:  
✓ progressive codebase understanding  
✓ follow-the-data analysis  
✓ team conventions & business logic mapping  
✓ error-path review  
✓ multi-agent LLM reasoning  
✓ onboarding documentation workflows  
✓ modernization & refactoring strategies  

Designed for RooCode’s Ask Mode + Gemini 2.5 for maximum clarity and practical usefulness.
