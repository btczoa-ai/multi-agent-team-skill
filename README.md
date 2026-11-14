# multi-agent-team-skill

A distribution skill repository for orchestrating **multi-model agent teams** (Coordinator, Advisor, Reviewer, Worker) across Antigravity projects, with 1-click global user setup for cross-terminal portability.

---

## Overview

Inspired by multi-model configurations in tools like Claude Code (Sonnet / Fable / Opus / Haiku), this skill establishes an efficient, cost-optimized, and high-precision delegation hierarchy on Antigravity:

| Role | Antigravity Model | Claude Analogy | Responsibilities |
|:---|:---|:---|:---|
| **Coordinator (Main)** | `inherit` / Flash | Sonnet | Direct user interaction, main orchestration, primary code implementation. |
| **Advisor (Architect)** | `pro` | Fable / Opus | High-level system architecture, tradeoff evaluation, design validation. |
| **Reviewer (Auditor)** | `pro` | Opus | Rigorous code review, security audit, type safety, refactoring verification. |
| **Worker (Subagent)** | `flash_lite` (or `flash`) | Haiku | Lightweight parallel file searches, batch text processing, quick lint/syntax checks. |

---

## Installation & Setup

### Method 1: Automatic Setup via Git Clone (Recommended for Any Machine)
Clone this repository to any environment and run the automated global installer:

```bash
git clone https://github.com/<your-username>/multi-agent-team-skill.git
cd multi-agent-team-skill
bash scripts/setup.sh
```

`setup.sh` automatically copies the lightweight, token-optimized delegation rule to:
1. `~/.gemini/config/rules/team_model_delegation.md` (Global rule directory)
2. `~/.gemini/AGENTS.md` (Global fallback rule)

All Antigravity sessions on that machine will immediately adopt this team configuration without further configuration.

### Method 2: Install via Skills Package Manager (`npx skills add`)
```bash
# Direct from GitHub repo
npx skills add <your-username>/multi-agent-team-skill

# Or from local clone
npx skills add ./multi-agent-team-skill
```

---

## Directory Structure

```text
multi-agent-team-skill/
├── README.md               # GitHub project documentation (Markdown)
├── html/
│   └── README.html         # Standalone HTML documentation (Rule.11 / Rule.12 Archetype C)
├── SKILL.md                # Root skill specification
├── skill.json              # Package metadata for skills package manager
├── scripts/
│   └── setup.sh            # Global 1-click setup script for new machines
├── templates/
│   └── team_model_delegation.md  # Token-efficient global rule template
└── skills/
    └── multi-agent-team/
        └── SKILL.md        # Nested skill entrypoint
```

---

## Documentation
For visual architecture diagrams and complete documentation, open [html/README.html](file://./html/README.html) in your browser.
