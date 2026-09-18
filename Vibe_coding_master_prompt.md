
# VIBECODING_MASTER_GUIDE.md
# The Complete 6-Document Framework for AI-Driven Software Engineering

---

## Table of Contents
1. [Framework Overview](#1-framework-overview)
2. [Document 1: Product Requirements Document (PRD)](#document-1-product-requirements-document-prd)
3. [Document 2: Technical Requirements Document (TRD)](#document-2-technical-requirements-document-trd)
4. [Document 3: Appflow & User Journey](#document-3-appflow--user-journey)
5. [Document 4: UI/UX Design Brief](#document-4-uiux-design-brief)
6. [Document 5: Backend Schema](#document-5-backend-schema)
7. [Document 6: Implementation Plan](#document-6-implementation-plan)
8. [AI Integration & Execution Playbook](#ai-integration--execution-playbook)
    * [Repository File Layout](#repository-file-layout)
    * [Cursor IDE Setup (.cursorrules)](#cursor-ide-setup-cursorrules)
    * [Claude Code Setup (CLAUDE.md)](#claude-code-setup-claudemd)
    * [OpenCode & Agent Setup (AGENTS.md)](#opencode--agent-setup-agentsmd)
    * [Phase-by-Phase AI Master Prompts](#phase-by-phase-ai-master-prompts)

---

## 1. Framework Overview

Vibecoding without structural documentation leads to architectural decay, context rot, and hallucinations. AI models (Claude 3.5, GPT-4o, Cursor, OpenCode) require deterministic boundary conditions to build scalable applications without guessing.

By preparing six standardized documents before generating code, you establish an immutable source of truth for the AI agent.

```text
       [ 1. PRD ] ------------+
       [ 2. TRD ] ------------|
       [ 3. Appflow ] --------+---> [ /docs Repository Context ] ---> [ AI Coding Agent ]
       [ 4. UI/UX Brief ] ----|                                        (Claude / Cursor / OpenCode)
       [ 5. Schema ] ---------|
       [ 6. Plan ] -----------+

```
## Document 1: Product Requirements Document (PRD)
### Purpose
Establishes the functional scope, target goals, core features, and success metrics. It tells the AI **what** to build and **why**.
### Specification Template
```markdown
# Product Requirements Document (PRD)

## 1. Overview
Brief, high-level summary of the product core value proposition.

## 2. Goals & Objectives
* Metric-driven goal 1
* Metric-driven goal 2

## 3. User Personas & Target Audience
* Primary User Profile
* Secondary User Profile

## 4. Functional & Non-Functional Requirements
### Functional Requirements
- [ ] User Authentication & Authorization
- [ ] Core Feature A
- [ ] Core Feature B

### Non-Functional Requirements
- Performance: Page loads < 1.5s
- Security: Role-Based Access Control (RBAC)
- Scalability: Up to 10k concurrent users

## 5. Success Metrics (KPIs)
* Daily Active Users (DAU)
* Feature Retention Rate

```
### Complete Working Example (TaskSocial)
```markdown
# PRD: TaskSocial

## 1. Overview
TaskSocial is a hybrid productivity and social networking application designed to help users track personal goals while sharing verified progress with an accountability community.

## 2. Goals & Objectives
* Increase daily user task completion rates by 30% through peer accountability.
* Reach 10,000 Monthly Active Users (MAU) within 90 days post-launch.

## 3. Requirements
### Functional
* **Task Management:** Create, update, tag, and organize tasks with privacy toggles (Public/Private).
* **Social Feed:** Share completed tasks as feed updates; allow followers to like and comment.
* **Direct Messaging:** Real-time 1-on-1 messaging between connected users.

### Non-Functional
* Mobile feed initial load time under 1.2 seconds.
* 99.9% uptime SLA using managed serverless infrastructure.

## 4. User Experience & Gamification
* Achievement badges awarded upon hitting completion streaks (3-day, 7-day, 30-day).
* Interactive progress bars visible on public user profiles.

## 5. Success Metrics
* Task Completion Ratio = (Tasks Completed / Tasks Created) * 100
* Social Engagement Index = (Comments + Likes) per Active User

```
## Document 2: Technical Requirements Document (TRD)
### Purpose
Defines the software architecture, language runtimes, libraries, databases, third-party APIs, and deployment infrastructure. It prevents the AI from switching frameworks or picking incompatible dependencies mid-build.
### Complete Technology Selection Matrix
| Architectural Layer | Choice | Justification & Technical Constraints |
|---|---|---|
| **Web Frontend** | React / TypeScript / Tailwind CSS | Strict typing with TypeScript; utility-first styling for rapid layout building. |
| **Mobile App** | React Native (Expo) | Single codebase cross-compiling to iOS and Android. |
| **Backend Service** | Node.js (Express) or Python (FastAPI) | Node.js for event-driven API; Python for data processing background tasks. |
| **Relational Database** | PostgreSQL | ACID compliance, robust indexing, relational data integrity. |
| **Caching & In-Memory** | Redis | Real-time session management and feed caching. |
| **Cloud Deployment** | AWS (EC2, RDS, S3) / Vercel | Scalable container/serverless infrastructure. |
### Complete Working Example (TRD File)
```markdown
# Technical Requirements Document (TRD)

## 1. Core Stack
* Frontend: React 18 with TypeScript 5, Tailwind CSS
* Mobile: React Native with Expo SDK 51
* Backend: Node.js (Express.js) REST API
* Database: PostgreSQL 16 managed on AWS RDS
* Caching: Redis 7.2
* Cloud Storage: AWS S3 for media uploads

## 2. Architecture & API Design
* RESTful JSON API endpoints structured under `/api/v1/`.
* JWT (JSON Web Tokens) stored in HttpOnly cookies for web, SecureStore for React Native.
* CORS strictly configured for domain white-labeling.

## 3. Technical Constraints for AI Developers
* Do NOT introduce ORMs other than Prisma.
* Use Zod for schema validation on all incoming API request payloads.
* All async endpoints must be wrapped in standard error-handling middleware.

```
## Document 3: Appflow & User Journey
### Purpose
Maps out screen-by-screen state transitions and user flow actions. It guarantees the AI builds coherent routing logic and state management.
### User Journey Sequence Chart
```text
[ Splash Screen ] ---> [ Auth Router ]
                             |---> (Unauthenticated) ---> [ Sign Up ] ---> [ Email OTP ] ---> [ Onboarding ] ---> [ Home Feed ]
                             |---> (Authenticated)   --------------------------------------------------------> [ Home Feed ]

```
### Complete Working Example (Appflow File)
```markdown
# Appflow & User Navigation Matrix

## Screen 1: Splash Screen
* **Purpose:** Initial application loading and session detection.
* **Logic:** Checks local token storage. If valid token exists -> Navigate to Screen 5. Else -> Navigate to Screen 2.

## Screen 2: Sign Up / Create Account
* **Fields:** Full Name, Email Address, Password, Confirm Password.
* **Actions:**
  * Click `Sign Up` -> Validate fields via Zod -> Call `/api/v1/auth/signup` -> Navigate to Screen 3.
  * Click `Social Auth (Google/Apple)` -> Trigger OAuth SDK -> Navigate to Screen 5.

## Screen 3: Verify Email
* **Fields:** 6-Digit OTP Code Input.
* **Logic:** Auto-submit on 6th digit entry. Success -> Navigate to Screen 4. Error -> Display toast.

## Screen 4: Onboarding Flow
* **Step 1:** Intro screen explaining social accountability.
* **Step 2:** User selects 3 initial goal categories.
* **Step 3:** Request System Notifications permission -> Navigate to Screen 5.

## Screen 5: Home Dashboard & Feed
* **Header:** Search Bar, Notification Bell.
* **Body:** Tabbed view switching between "My Tasks" and "Community Feed".
* **Bottom Bar:** Home, Explore, New Task (+), Chat, Profile.

```
## Document 4: UI/UX Design Brief
### Purpose
Defines the visual rules, typography scales, color schemes, component states, and spacing constraints. Prevents the AI from outputting inconsistent UI components.
### Specification Blueprint
```markdown
# UI/UX Design System Brief

## 1. Color System
* Primary Action: `#6200EA` (Electric Purple)
* Primary Hover: `#3700B3`
* Secondary Accent: `#03DAC6` (Teal)
* Dark Background: `#121212`
* Light Background: `#F8F9FA`
* Surface Card: `#FFFFFF`
* Success: `#4CAF50` | Warning: `#FF9800` | Error: `#F44336`

## 2. Typography Scale
* Font Family: `Inter`, `SF Pro Display`, sans-serif
* Display (H1): 32px / Bold / Line Height 1.2
* Section (H2): 24px / SemiBold / Line Height 1.3
* Subtitle (H3): 18px / Medium / Line Height 1.4
* Body Text: 14px / Regular / Line Height 1.5
* Caption / Meta: 12px / Light / Line Height 1.4

## 3. UI Component Library Rules
* Buttons: Border radius `8px` (`rounded-lg`). Padding `px-4 py-2`.
* Input Fields: Height `44px`, border `1px solid #E0E0E0`, focus ring `#6200EA`.
* Cards: Shadow `0 2px 8px rgba(0,0,0,0.08)`, padding `16px`, border-radius `12px`.

## 4. Feedback Components
* Toasts: Top-right positioning, auto-dismiss after 3000ms.
* Modals: Center overlay with dark background backdrop blur (`backdrop-blur-sm`).

```
## Document 5: Backend Schema
### Purpose
Defines relational database structure, entity relations, data types, primary/foreign keys, and indexes.
### Entity Relationship Diagram (ERD) Representation
```text
 [ USERS ] 1 ──── N [ POSTS ] 1 ──── N [ COMMENTS ]
    │                 │
    │ 1               │ 1
    N                 N
 [ FOLLOWERS ]     [ LIKES ]

```
### Complete Working Example (Backend Schema File)
```markdown
# Database Schema & Data Models

## USERS Table
| Column Name | Type | Constraints | Description |
| :--- | :--- | :--- | :--- |
| `id` | UUID | Primary Key, Default gen_random_uuid() | Unique User Identifier |
| `email` | VARCHAR(255) | Unique, Not Null | User login email |
| `password_hash`| VARCHAR(255) | Not Null | Bcrypt hashed password |
| `full_name` | VARCHAR(100) | Not Null | Display name |
| `avatar_url` | TEXT | Nullable | S3 bucket URL |
| `created_at` | TIMESTAMP | Default NOW() | Account creation date |

## POSTS Table
| Column Name | Type | Constraints | Description |
| :--- | :--- | :--- | :--- |
| `id` | UUID | Primary Key | Post ID |
| `user_id` | UUID | Foreign Key -> USERS(`id`) | Author reference |
| `title` | VARCHAR(200) | Not Null | Task post title |
| `content` | TEXT | Nullable | Detailed breakdown |
| `is_public` | BOOLEAN | Default TRUE | Visibility flag |
| `created_at` | TIMESTAMP | Default NOW() | Post timestamp |

## FOLLOWERS Table (Many-to-Many)
* `follower_id` (UUID, Foreign Key -> USERS(`id`))
* `following_id` (UUID, Foreign Key -> USERS(`id`))
* Primary Key: (`follower_id`, `following_id`)

## MESSAGES Table
* `id` (UUID, PK)
* `chat_id` (UUID, Not Null)
* `sender_id` (UUID, FK -> USERS(`id`))
* `content` (TEXT, Not Null)
* `created_at` (TIMESTAMP)

```
## Document 6: Implementation Plan
### Purpose
Defines the execution roadmap into sequential, atomic build phases so the AI agent works incrementally without skipping necessary foundations.
### 5-Phase Roadmap
```text
Phase 1: Planning (1 Week)
  └── Phase 2: Requirements & Architecture (1-2 Weeks)
        └── Phase 3: Design & Component Blueprinting (2-3 Weeks)
              └── Phase 4: Development & API Integration (4-10 Weeks)
                    └── Phase 5: Testing, Hardening & Deployment (2-3 Weeks)

```
### Implementation Task Breakdown
```markdown
# Implementation Plan & Milestone Execution

## Phase 1: Planning
- [x] Finalize application scope and core user value proposition.
- [x] Define success criteria and project timelines.

## Phase 2: Requirements & Infrastructure Setup
- [ ] Initialize Git repository with standard directory structure.
- [ ] Configure PostgreSQL database instance and ORM migrations.
- [ ] Setup authentication API routes (`/signup`, `/login`, `/refresh`).

## Phase 3: Design System & Frontend Shell
- [ ] Implement Tailwind configuration with exact hex palette and spacing rules.
- [ ] Build reusable UI primitives (Button, Input, Card, Modal, Toast).
- [ ] Construct screen routing according to the Appflow specification.

## Phase 4: Core Development
- [ ] Task Management CRUD module (API + UI).
- [ ] Social Feed rendering with Redis cached data.
- [ ] Real-time messaging engine using WebSockets/Socket.io.

## Phase 5: Testing & Deployment
- [ ] Run unit and integration tests (Jest / Vitest).
- [ ] Execute security audits on API auth headers and database rules.
- [ ] CI/CD pipeline setup for automated deployment to production.

```
## AI Integration & Execution Playbook
### Repository File Layout
Keep all system design documents in a centralized directory at the root of your project:
```text
/my-app-repo
├── /docs
│   ├── 1_PRD.md
│   ├── 2_TRD.md
│   ├── 3_APPFLOW.md
│   ├── 4_DESIGN_BRIEF.md
│   ├── 5_BACKEND_SCHEMA.md
│   └── 6_IMPLEMENTATION_PLAN.md
├── .cursor/
│   └── rules/
│       └── project-rules.mdc
├── CLAUDE.md
├── AGENTS.md
└── src/

```
### Cursor IDE Setup (.cursorrules)
Create .cursorrules or .cursor/rules/project-rules.mdc in your project root:
```markdown
---
description: Vibecoding Architectural Enforcement Rules
globs: **/*
---

# Cursor AI Instructions

1. ALWAYS reference files in `/docs/` before generating code.
2. Maintain technical choices specified in `docs/2_TRD.md`.
3. Follow color codes and typography guidelines in `docs/4_DESIGN_BRIEF.md`.
4. Validate database queries against `docs/5_BACKEND_SCHEMA.md`.
5. Execute features strictly in accordance with `docs/6_IMPLEMENTATION_PLAN.md`.
6. DO NOT install new dependencies or third-party packages without explicit approval.

```
### Claude Code Setup (CLAUDE.md)
Place a CLAUDE.md file in the repository root to control Claude CLI and Agent behavior:
```markdown
# CLAUDE.md - Project Guidelines

## Project Context
Refer to `/docs` for full system architecture specifications.

## Execution Rules
- Before writing code, run a plan analysis against `docs/6_IMPLEMENTATION_PLAN.md`.
- Match TypeScript types directly to database tables defined in `docs/5_BACKEND_SCHEMA.md`.
- All styling must strictly utilize Tailwind utility classes defined in `docs/4_DESIGN_BRIEF.md`.

## Build & Test Commands
- Build: `npm run build`
- Dev Server: `npm run dev`
- Run Tests: `npm run test`

```
### OpenCode & Agent Setup (AGENTS.md)
Create AGENTS.md for OpenCode or multi-agent CLI automation tools:
```markdown
# AGENTS.md - Multi-Agent Operating Instructions

## Role Definitions
* **Architect Agent:** Reads `docs/1_PRD.md`, `docs/2_TRD.md`, `docs/5_BACKEND_SCHEMA.md`. Generates project boilerplate and database migration files.
* **Frontend Agent:** Reads `docs/3_APPFLOW.md` and `docs/4_DESIGN_BRIEF.md`. Builds UI components, screens, and routes.
* **Backend Agent:** Reads `docs/2_TRD.md` and `docs/5_BACKEND_SCHEMA.md`. Builds API controllers, services, and middleware.

## Execution Hierarchy
1. Architect Agent completes database setup.
2. Backend Agent builds endpoints and tests API.
3. Frontend Agent connects UI components to verified backend routes.

```
### Phase-by-Phase AI Master Prompts
#### Prompt 1: Initial Repository & Database Setup
> "Read /docs/2_TRD.md and /docs/5_BACKEND_SCHEMA.md. Generate the database initialization scripts and ORM schemas (Prisma/SQL). Ensure all primary keys, foreign key constraints, indexes, and timestamp fields match the schema document exactly."
> 
#### Prompt 2: Core Component & UI Creation
> "Read /docs/4_DESIGN_BRIEF.md and /docs/3_APPFLOW.md. Create the core UI component library (Buttons, Inputs, Cards, Modals) using the exact color codes, typography, border radiuses, and spacing specified in the design brief."
> 
#### Prompt 3: Feature Implementation
> "Refer to step 1 of Phase 4 in /docs/6_IMPLEMENTATION_PLAN.md. Implement the user task creation module. Use the backend schema in /docs/5_BACKEND_SCHEMA.md for data types and ensure input fields validate using the Zod rules established in the TRD."
> 
```
