# AI Coding Framework Guide: Organize Your Project, Guide the AI

This guide is designed for developers who want to improve their interaction with AI coding assistants (like Claude, Cursor, GitHub Copilot, etc.) by structuring their project codebase to provide better context, standards, and reusable instructions.

## 1. Introduction
The goal of this framework is to turn your project repository into a self-documenting environment that AI models can easily parse. By providing clear instructions and standardized policies, you reduce hallucinations, ensure code consistency, and speed up development.

## 2. Directory Structure Overview
Your project should be structured to separate concerns:
- **Root-level instructions:** Model-specific behavioral adapters.
- **`docs/ai/`**: Deep context, architectural knowledge, and project standards.
- **`skills/`**: Reusable prompt templates for common tasks.
- **`.github/`**: Automation templates (e.g., Pull Requests).

---

## 3. Implementation Details

### A. Root Level Adapters (`AGENTS.md`, `CLAUDE.md`)
These files contain "System Instructions" or "Personas" for specific AI models.
- **`AGENTS.md`**: Instructions tailored for general-purpose models (e.g., GPT-4/Codex).
- **`CLAUDE.md`**: Instructions optimized for Claude’s capabilities and token handling.
*Keep these concise. Focus on preferred code style, library usage, and communication tone.*

### B. Project Context (`docs/ai/`)
This is the "Brain" of your project. The AI looks here to understand *how* to build your product.
1.  **`context.md`**: A high-level overview of what the project is, its purpose, and its current state.
2.  **`architecture.md`**: Explains the system design, tech stack, and data flow.
3.  **`coding-standards.md`**: Naming conventions, indentation, folder structures, and preferred design patterns.
4.  **`testing-policy.md`**: Expectations for test coverage, types of tests (unit/integration/E2E), and frameworks used.
5.  **`security-policy.md`**: Sensitive areas, authentication guidelines, and dependency management.
6.  **`release-policy.md`**: Steps for deployment, versioning, and environment management.
7.  **`code-review.md`**: What the AI should prioritize when reviewing your code (e.g., performance, readability, edge cases).

### C. Reusable Skill Templates (`skills/`)
These act as "macros" for the AI. Instead of typing a long prompt every time, you can ask the AI to "Follow the `bug-fix` skill template."
- **Example `bug-fix/`**: Contains steps: 1. Reproduce error, 2. Isolate code, 3. Propose fix, 4. Update tests.

### D. Automation Templates (`.github/`)
Use `.github/pull_request_template.md` to ensure that every PR submitted (even by AI) follows your team's checklist.

---

## 4. How to Get Started
1.  **Create the Folder Structure:** Start with the `docs/ai/` directory.
2.  **Populate the Files:** You don't need to write them all at once. Start with `context.md` and `coding-standards.md`.
3.  **Refine:** As you work with the AI, if it makes a mistake, update the corresponding `policy.md` file to ensure it doesn't make that same mistake again.
4.  **Iterate:** Treat these files as living documentation.

---

## 5. Index for Navigation
- [Introduction](#1-introduction)
- [Directory Structure Overview](#2-directory-structure-overview)
- [Implementation Details](#3-implementation-details)
    - [Adapters](#a-root-level-adapters-agentsmd-claudemd)
    - [Project Context](#b-project-context-docsai)
    - [Skill Templates](#c-reusable-skill-templates-skills)
    - [Automation](#d-automation-templates-github)
- [How to Get Started](#4-how-to-get-started)
"""