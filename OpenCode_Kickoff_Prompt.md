# OpenCode Project Kickoff Prompt Template

Use this document to initiate new PHP/MySQL projects with OpenCode in your XAMPP local environment.

---

## 📋 How to Use
1. Copy the prompt template below.
2. Replace the bracketed placeholders `[ ... ]` with your specific project details.
3. Place `XAMPP_PHP_MySQL_OpenCode_Guide.md` in your project root directory (`C:\xampp\htdocs\your-project-name\`).
4. Paste the prompt into OpenCode.

---

## 🚀 Copy-Paste Prompt Template

```markdown
I want to start developing a new project. I am attaching my project guidelines from `XAMPP_PHP_MySQL_OpenCode_Guide.md`. Please read and strictly adhere to all instructions, architectural constraints, and coding standards outlined in that guide.

### 1. Project Overview
- **Project Name:** [Insert Project Name]
- **Target Location / Port:** `http://localhost/[your-folder-name]`
- **Core Idea & Goal:** [Describe what the application does, who it is for, and the core workflow it solves]

### 2. Key Features & Capabilities
1. **Authentication & Roles:** [e.g., Admin / User role access control]
2. **Core Workflow:** [e.g., File tracking, client management, form submission]
3. **Data Storage:** [e.g., Storing structured client data in MySQL with status flags]
4. **Export / Reporting:** [e.g., Generate PDF reports or Word documents]

### 3. Immediate Action Plan Required
Before writing complete feature files, please execute the following steps:

1. **Rule Verification:** Acknowledge that you have loaded `XAMPP_PHP_MySQL_OpenCode_Guide.md` and list the primary tech stack rules (PHP version, PDO usage, folder structure).
2. **Database Schema:** Provide the initial SQL creation script (`schema.sql`) tailored for MySQL on XAMPP.
3. **Project Structure:** Output the full directory tree structure (MVC / modular format).
4. **Boilerplate Setup:** Generate the core configuration files:
   - `config/db.php` (PDO database connection with error handling)
   - `.env` / configuration constants template
   - `public/index.php` or main entry point router

Wait for my review and approval of the database schema before writing the full CRUD logic.
```

---
