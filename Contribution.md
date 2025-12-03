## Contributing Guidelines

Welcome to the web dev roadmap repository by **Arya (@aryagupta164)** and **Avirupa (@avirupamalakar)**.
This document explains how we work, how to structure code, and how to review each other’s work.

---

## 🎯 Repo Goals

Learn web development step by step using phases.

Each phase includes:

* A shared `README.md` (goals, notes, resources)
* A folder for **Arya**
* A folder for **Avirupa**
* An optional `shared/` folder for polished joint work
* Every project goes through a **PR + code review** by the other person

---

## 📁 Repository Structure

```
.
├── .gitignore
├── Contribution.md
├── 1-Web-Foundations/
│   ├── README.md
│   ├── 1-PhaseTest/
│   │   ├── README.md
│   │   ├── Arya/
│   │   └── Avirupa/
│   └── 1.1-Web_Foundations_Learning/
├── 2-HTML+CSS/
│   ├── README.md
│   └── 2-PhaseTest/
│       ├── README.md
│       ├── Arya/
│       └── Avirupa/
├── 3-Responsive+Advanced_CSS+Animations+3D/
├── 4-Mastering-JavaScript/
├── 5-React/
├── 6-Polyglot-backend/
├── 7-Backend_Engineering/
├── 8-Databases/
├── 9-Security+Auth+Production+Production_Hardening/
├── 10-Full-Stack-Major-Projects/
├── 11-Cross_Platform+AI_ML+WebRTC+High_Scale_System_Design/
├── 12-WEB3_Engineering/
└── 13-Game_Development/
```

### Naming Rules

**Phases:**
`X-Phase-Topic-Name` (where X is the phase number)

**Phase Tests:**
`X-PhaseTest/` (contains practical projects)

Inside each PhaseTest:

```
Arya/
Avirupa/
```

Projects:
`project-short-name`
Example: `project-todo-app`

---

## 🌿 Branching Strategy

### `main`

* Always stable, working code
* Never commit directly — use PRs

### Feature Branch Naming

```
arya/X-phase-short-description
avirupa/X-phase-short-description
shared/X-phase-short-description
```

Examples:

* `arya/1-web-foundations-landing-page`
* `avirupa/2-html-css-portfolio`
* `shared/4-javascript-final-project`

### Commands

Create branch:

```
git checkout -b arya/1-web-foundations-landing-page
```

Push branch:

```
git push -u origin arya/1-web-foundations-landing-page
```

---

## 🐞 Issues & Milestones

Create an Issue for each project:

* **Phase 1**: Arya – Web Foundations Project
* **Phase 2**: Avirupa – HTML+CSS Layout

Labels to use:

* `phase-1`, `phase-2`, `phase-3`, etc.
* `arya`, `avirupa`
* `project`, `bug`, `enhancement`

Optional Milestones:

* Phase 1 – Web Foundations
* Phase 2 – HTML+CSS
* Phase 4 – Mastering JavaScript
* Phase 5 – React

---

## 💬 Commit Message Conventions

### Good Examples

```
Phase 1: add hero section markup
Phase 2: implement responsive card grid
Phase 4: add JavaScript functionality
```

### Closing Issues

```
Phase 1: finalize layout (closes #7)
```

---

## 🎨 Code Style Guide

### HTML

* Use semantic tags
* Every image must have `alt` text
* Proper indentation
* Clear class names

### CSS

* Prefer external `.css` files
* `kebab-case` class naming
* Keep selectors simple and readable

### JavaScript

* Use `const`/`let` only
* Small, focused functions
* Descriptive variable names

---

## 🔄 Per-Phase Workflow

1. Create/update the phase folder on `main`
2. Add or update `README.md` with goals, tasks, notes
3. Create Issues for each project
4. Create feature branches
5. Work only inside your own folder (`Arya/` or `Avirupa/`) within the PhaseTest directory
6. Open a PR and request review
7. Reviewer checks and approves
8. Merge to `main`

---

## 🔧 Pull Request (PR) Guidelines

### PR Title Examples

* Phase 1 – Arya Web Foundations Project
* Phase 2 – Avirupa HTML+CSS Layout
* Phase 4 – Arya JavaScript Implementation

### PR Template

**Summary**
Short description.

**Changes**

* Bullet points
* List modifications clearly

**Checklist**

```
[ ] Code runs locally  
[ ] No console errors  
[ ] Naming conventions followed  
[ ] Phase README updated  
[ ] Screenshots added (optional)  
```

**Notes for reviewer**
Ask for specific feedback.

### Review Process

* Reviewer runs the project locally
* Comments on:

  * HTML semantics
  * CSS layout
  * Code readability
* Approve or request changes

---

## 🤝 Shared Final Versions

For joint polished work:

* Create branch: `shared/X-phase-final-project`
* Work inside `X-Phase-Name/shared/` (if shared folder exists)
* Combine best ideas
* Open PR reviewed by **both** contributors

---

## ➕ Adding a New Phase

Create folder:

```
X-Phase-Topic-Name/
├── README.md
├── X-PhaseTest/
│   ├── README.md
│   ├── Arya/
│   └── Avirupa/
└── X.X-Subtopic_Learning/ (optional)
```

### The `README.md` must include:

* Goals
* Topics
* Tasks for both contributors
* Shared notes section

---

## 🖥️ Local Setup

```
npm install
npm run dev
npm run lint
npm test
```

For plain HTML/CSS:

* Open `index.html` in browser
* Or use Live Server

---

## 🌟 Mini Code of Conduct

* Be respectful in comments
* Feedback should help and clarify
* Ask questions instead of assuming
* Celebrate progress

---

**Happy hacking and learning! 🚀**
*End of CONTRIBUTING.md*

---

If you want, I can also:

✔ Automatically generate a `CONTRIBUTING.md` file in your repo format
✔ Turn this into a PDF / webpage version
✔ Create a PR template file (`.github/pull_request_template.md`)
✔ Create issue templates too

Just tell me!
