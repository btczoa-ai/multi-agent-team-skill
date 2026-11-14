---
name: multi-agent-team
description: Orchestrates and configures multi-model AI teams (Coordinator, Advisor, Reviewer, Worker) across Antigravity projects. Use when designing, spawning, or managing teams with distinct model roles (Flash, Pro, Flash-Lite) or configuring user-level team rules.
---

# Multi-Agent Team Orchestration Skill

Configure and orchestrate specialized multi-model agent teams inspired by Claude Code roles (Coordinator, Advisor, Reviewer, Worker) using Antigravity and Gemini models.

## Model Hierarchy & Role Mapping

| Role | Antigravity Model | Claude Analogy | Primary Responsibility |
|:---|:---|:---|:---|
| **Coordinator (Main)** | `inherit` / Flash | Sonnet | Direct user interaction, orchestrating workflow, core implementation. |
| **Advisor (Architect)** | `pro` | Fable / Opus | High-level system architecture, tradeoff evaluation, design validation. |
| **Reviewer (Auditor)** | `pro` | Opus | Rigorous code review, security audit, type safety, refactoring verification. |
| **Worker (Subagent)** | `flash_lite` (or `flash`) | Haiku | Lightweight parallel file searches, batch text processing, quick lint/syntax checks. |

## Execution Patterns

### 1. Dynamic Subagent Invocation (`invoke_subagent`)
Use `invoke_subagent` for focused, out-of-context tasks:
- **Architectural Brainstorming:**
  ```json
  {
    "TypeName": "self",
    "Role": "System Architect",
    "Model": "pro",
    "Prompt": "Analyze the tradeoffs between approach A and approach B for..."
  }
  ```
- **Code Audit:**
  ```json
  {
    "TypeName": "self",
    "Role": "Strict Code Reviewer",
    "Model": "pro",
    "Prompt": "Review git diff for security vulnerabilities, edge cases, and compliance with Rule.06/Rule.09."
  }
  ```
- **Batch / Parallel Search:**
  ```json
  {
    "TypeName": "research",
    "Role": "Codebase Investigator",
    "Model": "flash_lite",
    "Prompt": "Find all usages of deprecated API X across the repository."
  }
  ```

### 2. Live Collaborative Swarm (`swarm`)
When agents need to collaborate asynchronously via a shared message board:
```bash
# Add Architect / Advisor
swarm action="add" name="advisor" model="pro" brief="You are the system architect. Review design proposals and advise on tradeoffs."

# Add Strict Reviewer
swarm action="add" name="reviewer" model="pro" brief="You are the auditor. Inspect all code changes and enforce quality standards."

# Add Parallel Workers
swarm action="add" name="worker" n=3 model="flash_lite" brief="Execute lightweight batch tasks and run tests."
```

## Global Machine Setup
To configure this team protocol machine-wide across all workspaces:
```bash
bash scripts/setup.sh
```
This populates `~/.gemini/config/rules/team_model_delegation.md` and appends to `~/.gemini/AGENTS.md`.
