# AI Coding Framework Guide: Organize Your Project, Guide the AI

This guide is designed for developers who want to improve their interaction with AI coding assistants (like Claude, Cursor, GitHub Copilot, etc.) by structuring their project codebase to provide better context, standards, and reusable instructions.

## Index for Navigation
- [1. Introduction](#1-introduction)
- [2. Directory Structure Overview](#2-directory-structure-overview)
- [3. Implementation Details](#3-implementation-details)
    - [A. Root Level Adapters](#a-root-level-adapters-agentsmd-claudemd)
    - [B. Project Context](#b-project-context-docsai)
    - [C. Reusable Skill Templates](#c-reusable-skill-templates-skills)
    - [D. Automation Templates](#d-automation-templates-github)
- [4. How to Get Started](#4-how-to-get-started)

---

## 1. Introduction
The goal of this framework is to turn your project repository into a self-documenting environment that AI models can easily parse. By providing clear instructions and standardized policies, you reduce hallucinations, ensure code consistency, and speed up development.

## 2. Directory Structure Overview
Your project should be structured to separate concerns:
*   **Root-level instructions:** Model-specific behavioral adapters.
*   **`docs/ai/`**: Deep context, architectural knowledge, and project standards.
*   **`skills/`**: Reusable prompt templates for common tasks.
*   **`.github/`**: Automation templates (e.g., Pull Requests).

## 3. Implementation Details

### A. Root Level Adapters (`AGENTS.md`, `CLAUDE.md`)
These files contain "System Instructions" or "Personas" for specific AI models.

*   **`AGENTS.md`**: Instructions tailored for general-purpose models (e.g., GPT-4/Codex).
    ```markdown
    # Agent Persona: General Purpose
    You are an expert software engineer. 
    - Tone: Professional, concise, and helpful.
    - Priority: Code maintainability, security, and performance.
    - Rules: Never suggest deprecated APIs. Always explain the reasoning behind major architectural decisions.
    ```
*   **`CLAUDE.md`**: Instructions optimized for Claudeâs capabilities and token handling. Keep these concise. Focus on preferred code style, library usage, and communication tone.
    ```markdown
    # Agent Persona: Claude
    You are the lead architect for this project. 
    - Goal: Maintain the highest standards of code quality.
    - Constraints: Use modern TypeScript/ES6+ features. Avoid overly verbose code. 
    - Preferences: Write detailed JSDoc comments for public-facing functions.
    ```

### B. Project Context (`docs/ai/`)
This is the "Brain" of your project. The AI looks here to understand how to build your product.

*   **`context.md`**: A high-level overview of what the project is, its purpose, and its current state.
    ```markdown
    # Project Context
    - Project Name: [Project Name]
    - Purpose: [Brief description of what the project does]
    - Stack: [e.g., Next.js, PostgreSQL, Tailwind]
    - Key Goals: [e.g., High performance, mobile-first design]
    ```
*   **`architecture.md`**: Explains the system design, tech stack, and data flow.
    ```markdown
    # Architecture Overview
    - Pattern: [e.g., Clean Architecture, MVC]
    - Data Flow: [Explain how data travels from API to UI]
    - Key Modules: [List main folders and their responsibilities]
    ```
*   **`coding-standards.md`**: Naming conventions, indentation, folder structures, and preferred design patterns.
    ```markdown
    # Coding Standards
    - Language: TypeScript (Strict mode)
    - Styling: [e.g., Tailwind CSS, BEM]
    - Naming: PascalCase for components, camelCase for functions.
    - Formatting: 2 spaces, no semicolons (or your preference).
    ```
*   **`testing-policy.md`**: Expectations for test coverage, types of tests (unit/integration/E2E), and frameworks used.
    ```markdown
    # Testing Policy
    - Coverage Target: 80%
    - Frameworks: [e.g., Jest, Playwright]
    - Requirements: Every new feature must include at least one unit test.
    ```
*   **`security-policy.md`**: Sensitive areas, authentication guidelines, and dependency management.
    ```markdown
    # Security Policy
    - Secrets: Never commit API keys. Use `.env` and `dotenv`.
    - Validation: Validate all user input using [e.g., Zod, Joi].
    - Auth: Use [e.g., NextAuth.js] for authentication.
    ```
*   **`release-policy.md`**: Steps for deployment, versioning, and environment management.
    ```markdown
    # Release Policy
    - Branching: `main` for production, `develop` for staging.
    - Versioning: Follow SemVer (v1.0.0).
    - Deploy Process: Run `npm test`, then `npm run build`, then deploy to [Platform].
    ```
*   **`code-review.md`**: What the AI should prioritize when reviewing your code (e.g., performance, readability, edge cases).
    ```markdown
    # Code Review Protocol
    - Performance: Are there unnecessary re-renders?
    - Readability: Is the code self-documenting?
    - Edge Cases: Did you handle null/undefined scenarios?
    ```

### C. Reusable Skill Templates (`skills/`)
These act as "macros" for the AI. Instead of typing a long prompt every time, you can ask the AI to "Follow the `bug-fix` skill template."

*   **Example `skills/bug-fix/README.md`**: Contains steps: 1. Reproduce error, 2. Isolate code, 3. Propose fix, 4. Update tests.
    ```markdown
    # Skill: Bug Fix
    Follow this process:
    1. Identify root cause.
    2. Create a reproduction script.
    3. Write a test case that fails.
    4. Implement the fix.
    5. Verify test success.
    ```

### D. Automation Templates (`.github/`)
Use `.github/pull_request_template.md` to ensure that every PR submitted (even by AI) follows your team's checklist.
```markdown
## Summary
[What was changed and why?]

## Checklist
- [ ] Code follows project standards
- [ ] Tests updated
- [ ] No security issues introduced
```

## 4. How to Get Started
*   **Create the Folder Structure:** Start with the `docs/ai/` directory.
*   **Populate the Files:** You don't need to write them all at once. Start with `context.md` and `coding-standards.md`.
*   **Refine:** As you work with the AI, if it makes a mistake, update the corresponding `policy.md` file to ensure it doesn't make that same mistake again.
*   **Iterate:** Treat these files as living documentation.
