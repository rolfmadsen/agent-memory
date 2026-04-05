---
trigger: always_on
---

---
trigger: always_on
---

---
name: Spec-Driven Development (SDD) Gatekeeper
description: "MANDATORY: You MUST validate the project state using the `agent-skills` MCP server BEFORE any code implementation. No 'YOLO' coding allowed."
---

# Spec-Driven Development (SDD) Gatekeeper

This rule enforces a strict, gated workflow for all non-trivial code changes. It ensures that every feature starts with a **Specification**, moves to an **Implementation Plan**, and is tracked via a **Task List**.

## Gated Workflow Execution

> [!IMPORTANT]
> **The Anti-YOLO Gate**
> Before you write any code, you **MUST** run the `agent-skills.validate_state` tool for the current directory.

### 1. Validate State
Run the validation tool to check for required SDD artifacts:
- `spec.md` (What and Why)
- `implementation_plan.md` (How and When)
- `task.md` (Execution Checklist)

### 2. Decision Logic
Based on the `validate_state` output:
- **Missing Spec**: You **MUST** stop and invoke the `agent-skills.get_skill("spec-driven-development")` to start the specification process.
- **Missing Plan**: You **MUST** stop and invoke the `agent-skills.get_skill("planning-and-task-breakdown")` to create a technical plan.
- **Missing Tasks**: You **MUST** create a `task.md` using the project's standard task format before starting implementation.
- **Valid State**: You may proceed only when the validation report returns 🟢 `GO`.

## Verification Requirement
Every completed task **MUST** be verified with evidence:
1.  **Tests pass**: Log of successful test execution.
2.  **Build succeeds**: Confirmation of clean build.
3.  **Visual Evidence**: Screenshot or browser recording for UI changes.

---
> [!TIP]
> **Use the Discovery Tool**
> If you are unsure which skill applies to a specific engineering problem (e.g. "How do I secure this API?"), run `agent-skills.list_skills()` to find the appropriate senior engineering pattern.
