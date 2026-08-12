---
name: medical-device-requirements
description: Draft, refine, review, or trace medical-device user needs and system, software, and hardware requirements. Use for device requirements specifications, design inputs, acceptance criteria, requirements reviews, and traceability work that should apply EARS syntax and SOPHIST quality rules while accounting for intended use, users, use environments, risk controls, verification, and validation.
---

# Medical Device Requirements

Create clear, testable requirements. Treat this skill as a writing and review aid, not a regulatory-compliance determination. Ask for the applicable markets, device classification, quality-system procedures, risk-management file, and controlled terminology when they affect the requested output.

## Start with the requirement context

Before drafting, obtain or state assumptions for:

- Intended use, indication, patient population, intended users, and use environment.
- Product boundary and the requirement level: user need, system, software, or hardware.
- Source, stakeholder, hazard or risk-control link, and any governing standards or company procedures.
- Units, tolerances, operating conditions, interfaces, data, and the verification method or success criterion.

Do not invent clinical claims, safety limits, risk acceptability, standards compliance, or regulatory classifications. Mark missing information as `TBD` and formulate a focused question.

## Preserve the requirement hierarchy

Keep each level distinct and link the levels in both directions.

| Level | State | Avoid |
| --- | --- | --- |
| User need | Desired outcome for a defined user in a defined use context. | Implementation, architecture, or unexplained technical limits. |
| System requirement | Device behavior or performance that fulfills a user need or risk control. | Unallocated software or hardware detail. |
| Software requirement | Behavior, data handling, interfaces, timing, failure handling, or constraints allocated to software. | Vague system behavior or hardware assumptions. |
| Hardware requirement | Physical, electrical, mechanical, environmental, or interface behavior allocated to hardware. | Software logic disguised as an electrical requirement. |

A user need is normally validated with representative intended users and intended use. A lower-level requirement is normally verified against its stated acceptance criterion. Do not call a verification activity validation, or vice versa.

## Draft requirements

Use `shall` for mandatory requirements. Give every requirement one subject, one observable obligation, and one verification-ready result. Prefer active voice, controlled terminology, measurable values, and explicit conditions. Split compound statements unless all clauses are inseparable for one verification.

Write the main sentence in EARS form. Choose the smallest fitting pattern from [EARS and SOPHIST patterns](references/ears-sophist-patterns.md), then apply the SOPHIST quality checks in that reference. Use a unique identifier and include the accompanying record fields below.

```markdown
ID: SYS-###
Title: Short, unique intent
Requirement: When <trigger>, the <system> shall <observable response> <measurable constraint>.
Rationale: Why this requirement exists.
Source: <stakeholder / hazard / standard / change request>
Parent links: <user need / system requirement IDs>
Risk links: <hazard, hazardous situation, risk-control IDs; if applicable>
Verification: <inspection | analysis | test | demonstration>, with pass criterion.
Status: Draft
Open items: <TBDs or none>
```

For a user need, replace `Verification` with `Validation approach` and describe the representative user, use scenario, and observable success outcome. Do not force a user need into a technical EARS sentence if it loses the user outcome; use a concise outcome statement followed by measurable validation criteria.

## Address safety and use conditions explicitly

For each safety-related or risk-control-derived requirement, name the relevant operating state, trigger or foreseeable misuse where applicable, required response, safe state or user-facing information, and verification evidence. Do not assert that a requirement reduces risk sufficiently; connect it to the approved risk-management analysis and its acceptance rationale.

For user-facing behavior, capture intended users, use environment, critical tasks, alarms or messages, and response time where relevant. Do not assume that a display, alert, or control is usable merely because it exists.

Read [Medical-device guardrails](references/medical-device-guardrails.md) when the request concerns regulatory framing, risk controls, usability, cybersecurity, or a requirements baseline.

## Review and improve an existing set

Review in this order:

1. Classify each item by level and allocation; flag hierarchy leakage.
2. Map the sentence to an EARS pattern; rewrite only when the meaning is preserved.
3. Apply SOPHIST checks: atomic, necessary, unambiguous, feasible, consistent, complete, traceable, and verifiable.
4. Check parameters, units, tolerances, timing anchors, error behavior, interfaces, and defined terms.
5. Check parent/child traceability, risk-control linkage, and an objective verification or validation approach.
6. Return a review table with ID, finding, severity, proposed wording, reason, and unresolved assumption.

Never silently change the intended meaning of an approved requirement. Present meaning-changing edits as alternatives and identify the decision needed.

## Deliverables

Unless the user specifies another format, return:

1. Assumptions and open questions.
2. A requirements table with ID, level, EARS requirement, rationale, source, links, and verification or validation.
3. A traceability summary showing user need → system → software/hardware allocation → verification or validation evidence.
4. A concise review of gaps, conflicts, and compliance-sensitive items requiring quality or regulatory approval.

## Portability

This is intentionally a plain `SKILL.md` skill with relative Markdown references and no tool dependency. Copy the `medical-device-requirements/` folder into the target assistant's skills directory, or provide `SKILL.md` as the governing instruction file where the target platform uses another skill format.
