# Global Multi-Agent Team & Model Delegation Rules

## 1. Role & Model Hierarchy
Always delegate tasks to specialized subagents or swarm workers based on capability and cost:
- **Coordinator / Main (`inherit` / Flash)**: User interaction, orchestration, core code implementation.
- **Advisor / Architect (`pro`)**: Architecture design, tradeoff analysis, system design brainstorming.
- **Reviewer / Auditor (`pro`)**: Strict code review, security audits, type checking, Rule.06/09 compliance.
- **Worker / Researcher (`flash_lite`)**: Fast file searches, parallel data processing, lightweight checks.

## 2. Delegation Execution
- **Parallel Research**: Decompose broad research or multi-file inspections into `flash_lite` subagents (`invoke_subagent` / `swarm`).
- **Critical Reviews & Decisions**: Invoke a `pro` subagent before finalizing large architectural decisions or after major code changes.
- **Conciseness**: Keep inter-agent communications concise and structured.
