# Academic Project Builder (Agent Skill)

> **Build complete, university-grade, viva-ready full-stack web applications from just an initial idea or topic prompt.**  
> A universal AI agent skill for **Google Antigravity** and **Claude Code**.

---

## 🎯 Overview

`academic-project-builder` is an autonomous workflow skill designed for AI programming agents (Antigravity and Claude). It equips the agent with end-to-end design patterns, single-command run architectures, and academic documentation standards necessary to generate undergraduate capstone projects that pass university evaluations with flying colors.

### The 6 Golden Rules Enforced:
1. **Zero External DB Daemons**: Uses embedded SQLite (`better-sqlite3`) that auto-creates and auto-seeds on first startup. No PostgreSQL/MySQL configuration nightmares.
2. **Single-Command Full-Stack Run**: Single root `package.json` with `npm run dev` starting both Express backend and Vite frontend concurrently.
3. **Collision-Free Port Assignment**: Checks available ports and isolates dev servers (`5001/5173`, `5002/5174`, `5003/5175`).
4. **Zero Paid API Lock-In**: Deterministic local heuristics, rule-based algorithms, and NLP dictionaries that run 100% offline and cost-free.
5. **1-Click Demo Profiles**: Pre-seeded demo user switcher in the navbar and login page for instant viva grading without creating accounts.
6. **Two Compulsory Documentation Deliverables**:
   - `README.md`: Problem statement, 1-command install, Mermaid architecture diagram, API table, demo credentials.
   - `DOCUMENTATION.md`: Academic SRS, Mermaid sequence diagrams, ERD with complete Data Dictionary, mathematical equations, and **20 university viva defense Q&As with model answers**.

---

## 📦 Repository Structure

```
academic-project-builder/
├── SKILL.md                          # Primary agent skill instructions & rules
├── README.md                         # Repository documentation
├── references/
│   ├── readme-template.md            # Standard-compliant university README blueprint
│   └── documentation-template.md     # Academic capstone DOCUMENTATION blueprint (with 20 viva Q&As)
└── templates/
    ├── package.json.template         # Single-root package (concurrently + Express + Vite + SQLite)
    ├── vite.config.js.template       # Zero-CORS dev server proxy configuration
    ├── db.js.template                # better-sqlite3 auto-seed connection module
    └── reset.js.template             # 1-command npm run db:reset script
```

---

## 🚀 Installation

### 1. For Google Antigravity
Clone or copy this folder into your global Antigravity skills directory:
```bash
git clone git@github.com:shahariartushar/academic-project-builder.git ~/.gemini/config/skills/academic-project-builder
```

### 2. For Claude Code
Clone or copy this folder into your global Claude skills directory:
```bash
git clone git@github.com:shahariartushar/academic-project-builder.git ~/.claude/skills/academic-project-builder
```

---

## 💡 Usage

In your AI assistant prompt, simply provide an initial concept:

> *"Using the academic-project-builder skill, create a university-ready project for: A Smart Campus Lost & Found Platform."*

The agent will automatically read `SKILL.md`, scaffold the architecture, build the full-stack code, seed the database, verify the build (`npm run build`), and generate complete academic documentation!

---

## 📄 License

MIT License. Open-source for students, educators, and developers worldwide.
