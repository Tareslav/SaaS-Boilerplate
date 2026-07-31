Record only decisions future agents must understand.

Use this format:

## **YYYY-MM-DD — Decision title**

### **Status**

Proposed / Accepted / Replaced

### **Context**

Why was a decision needed?

### **Decision**

What was decided?

### **Reasoning**

Why was this option selected?

### **Consequences**

What becomes easier, harder, allowed, or prohibited?

### **Replaces**

Previous decision, if applicable.

---

## **Initial decision — Multi-agent development workflow**

### **Status**

Accepted

### **Context**

The project will use Claude Code and Codex sequentially. Claude usage limits are constrained.

### **Decision**

* The repository is the shared source of truth.  
* Claude handles planning, architecture, difficult debugging, security, and review.  
* Codex handles most routine implementation.  
* Every implementation sprint requires an approved plan.  
* Agents work in small focused sprints.  
* Context is transferred through documentation, Git commits, and ﻿﻿﻿HANDOFF.md﻿.

  ### **Reasoning**

This division protects the Claude token budget while preserving strong reasoning and review for high-risk work.

### **Consequences**

The project requires current documentation, small commits, clear acceptance criteria, and concise handoffs.

1. 

