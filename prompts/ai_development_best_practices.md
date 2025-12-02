# Best Practices for AI‑Assisted Development Prompts

A practical reference for using AI tools (Gemini, ChatGPT, Claude, etc.) safely and effectively during software development.

---

## ✅ DO — Core Principles

### **1. Ask Clarifying Questions First**

**Prompt:**

* *"Before generating code, ask me 3 clarifying questions to understand the context and requirements."*
* *"Ask for missing information about inputs, outputs, constraints, and the existing codebase before proposing a solution."*

### **2. Read and Understand AI‑Generated Code Before Using It**

**Prompt:**

* *"Explain the code you generated line‑by‑line."*
* *"What assumptions does this code make?"*

### **3. Test Thoroughly — AI Can Make Mistakes**

**Prompt:**

* *"Generate unit tests and edge cases for this code."*
* *"What scenarios might break this implementation?"*

### **4. Verify Information**

**Prompt:**

* *"Show the specific documentation references or standards this solution relies on."*
* *"List API versions, library names, or assumptions you used so I can verify."*

### **5. Iterate Until the Output Is Useful**

**Prompt:**

* *"Refine your previous answer. Here’s what needs improvement…"*
* *"Generate 3 alternate approaches, ranked by safety and clarity."*

### **6. Document as You Go**

**Prompt:**

* *"Generate commit messages summarizing the changes and motivations."*
* *"Draft a short architecture note explaining the design choices."*

---

## ❌ DON'T — Common Pitfalls to Avoid

### **1. Don’t Blindly Copy/Paste AI Code**

**Prompt:**

* *"Review this AI‑generated code for risks, hidden assumptions, or missing error handling."*

### **2. Don’t Skip Testing Because 'AI Wrote It'**

**Prompt:**

* *"Write a test suite that ensures the code behaves as intended and catches regressions."*

### **3. Don’t Assume AI Understands Your Context**

**Prompt:**

* *"Ask me 5 questions about the existing system architecture before proposing modifications."*

### **4. Don’t Use AI as a Shortcut to Avoid Learning**

**Prompt:**

* *"Explain the concepts behind this implementation as if teaching a new engineer."*

### **5. Don’t Rely on AI for Critical Security Decisions Unreviewed**

**Prompt:**

* *"Identify security risks in this code and label anything that needs a manual audit."*

---

# Success Criteria for Effective AI‑Assisted Development

Use these prompts to verify that a task was completed correctly.

### **✓ Repository Setup**

**Prompt:**

* *"Review my repository structure for consistency, clarity, and standard best practices."*

### **✓ Architecture Understanding**

**Prompt:**

* *"Explain the architecture of this application and diagram the major flows."*

### **✓ Complete README Documentation**

**Prompt:**

* *"Analyze my README and suggest improvements for clarity, onboarding, and accuracy."*

### **✓ Issue Resolution**

**Prompt:**

* *"Summarize how Issue #X was resolved. Identify remaining risks or follow‑up items."*

### **✓ Effective Human–AI Collaboration**

**Prompt:**

* *"Evaluate my prompts and suggest improvements for precision and clarity."*

### **✓ Documented Learning**

**Prompt:**

* *"Create a learning log summarizing what I learned through each change or issue fix."*
