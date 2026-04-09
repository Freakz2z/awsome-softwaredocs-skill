<div align="center">

# awsome-softwaredocs-skill

**Professional Software Engineering Skill** — Build industry-standard software projects from scratch

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![UML 2.5](https://img.shields.io/badge/UML-2.5-green)]()

[简体中文](README.md)｜[English](README_EN.md)

*For Claude Code · Chinese & English · 9 Professional Documents · 6 UML Diagrams*

</div>

---

## Why awsome-softwaredocs-skill?

| Scenario | Without it | With it |
|----------|-----------|---------|
| **Learning Software Engineering** | Dry theory, hard to practice | Learn by doing, docs as textbook |
| **Capstone Project** | Don't know where to start | Complete templates, quick start |
| **Team Project** | Inconsistent, incomplete docs | One-click industrial-standard docs |
| **Freelance Project** | Client asks for docs, can't write | Professional templates, efficient delivery |

## Two Working Modes

```
┌─────────────────────────────────────────────────────────────┐
│  Mode 1: Step-by-Step Mode (Learning)                       │
│  ─────────────────────────────────────────────               │
│  Phase 1 Project Init → Phase 2 Requirements                │
│  → Phase 3 Architecture → Phase 4 Detailed Design            │
│  → Phase 5 Implementation → Phase 6 Unit Testing            │
│  → Phase 7 System Testing → Phase 8 Deployment               │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│  Mode 2: One-Click Mode (Quick Start)                      │
│  ─────────────────────────────────────────────               │
│  You provide: Project name + Type + Core features           │
│  Auto-generates: Complete structure + All docs + Code        │
└─────────────────────────────────────────────────────────────┘
```

## Installation

### Method 1: Install from Source

```bash
# Clone the repository
git clone https://github.com/Freakz2z/awsome-softwaredocs-skill.git

# Install the skill
mkdir -p ~/.claude/skills
cp -r awsome-softwaredocs-skill/skills/awsome-softwaredocs-skill ~/.claude/skills/
```

### Method 2: Install from Plugin Marketplace

```bash
# 1. Add the plugin marketplace
/plugin marketplace add https://github.com/Freakz2z/awsome-softwaredocs-skill

# 2. Install the skill
/plugin install awsome-softwaredocs-skill@awsome-softwaredocs-market
```

## Usage

Simply chat in Claude Code:

```
User: Create a task management system
User: Use one-click mode
User: Generate requirements specification
```

## Project Structure

```
awsome-softwaredocs-skill/
├── .claude-plugin/
│   ├── marketplace.json      # Marketplace config
│   └── plugin.json           # Plugin config
├── skills/
│   └── awsome-softwaredocs-skill/
│       ├── SKILL.md          # Skill definition
│       └── templates/        # Template directory
│           ├── zh/           # Chinese templates
│           │   ├── docs/     # 9 document templates
│           │   └── uml-diagrams/  # UML diagram templates
│           └── en/           # English templates
│               ├── docs/
│               └── uml-diagrams/
├── README.md
├── README_EN.md
├── CONTRIBUTING.md
├── CONTRIBUTING_EN.md
├── LICENSE
└── .gitignore
```

## Core Features

### 📄 Software Engineering Documents (9)

| Document | Code |
|----------|------|
| Software Requirements Specification | SRS |
| Software Design Specification | SDS |
| Database Design Specification | DD |
| Interface Design Specification | ID |
| Test Plan | TP |
| Test Report | TR |
| User Manual | UM |
| Project Plan | PP |
| Configuration Management Plan | CMP |

### 📊 UML Diagrams (6)

| Diagram | Use Case |
|---------|----------|
| Use Case | System functionality modeling |
| Class | Object-oriented design |
| Sequence | Object interaction timing |
| Activity | Business process |
| State | State machine |
| Deployment | System architecture |

### 💻 Supported Tech Stack

| Layer | Options |
|-------|---------|
| **Backend** | Java Spring Boot, Python Django, Go Gin, Node.js Express |
| **Frontend** | React, Vue 3, Vanilla HTML/JS |
| **Database** | MySQL, PostgreSQL, MongoDB, Redis |

## Reference Standards

| Standard | Description |
|----------|-------------|
| GB/T 8566-2007 | Software Life Cycle Processes |
| GB/T 9385-2008 | Computer Software Requirements Specification |
| GB/T 8567-2006 | Computer Software Design Description |
| ISO/IEC 25010 | Systems and Software Quality Requirements |
| UML 2.5 | Unified Modeling Language Specification |

---

For detailed development guide, see [CONTRIBUTING_EN.md](CONTRIBUTING_EN.md).

## License

MIT License · Copyright (c) 2026

## If Helpful, Please Give a ⭐

If awsome-softwaredocs-skill helps you, please give it a Star!
