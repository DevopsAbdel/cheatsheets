# Claude Code Project Structure: A Complete Beginner's Guide

Welcome to the definitive, beginner-friendly guide to structuring and managing projects using **Claude Code**. Whether you are new to AI-assisted software development or looking to structure production-ready agentic workflows, this guide will walk you through every detail step-by-step.

---

## Table of Contents
1. [Introduction to Claude Code](#1-introduction-to-claude-code)
2. [Project Directory & File Structure](#2-project-directory--file-structure)
3. [Core Architectural Components](#3-core-architectural-components)
4. [CLAUDE.md Essentials](#4-claudemd-essentials)
5. [Extending Claude Code: Extension Types](#5-extending-claude-code-extension-types)
6. [Lifecycle Hook Events](#6-lifecycle-hook-events)
7. [Anatomy of a Skill Structure](#7-anatomy-of-a-skill-structure)
8. [Integrating Model Context Protocol (MCP) Servers](#8-integrating-model-context-protocol-mcp-servers)
9. [Slash Commands Reference](#9-slash-commands-reference)
10. [Multi-Agent Team Patterns](#10-multi-agent-team-patterns)
11. [Getting Started Step-by-Step](#11-getting-started-step-by-step)
12. [Context Management & Token Optimization](#12-context-management--token-optimization)
13. [Security Best Practices](#13-security-best-practices)
14. [CLAUDE.md Anti-Patterns](#14-claudemd-anti-patterns)
15. [Debugging, Logging & Troubleshooting](#15-debugging-logging--troubleshooting)
16. [Pro Tips & Advanced Strategies](#16-pro-tips--advanced-strategies)
17. [Frequently Asked Questions (FAQs)](#17-frequently-asked-questions-faqs)

---

## 1. Introduction to Claude Code

**Claude Code** is an AI-assisted development CLI and workspace system built by Anthropic. It allows developers to integrate Claude directly into their development terminal and repository. 

### Key Term Glossary
* **Workspace / Project Memory (`CLAUDE.md`)**: A centralized context file containing key instructions, conventions, architecture guidelines, and workflows for Claude.
* **Skills**: Auto-activated modular workflows that give Claude specialized capabilities (e.g., automated code review, test writing, security auditing).
* **Hooks**: Event-driven scripts that execute automatically during specific lifecycle events (e.g., pre-tool use, pre-commit secret scanning).
* **MCP (Model Context Protocol)**: An open standard enabling Claude to connect securely to external systems, databases, third-party APIs, and local services.
* **Subagents**: Isolated, parallel task-execution agents configured via `.yml` files to perform specific roles without polluting the primary context.

---

## 2. Project Directory & File Structure

A standard, production-ready Claude Code repository follows a clean, organized hierarchy. Below is the complete project tree visualization:

```text
my_project/
├── CLAUDE.md                      # Primary project memory & instruction set
├── .claude/                       # Core configuration & extension hub
│   ├── settings.json              # Shared project settings (tracked in Git)
│   ├── settings.local.json        # Personal/local overrides (Git-ignored)
│   ├── commands/                  # Custom Slash Commands (.md templates)
│   │   ├── review.md              # Code review command template
│   │   ├── deploy.md              # Staging/Production deployment script
│   │   ├── test-all.md            # Comprehensive test runner guide
│   │   └── bootstrap.md           # Module scaffolding script
│   ├── skills/                    # Specialized auto-activated capabilities
│   │   ├── code-review/
│   │   │   ├── SKILL.md           # Instructions & meta configuration
│   │   │   ├── scripts/           # Execution scripts (Python/Bash)
│   │   │   ├── references/        # Documentation loaded on demand
│   │   │   └── assets/            # Static files & boilerplate templates
│   │   ├── test-writer/
│   │   │   └── SKILL.md
│   │   ├── security-audit/
│   │   │   └── SKILL.md
│   │   └── refactor/
│   │       └── SKILL.md
│   ├── agents/                    # Subagent role definitions (.yml)
│   │   ├── code-reviewer.yml
│   │   ├── test-writer.yml
│   │   ├── security-auditor.yml
│   │   └── devops-sre.yml
│   └── plugins/                   # Bundled distributable extensions
│       ├── manifest.json
│       └── my-plugin/
├── .mcp.json                      # Model Context Protocol server configuration
├── src/                           # Source codebase
│   ├── components/                # UI / Feature components (auth, dashboard, shared)
│   ├── services/                  # Business logic (api.ts, auth.ts, database.ts)
│   ├── utils/                     # Utility helpers (logger.ts, validators.ts)
│   └── types/                     # TypeScript definitions (index.ts)
├── tests/                         # Unit, Integration, and E2E test suits
├── docs/                          # Architecture, API, and onboarding docs
├── scripts/                       # Local build and database scripts (setup.sh, seed-db.sh)
├── package.json                   # Node.js dependencies
├── tsconfig.json                  # TypeScript compiler settings
├── .env.example                   # Environment variable template
├── .gitignore                     # Git exclusion rules
├── Dockerfile                     # Container specs
└── README.md                      # General human-readable project overview
```

---

## 3. Core Architectural Components

The primary framework of Claude Code is composed of six essential blocks:

| Component | Path / Location | Purpose & Function |
| :--- | :--- | :--- |
| **CLAUDE.md** | `/CLAUDE.md` | Core project memory and architecture instructions. |
| **.claude/** | `/.claude/` | Central hub for settings, custom commands, skills, and subagents. |
| **commands/** | `/.claude/commands/` | Custom user-invoked markdown scripts triggered by `/command`. |
| **skills/** | `/.claude/skills/` | Deep, multi-file modular capabilities triggered automatically based on intent. |
| **.mcp.json** | `/.mcp.json` | Protocol setup connecting Claude to external resources (DBs, APIs, SaaS tools). |
| **agents/** | `/.claude/agents/` | Dedicated worker personalities defined in YAML for isolated task execution. |
| **plugins/** | `/.claude/plugins/` | Packaged extensions combining skills, hooks, and commands into standard setups. |

---

## 4. CLAUDE.md Essentials

The `CLAUDE.md` file serves as Claude's persistent cognitive memory for your repository. Whenever Claude starts a session, it reads this file first to understand project constraints and rules.

### Essential Structure of a `CLAUDE.md`

1. **Tech Stack & Architecture Overview**: Frameworks, languages, databases, and key design patterns (e.g., Next.js, PostgreSQL, Clean Architecture).
2. **Project Conventions & Style Guide**: Naming conventions, formatting, file naming, functional vs. OOP paradigms.
3. **Testing Requirements & Patterns**: Required coverage percentages, test runner commands (e.g., `npm test`), mock policies.
4. **Git Workflow & Branch Strategy**: Naming conventions (`feature/`, `fix/`), PR templates, and commit message formats.
5. **Security & Compliance Rules**: Hard restrictions on secret storage, data sanitization, and API permissions.

#### Example `CLAUDE.md` Template
```markdown
# Project Memory & Conventions

## Tech Stack
- Frontend: React 18, Next.js 14 (App Router), Tailwind CSS
- Backend: Node.js, Express, TypeScript
- Database: PostgreSQL with Prisma ORM

## Code Style & Rules
- Use functional TypeScript components with explicit interface types.
- Never hardcode API keys or credentials.
- Always handle errors with try/catch blocks using the custom `AppError` class.

## Testing Standards
- All new service methods require unit test coverage in `tests/unit/`.
- Run `npm test` before committing.
```

---

## 5. Extending Claude Code: Extension Types

Claude Code can be customized across six distinct layers:

```
                  +-----------------------------------+
                  |        Claude Code Kernel         |
                  +-----------------------------------+
                                    |
     +-----------------+------------+------------+-----------------+
     |                 |                         |                 |
+----+----+      +-----+-----+             +-----+-----+     +-----+-----+
| Skills  |      |   Hooks   |             |    MCP     |     | Subagents |
+---------+      +-----------+             +-----------+     +-----------+
 Auto-matched     Lifecycle                 External          Isolated
 Workflows        Events                    Integrations      Parallel Workers
```

1. **Skills**: Modular capabilities (e.g., `code-review`, `security-audit`) loaded automatically when task intent matches pre-defined patterns.
2. **Hooks**: Deterministic shell scripts or triggers executing strictly on engine lifecycle events.
3. **MCP (Model Context Protocol)**: Connectors that expose database queries, API interactions, and local tools directly to Claude.
4. **Subagents**: Isolated worker tasks executing specialized prompts in clean, dedicated sub-contexts.
5. **Agent Teams**: Coordinated collections of subagents running multi-phase pipelines (e.g., design -> implement -> audit).
6. **Plugins**: Standardized distribution packages containing pre-packaged skills, hooks, and commands.

---

## 6. Lifecycle Hook Events

Hooks allow you to enforce strict policies, run linters, or send alerts during Claude's execution session.

```
[User Action / Prompt] 
          │
          ▼
   (SessionStart) ──► Loads context, rules, and env variables
          │
          ▼
    (PreToolUse)  ──► Intercepts & blocks prohibited actions (e.g., dropping DB tables)
          │
      [Tool Run]
          │
          ▼
   (PostToolUse)  ──► Auto-formats or auto-lints modified files
          │
          ▼
    (PreCommit)   ──► Scans code for hardcoded secrets/passwords
          │
          ▼
    (SessionEnd)  ──► Generates session summaries and logs
```

### Event Breakdown
* **`PreToolUse`**: Intercepts actions *before* execution. Use case: Blocking harmful shell execution or dangerous SQL queries.
* **`PostToolUse`**: Executes *after* a tool finishes. Use case: Auto-running `prettier` or `eslint` after file edits.
* **`SessionStart`**: Runs when a new CLI session boots. Use case: Pulling latest environment variables or setting initial state.
* **`SessionEnd`**: Triggered when exiting the session. Use case: Writing session summaries or temporary file cleanup.
* **`PreCommit`**: Triggered prior to Git commits. Use case: Mandatory secret detection gate preventing credential leaks.
* **`Notification`**: Dispatches system events. Use case: Sending Slack, Discord, or Webhook alerts on test failures.

---

## 7. Anatomy of a Skill Structure

Skills reside in `.claude/skills/<skill-name>/` and provide Claude with specialized domain knowledge and executable tools.

```text
.claude/skills/code-review/
├── SKILL.md          # Primary instructions, trigger metadata, and parameter definitions
├── scripts/          # Automation scripts (Python, Bash, Node.js) executed by the skill
├── references/       # Supplemental specs, style guides, or API documentation loaded on demand
└── assets/           # Static templates, boilerplate code, and baseline assets
```

### Purpose of Key Files
* **`SKILL.md`**: The brain of the skill. Contains metadata declaring when the skill should activate and instructions for carrying out the task.
* **`scripts/`**: Executable scripts that perform deterministic operations (e.g., parsing code metrics or generating ASTs).
* **`references/`**: Heavy reference documentation loaded into context *only when needed*, preserving token limits.
* **`assets/`**: Standard boilerplate templates injected when generating new modules or configuration files.

---

## 8. Integrating Model Context Protocol (MCP) Servers

MCP enables Claude Code to directly access production tool sets and databases without intermediary copy-pasting.

### Common MCP Integrations
* **GitHub**: Fetch issues, open Pull Requests, inspect workflow runs.
* **JIRA / Linear**: Read tickets, update issue status, log progress notes.
* **Slack**: Search historical team chats, post execution updates.
* **PostgreSQL / Database**: Execute read-only sanity checks, inspect schemas.
* **Playwright**: Automate headful/headless browser rendering and test web interfaces.

### Configuration Example (`.mcp.json`)
```json
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres", "postgresql://user:pass@localhost:5432/mydb"]
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_xxxxxxxxxxxx"
      }
    }
  }
}
```

---

## 9. Slash Commands Reference

Slash commands provide instant, manual triggers for common repeatable workflows stored in `.claude/commands/`.

| Command | Action | Description |
| :--- | :--- | :--- |
| `/review` | Run Code Review | Performs static analysis and code review on current Git diffs. |
| `/deploy` | Deploy Staging/Prod | Triggers deployment scripts and pushes changes to staging environment. |
| `/test-all` | Execute Test Suite | Runs all unit, integration, and end-to-end test suites. |
| `/bootstrap` | Scaffold Module | Interactively creates a new feature directory with components, types, and tests. |
| `/document` | Auto-Generate Docs | Analyzes recent changes and generates updated inline and markdown documentation. |
| `/refactor` | Code Refactoring | Evaluates target files and suggests architecture and performance improvements. |

---

## 10. Multi-Agent Team Patterns

When handling complex software tasks, subagent teams can be organized using five classic patterns:

```
1. Orchestrator              2. Pipeline              3. Map-Reduce
  [Orchestrator]             [A] ──► [B] ──► [C]        [Splitter]
   ┌────┼────┐                                         ┌────┼────┐
  [A]  [B]  [C]                                       [A]  [B]  [C]
                                                       └────┼────┘
                                                          [Merger]

4. Supervisor                5. Swarm
  [Supervisor]               [A] ◄───► [B]
    │      ▲                  ▲         ▲
    ▼      │                  │         │
  [Worker Node]               └─► [C] ◄─┘
```

1. **Orchestrator**: A central agent analyzes incoming tasks, delegates sub-tasks to specialized subagents, and synthesizes the results.
2. **Pipeline**: Sequential handoff chain where Agent A's output becomes Agent B's input (e.g., Code -> Audit -> Test -> Doc).
3. **Map-Reduce**: Large tasks are split across identical subagents running in parallel, with outputs merged into a single outcome.
4. **Supervisor**: A controller agent monitors worker execution, validates outputs, and forces retries upon failure detection.
5. **Swarm**: Dynamic, peer-to-peer execution where autonomous agents pass context and execution rights fluidly to each other.

---

## 11. Getting Started Step-by-Step

Follow this sequence to initialize Claude Code on any project:

1. **Install Claude Code globally**:
   ```bash
   npm i -g @anthropic-ai/claude-code
   ```
2. **Navigate to project directory and initiate session**:
   ```bash
   cd your-project && claude
   ```
3. **Create the initial repository context**:
   Create a `CLAUDE.md` file in the project root containing your tech stack, coding standards, and common commands. (Or run `/init` to generate automatically).
4. **Add custom Slash Commands**:
   Create markdown command files inside `.claude/commands/` (e.g., `.claude/commands/review.md`).
5. **Configure external tool connections**:
   Add external services, APIs, and databases using `.mcp.json`.
6. **Scale capabilities with Skills**:
   As project requirements grow, build custom workflows under `.claude/skills/`.

---

## 12. Context Management & Token Optimization

Managing context space is critical to maintaining precision, speed, and cost efficiency. Use this context strategy:

```
0% Context                50%                  70%            90%+
[==========================|====================|==============|==========>]
      Work Freely          Monitor Spend     Run /compact    CRITICAL:
                                                              Run /clear
```

* **0%–50% Context Usage**: Optimal performance zone. Work freely on core features and deep tasks.
* **50%–70% Context Usage**: Routine usage zone. Keep an eye on long conversations and large file reads.
* **70%–90% Context Usage**: High usage zone. Run `/compact` to condense conversation history while retaining key decision context.
* **90%+ Context Usage**: Danger zone. Run `/clear` to start a fresh thread and prevent degradation or context truncation.

---

## 13. Security Best Practices

Protect your repository and credentials when working with AI models:

* **Never Store Secrets in `CLAUDE.md`**: Do not put passwords, private API keys, or database credentials in `CLAUDE.md`.
* **Environment Variable Templates**: Use a `.env.example` file with mock values for context, and load actual secrets through environment variables.
* **Isolate Local Overrides**: Always place personal keys and local developer overrides in `.claude/settings.local.json` and ensure `.claude/settings.local.json` is added to `.gitignore`.
* **Automated Secret Detection**: Implement a `PreCommit` lifecycle hook to automatically scan and intercept credentials before commits are made.
* **Principle of Least Privilege for MCP**: Configure `.mcp.json` with read-only permissions whenever possible.

---

## 14. CLAUDE.md Anti-Patterns

Avoid these common pitfalls when authoring `CLAUDE.md`:

| Anti-Pattern | Why It Fails | Correct Solution |
| :--- | :--- | :--- |
| **500+ Lines File** | Consumes excessive context space on every single turn. | Keep `CLAUDE.md` under 500 lines. Offload details to `.claude/skills/`. |
| **Vague Instructions** | "Write good code" gives Claude no actionable guidance. | Use explicit rules: "Use TypeScript strict mode and standard error boundaries." |
| **Duplicating Docs** | Duplicating documentation leads to out-of-date instructions. | Link directly to source documentation files (e.g., `docs/api.md`). |
| **Missing Test Instructions** | Omitting test instructions leads to skipped or incorrect tests. | Specify explicit commands like `npm test -- --watch=false`. |
| **No Error Handling Guidelines** | Results in inconsistent error patterns across the repository. | Define clear handling conventions (e.g., "Log using `logger.ts`"). |

---

## 15. Debugging, Logging & Troubleshooting

When Claude produces unexpected behavior or tool errors occur, use these troubleshooting modes:

### Core Debug Flags & Tools
* **`--verbose`**: Enable detailed trace logs to inspect all raw prompts, system messages, and JSON payloads.
* **`/cost`**: Track token spending and cost breakdown across the current session.
* **`--resume`**: Replay, debug, or restore a failed execution session without re-running prior prompts manually.
* **Notification Hooks**: Set up custom alerting hooks to log tool execution errors to external channels.

### Troubleshooting Scenarios

#### Problem 1: Claude forgets standard project conventions midway through a session
* **Root Cause**: The context window filled up and older instructions were truncated.
* **Solution**: Execute `/compact` to condense context, or start fresh with `/clear` while referencing your `CLAUDE.md`.

#### Problem 2: MCP server commands are failing or timing out
* **Root Cause**: Invalid connection string or missing local environment dependencies.
* **Solution**: Verify credentials in `.env` and test the connection using native CLI commands outside of Claude Code.

---

## 16. Pro Tips & Advanced Strategies

* **Subagents for Parallel Research**: Use subagents to perform background code analysis or documentation research without filling up your primary prompt context.
* **Keep `CLAUDE.md` Under 500 Lines**: Keep core instructions concise; offload deep feature guides to `.claude/skills/`.
* **Git-Ignore Local Settings**: Keep `.claude/settings.local.json` in `.gitignore` to prevent leaking personal preferences or machine-specific paths.
* **Skills for Complex Prompts, Hooks for Rules**: Use **Skills** when you need intelligent, intent-matched workflows; use **Hooks** when you need strict, deterministic rules.
* **Auto-Scaffold Context**: Run `/init` in a new repository to automatically generate a baseline `CLAUDE.md` template based on existing repository files.

---

## 17. Frequently Asked Questions (FAQs)

### Q: What is the main difference between a Skill and a Slash Command?
**A:** A **Slash Command** is triggered manually by the user (e.g., typing `/review`), whereas a **Skill** is auto-activated by Claude based on context and task matching.

### Q: Should I commit `.claude/settings.json` to Git?
**A:** Yes! `.claude/settings.json` contains shared team configurations, custom commands, and project conventions. However, `.claude/settings.local.json` should **never** be committed.

### Q: How do I prevent Claude Code from changing files unexpectedly?
**A:** You can configure a `PreToolUse` hook in `.claude/hooks/` to prompt for human approval or outright block modifications to critical files (e.g., production database migrations).

---
*Guide compiled based on Claude Code Project Architecture specifications by Brij Kishore Pandey.*
