# CODEX.md

A continuación tienes una **plantilla de `CODEX.md` lista para usar**, diseñada **específicamente para Codex**, alineada con **Context Engineering + FIC**, y **optimizada para sobrevivir a resets de contexto**.

## Purpose

This document defines **global, always-applicable rules** for how Codex must reason, plan, and implement code in this repository.

These rules apply **across all sessions**, **all phases**, and **all tasks**.

If a rule conflicts with a task request, **the rule wins unless explicitly overridden in writing**.

---

## Source of Truth Hierarchy

Codex must respect the following priority order:

1. **This CODEX.md**
2. **Explicit plans** in `/thoughts/plans/`
3. **Existing codebase**
4. **Task prompt**
5. **Conversation history**

Conversation context is **not** a reliable source of truth.

---

## Workflow Model (FIC)

All work follows **Frequent Intentional Compaction (FIC)**.

Codex must assume the current task belongs to **one and only one phase**:

* **Research** → investigate, no code
* **Plan** → design, no code
* **Implement** → code, strictly following a plan
* **Validate** → verify against plan

If the phase is unclear, Codex must ask.

---

## Phase Rules

### Research Phase

* Do **not** write code
* Do **not** suggest implementations
* Focus on:

  * Existing architecture
  * Data flow
  * Constraints
* Output must be a **structured document** intended to be saved under:

  ```
  /thoughts/research/
  ```

---

### Plan Phase

* Do **not** write production code
* Produce a **step-by-step plan**
* Plans must include:

  * Objective
  * Phases
  * Files to change
  * Tests to add or update
  * Risks and non-goals
* Plans are saved under:

  ```
  /thoughts/plans/
  ```

---

### Implement Phase

* Implement **only the requested phase**
* Follow the plan **exactly**
* Reuse existing code whenever possible
* Do not introduce new abstractions unless the plan requires it
* Stop after completing the phase
* Prefer correctness and clarity over cleverness

---

### Validate Phase

* Compare implementation strictly against the plan
* Identify:

  * Missing steps
  * Deviations
  * Undocumented changes
* Do not refactor unless explicitly requested

---

## Architectural Principles

* Prefer **existing services, patterns, and abstractions**
* Avoid duplication
* Avoid speculative generalization
* Make changes **minimal and local**
* New code must fit the existing style and structure

If unsure, **reuse instead of creating**.

---

## Testing Rules

* Tests are mandatory when:

  * Adding behavior
  * Changing logic
  * Fixing bugs
* Prefer modifying existing tests over adding new ones
* Tests must reflect **intent**, not implementation details

---

## Context Discipline

* Assume context may be incomplete or degraded
* Never rely on “earlier discussion”
* Always re-read referenced files
* Treat documents as authoritative, not memory

If instructions seem missing, Codex must request clarification instead of guessing.

---

## What Codex Must Not Do

* Do not “improve” unrelated code
* Do not refactor without instruction
* Do not invent requirements
* Do not bypass the plan
* Do not continue beyond the requested scope

---

## Default Behavior

If anything is ambiguous:

1. Ask a clarifying question
2. Do not assume
3. Do not proceed blindly

---

## Reset Compatibility

This CODEX.md is designed to work correctly:

* In fresh sessions
* After hard resets
* With only file-based context

Codex must behave consistently across sessions when given the same documents.

---

## Final Rule

> **Documents define reality.
> Conversation is ephemeral.**

---

### Opcional (muy recomendado)

En cada prompt de Implement o Validate, empieza con:

```text
Re-read and follow CODEX.md strictly.
```


# Templates

A continuación tienes una **plantilla de `/thoughts/plans/*.md`** pensada **específicamente para trabajar con Codex**, alineada con **FIC**, y optimizada para:

Copiar la plantilla a `/thoughts/plans/template.md`

* ejecución por **fases**
* resets frecuentes de contexto
* validación objetiva
* mínima ambigüedad

Es deliberadamente **estructurada y explícita**: Codex rinde mejor así.

```
---

# Plan: `<short-descriptive-title>`

**Status:** Draft | Approved | Implemented
**Date:** YYYY-MM-DD
**Author:** `<name or role>`
**Related research:**

* `@thoughts/research/<research-file>.md`

---

## 1. Objective

Describe **exactly** what this plan achieves.

* What problem is being solved
* What success looks like
* One–two paragraphs max

**Non-goals**

* Explicitly list what is out of scope

---

## 2. Constraints

List **hard constraints** Codex must not violate.

* Architectural constraints
* Backward compatibility
* Performance / security requirements
* External dependencies that must not change

If something must not be touched, write it here.

---

## 3. Current State Summary

Brief description of the current implementation.

* Relevant modules/services
* Key classes or files
* Existing behavior and limitations

This section is critical for context re-hydration.

---

## 4. Proposed Solution (High Level)

Explain the approach **without code**.

* Design decisions
* Data flow changes
* Interaction between components

Use diagrams or bullet flows if helpful.

---

## 5. Implementation Phases

Each phase must be **independently implementable**.

---

### Phase 1 — `<name>`

**Goal**
What this phase delivers.

**Changes**

* File A: what changes
* File B: what changes

**New behavior**

* Bullet list of observable changes

**Tests**

* Tests to add or update

**Exit criteria**

* Conditions that must be true to consider this phase complete

---

### Phase 2 — `<name>`

(Repeat the same structure)

---

## 6. Risks and Mitigations

* Technical risks
* Migration risks
* Edge cases

Explain how each risk is mitigated or why it’s acceptable.

---

## 7. Validation Checklist

This is used in the **Validate phase**.

* [ ] All phases implemented
* [ ] No undocumented changes
* [ ] Tests passing
* [ ] Code follows CODEX.md
* [ ] No scope creep

---

## 8. Open Questions

List unresolved decisions.

If this section is non-empty, **implementation should not start**.

---

## 9. Decision Log (Optional but powerful)

Record **why** key decisions were made.

* Decision
* Alternatives considered
* Rationale

This survives context resets and team changes.

---

## Usage Pattern (important)

### Create plan

```text
Create a plan using /thoughts/plans/template.md or this template by default.
Do not write code.
```

### Implement phase

```text
Implement Phase 1 only.
Follow this plan exactly.
```

### Validate

```text
Validate implementation against this plan.
Do not modify code.
```

---

## Design Principles for Codex (why this works)

* Explicit beats implicit
* Phases reduce context load
* Exit criteria prevent drift
* Checklists enable objective validation

---

### Regla final

> **If it’s not written in the plan, it does not exist.**

