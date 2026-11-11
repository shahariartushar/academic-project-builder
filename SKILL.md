---
name: academic-project-builder
description: Build complete, university-grade, viva-ready full-stack web applications from just an initial idea or topic. Generates zero-config single-command architectures (Node.js + Express + React + SQLite), comprehensive academic documentation (README.md, DOCUMENTATION.md with Mermaid diagrams, ERD, data dictionary, and 20 viva defense Q&As), pre-seeded realistic university datasets, 1-click evaluation demo personas, and collision-free port assignments.
---

# Academic Project Builder

Transform an initial project idea, course prompt, or topic into a **complete, production-grade, university-ready capstone web application** with working frontend, backend, zero-config database, demo personas, and comprehensive academic documentation.

---

## 🏛️ The 6 Golden Rules of Academic Projects

Every project generated with this skill **MUST** strictly adhere to these six engineering standards:

1. **Zero External Database Daemons (Embedded SQLite):**
   - NEVER require PostgreSQL, MySQL, or MongoDB daemons to be installed or running locally.
   - Use embedded `better-sqlite3`. On server startup, the database file must **auto-create tables from schema.sql** and **auto-seed realistic sample data** if empty.
   - Include `npm run db:reset` to wipe and restore fresh demo data instantly.

2. **Single-Command Full-Stack Execution:**
   - Both client and server must be managed from a single root `package.json`.
   - Running `npm run dev` (via `concurrently`) starts both the Express API and the Vite frontend dev server in one terminal.

3. **Collision-Free Port Assignment:**
   - Never hardcode conflicting ports. Check existing processes (`lsof -i :<port>`).
   - Assign dedicated backend (e.g. `5001`, `5002`, `5003`) and frontend ports (e.g. `5173`, `5174`, `5175`).
   - Configure Vite's dev proxy (`vite.config.js`) so frontend `/api/*` calls proxy seamlessly to the backend server.

4. **Zero Paid API Lock-In:**
   - The core functionality must run 100% offline and cost-free without depending on external paid AI API keys (OpenAI, Gemini, Claude, AWS).
   - Use deterministic pattern matching, rule-based NLP dictionaries, scoring heuristics, or local algorithms. Document how LLMs can be plugged in as an optional enhancement.

5. **1-Click Evaluation Personas:**
   - Evaluators, professors, and viva examiners will not spend time registering new accounts or typing passwords.
   - Always provide a **"Demo Profiles"** dropdown in the Navbar and **"Autofill"** buttons on the Login page with at least 3 distinct personas (e.g. Student 1, Student 2, Admin / Officer).

6. **Two Compulsory Academic Documentation Files:**
   - **`README.md`**: Project overview, problem statement, demo credentials table, 1-command install, high-level architecture diagram, core features, and REST API table.
   - **`DOCUMENTATION.md`**: Academic capstone specification including SRS, high-level architecture with Mermaid diagrams, sequence diagrams, ERD with full Data Dictionary, mathematical/algorithmic formulations, security model, and **20 university viva defense Q&As with model answers**.

---

## 📋 End-to-End Build Process

### Phase 1: Idea Synthesis & Scope Modeling
From a simple user prompt (e.g., *"Create an event ticketing app for campus"* or *"A lost and found portal"*):
1. Determine the core problem statement and academic domain.
2. Formulate 3–5 primary entities (e.g. Users, Items, Claims, Logs).
3. Plan distinct visual branding:
   - Select a custom color theme (e.g. Forest Teal for safety, Deep Indigo for career, Crimson/Navy for university).
   - Choose modern Google Fonts (e.g. `Plus Jakarta Sans`, `Space Grotesk`, `Outfit`).

### Phase 2: Project Scaffolding
Create the standard root directory layout:
```
<project-name>/
├── package.json              # Single root package managing client & server
├── vite.config.js            # Vite dev proxy configuration
├── .gitignore                # node_modules, *.sqlite, dist, .DS_Store
├── .nvmrc                    # Target Node.js version (e.g. 20 or 22)
├── README.md                 # Professional overview & quick start
├── DOCUMENTATION.md          # Comprehensive academic capstone defense guide
├── server/
│   ├── server.js             # Express API entry point & session config
│   ├── middleware/auth.js    # Session auth & role verification
│   ├── database/
│   │   ├── schema.sql        # SQLite table definitions with foreign keys
│   │   ├── seed.js           # Rich pre-loaded university demo dataset
│   │   ├── db.js             # better-sqlite3 connection & auto-seed trigger
│   │   └── reset.js          # Database reset & re-seed script
│   ├── routes/               # Modular REST API endpoints (/auth, /entities, /stats)
│   └── services/             # Core algorithms (matching, scoring, parsing)
└── client/
    ├── index.html            # Single page entry HTML
    └── src/
        ├── main.jsx          # React DOM entry point
        ├── App.jsx           # React Router v6 routing & layout shell
        ├── styles/main.css   # Self-contained modern CSS design system
        ├── context/AuthContext.jsx # Global user session & auth state
        ├── services/api.js   # Fetch client with credentials: 'include'
        ├── components/       # Navbar, Footer, Badges, Modals, Cards
        └── pages/            # Home, Browse, Detail, Create/Action, Dashboard, Auth
```

### Phase 3: Database & Backend Architecture
1. **Schema Definition (`server/database/schema.sql`):**
   - Enable `PRAGMA foreign_keys = ON;`
   - Include `users` table with bcrypt password hashes and roles (`student`, `faculty`, `admin`, etc.).
   - Include primary domain tables with explicit foreign key constraints (`ON DELETE CASCADE`).
   - Include an `activity_logs` table for automated audit trailing.
2. **Auto-Seeding Engine (`server/database/seed.js`):**
   - Check if database has records; if empty, insert 3+ realistic users (using `bcrypt.hashSync('password123', 10)`).
   - Seed 8–15 realistic domain items across various states (e.g. Active, Pending, Completed, Archived).
3. **Connection Module (`server/database/db.js`):**
   - Instantiate `new Database(dbPath)`.
   - Read and execute `schema.sql`, then trigger `seedDatabase(db)`.
4. **Session Authentication & Controllers:**
   - Configure `express-session` with `cookie: { httpOnly: true, sameSite: 'lax' }`.
   - Implement `GET /api/auth/me`, `POST /api/auth/login`, `POST /api/auth/register`, `POST /api/auth/logout`, and `GET /api/auth/demo-users`.
   - Implement domain CRUD routes with input validation and filtering.

### Phase 4: Frontend Client & High-Contrast UI
1. **Self-Contained Design System (`client/src/styles/main.css`):**
   - Define CSS custom properties (`--primary`, `--primary-light`, `--bg-page`, `--text-main`, `--radius-lg`, `--shadow-card`).
   - Do not rely on external CSS bundlers or PostCSS plugins that might fail to compile; use clean, native CSS with utility classes.
2. **Interactive Components:**
   - **Navbar**: Logo, dynamic navigation links, user profile avatar, and the **Demo Profiles** 1-click switcher.
   - **StatusBadge**: Distinct pill badges for entity states.
   - **Hero Section**: Tagline badge, bold heading, short overview, quick search or CTAs, and live summary stats card.
   - **Detail & Action Modals**: Clean form controls with validation and error alerts.
   - **Analytics Dashboard**: Metric summary boxes, category breakdown bars, and recent audit feed.

### Phase 5: Academic Documentation Deliverables
Always generate both documentation documents in full markdown:

#### 1. `README.md` Structure:
- 🎯 **1. Project Overview & Problem Statement:** Academic context and concrete problem solved.
- 🚀 **2. Quick Start & Installation:** 1-command install (`npm install`), run (`npm run dev`), and browser URL.
- 🔑 **3. Demo Credentials Table:** Role, Name, Email, Password, and pre-loaded scenario context.
- 🏗️ **4. System Architecture Diagram:** Mermaid flowchart of Client, Server, and Embedded Data tiers.
- ✨ **5. Core Features:** Detailed breakdown of top 4 features.
- 📂 **6. Project Directory Structure:** Full ASCII tree of key files.
- 📡 **7. REST API Reference:** Table of endpoints, methods, access levels, and descriptions.
- 🛠️ **8. Useful NPM Scripts:** `dev`, `server`, `client`, `build`, `preview`, `db:reset`.

#### 2. `DOCUMENTATION.md` Structure:
- **1. Executive Summary & Problem Motivation:** In-depth academic justification.
- **2. High-Level Architecture & Tech Justifications:** Why React, Vite, Express, and SQLite were chosen.
- **3. Deep-Dive Feature Specifications:** End-to-end functionality breakdown.
- **4. System Workflows & Mermaid Sequence Diagrams:** At least two sequence diagrams illustrating critical user flows.
- **5. Database Design & Data Dictionary:** Mermaid ERD and tables listing every column, data type, constraint, and description.
- **6. Algorithmic / Mathematical Formulation:** Explicit scoring or matching equations with KaTeX formulas.
- **7. Complete REST API Specification:** Full endpoints, request/response formats.
- **8. University Viva & Presentation Defense Guide (20 Q&A):** 20 rigorous questions and comprehensive model answers covering architecture, design decisions, security, scaling, and future work.

### Phase 6: Verification & Git Protocol
1. Execute `npm run build` using the run_command tool to ensure the Vite production build succeeds with 0 errors.
2. Start the Express server briefly, test `/api/health` and `/api/stats/overview`, and verify auto-seeding.
3. If running inside a multi-account Git environment:
   - Check local git configurations (`git config user.name`, `git config user.email`).
   - Add all files, commit with a descriptive conventional commit message (`feat: complete ...`), and push to the remote repository.
