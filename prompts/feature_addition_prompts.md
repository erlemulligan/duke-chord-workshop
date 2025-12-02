# Feature Addition & Modification Prompt Library
(Optimized for RooCode + Gemini 2.5)

This library contains high-quality prompts for extending legacy or modern codebases while maintaining consistency, avoiding breaking changes, and following established architecture. Designed for Architect Mode → Orchestrator Mode workflows.

---

# A. Strategic Feature Planning Prompts

## 1. **Feature Strategy Generation**
“Analyze the existing codebase and create a strategy for implementing the ____ feature. Ensure alignment with existing architecture, data flow, naming conventions, and component patterns.”

## 2. **Integration Pattern Analysis**
“Explain how this new feature should integrate with current patterns for data models, API services, UI components, and state management.”

## 3. **Design Before Code**
“Before writing any code, create an implementation design for this feature that matches the project's architectural style and avoids breaking changes.”

---

# B. Impact Assessment Prompts

## 4. **Affected Components & Files**
“Identify all components, modules, and functions that will be affected if we add/modify the ____ feature. Include direct and indirect impact.”

## 5. **Breaking Change Risk Assessment**
“List all potential breaking changes this feature may introduce. For each, provide mitigation steps.”

## 6. **State & Data Impact**
“Analyze how this feature affects global and local state, and what dependencies or consumers may be impacted.”

---

# C. Consistency Analysis Prompts

## 7. **Naming Convention Advisor**
“Based on the existing codebase’s naming patterns, what should I name the components, functions, files, and variables for the ____ feature?”

## 8. **Architectural Consistency Check**
“Compare this feature to other similar features in the app. What architectural patterns must I follow to keep consistency?”

## 9. **Error & Loading Patterns**
“Show me how error handling and loading states are implemented elsewhere, and provide recommendations for applying the same patterns in this feature.”

---

# D. Task List Generation Prompts

## 10. **Full Implementation Task List**
“Create a detailed, sequential task list for implementing the ____ feature, including data model changes, API work, business logic, UI updates, integration, and testing.”

## 11. **Layered Task List (Data → Logic → UI → Tests)**
“Generate a task list for this feature organized by layers:  
1. Data layer  
2. Business logic  
3. UI components  
4. Integration  
5. Testing”

## 12. **Explicit File & Function Task List**
“Generate a task list that specifies exact filenames, export names, and component/function signatures needed for this feature.”

---

# E. Implementation Scaffolding Prompts

## 13. **Data Model Extension**
“Show how to extend existing data models to support the ____ feature while following patterns used in other models.”

## 14. **API Extension Planning**
“Plan the API endpoints required for this feature using the established REST/GraphQL conventions in the codebase.”

## 15. **Component Hierarchy Plan**
“Identify where new UI components should live, how they should be structured, and how they integrate with the current component hierarchy.”

---

# F. Integration & Compatibility Prompts

## 16. **Component Modification Safety Check**
“If I modify ____ component to include this feature, what other areas of the app will be affected? Provide a full usage map.”

## 17. **State Management Compatibility**
“Analyze whether adding this state to the existing context/store will break or affect any current consumers.”

## 18. **API Versioning & Safety**
“Will adding these API endpoints or changing responses risk breaking existing endpoints or clients? Provide recommendations.”

---

# G. Legacy Code Feature Addition Prompts

## 19. **Legacy Modernization While Adding Feature**
“This module uses outdated patterns. How can I add the ____ feature while gradually modernizing the code without breaking functionality?”

## 20. **Pattern Bridging**
“The existing code uses older patterns for state/UI/data. How can I add this feature while bridging old patterns to new ones safely?”

## 21. **Low-Risk Legacy Integration**
“Provide the lowest-risk approach for adding this feature to this legacy component. Avoid major rewrites but improve quality where possible.”

---

# H. Architect → Orchestrator Handoff Prompts

## 22. **Task List Validation for Orchestrator Mode**
“Rewrite this task list to make each step atomic, unambiguous, and implementation-ready for Orchestrator Mode.”

## 23. **Generate Boilerplate for Each Task**
“For each step in the task list, generate skeleton code that fits existing patterns.”

## 24. **Integration Checkpoints**
“Add checkpoints where each part of the feature should be tested or validated before moving forward.”

---

# I. Testing, Validation, and Documentation Prompts

## 25. **Test Plan Generation**
“Create a complete testing plan for this feature including unit, integration, and regression tests.”

## 26. **Edge Case Identification**
“List all edge cases for this feature, including failures, invalid states, network issues, and unexpected user behavior.”

## 27. **Update Documentation Plan**
“List all documentation updates needed for this feature: README, API docs, component docs, architectural notes.”

---

# J. Multi-Agent Feature Planning Prompts

## 28. **Three-Agent Feature Plan**
“Simulate three agents collaborating on this feature:  
- Agent 1: Architect (high-level strategy)  
- Agent 2: Engineer (implementation details)  
- Agent 3: Reviewer (risks, improvements)  
Produce a unified plan.”

## 29. **Layered Feature Explanation**
“Explain this new feature addition in layers:  
1. Intent & purpose  
2. Architectural impact  
3. Data flow  
4. Required changes  
5. Potential risks  
6. Final recommended approach”

## 30. **Failure Mode Simulation**
“Simulate what could go wrong after adding this feature: integration issues, regressions, state inconsistencies, UI conflicts, or API mismatches.”

---

This library supports feature planning, risk analysis, modernization strategies, detailed task lists, architectural consistency, and safe implementation workflows for RooCode + Gemini 2.5.
