---
name: memo-requirements
description: Create, review, refine, or trace medical-device user needs and system, software, and hardware requirements. Use for device requirements specifications, design inputs, acceptance criteria, requirements reviews, and traceability work that should apply EARS syntax and SOPHIST quality rules while accounting for intended use, users, use environments, risk controls, verification, and validation. Accept SysML v2 or MEMO models as input context for further refinement.
---

# Medical Device Requirements

Create clear, testable requirements. Apply EARS as the requirement-sentence syntax and SOPHIST as the quality method by default; do not require the user to request either method. Treat this skill as a writing and review aid, not a regulatory-compliance determination. Ask for the applicable markets, device classification, quality-system procedures, risk-management file, and controlled terminology when they affect the requested output.

Use EARS to state each technical requirement in a clear conditional or unconditional `shall` sentence. Use SOPHIST to test that wording for necessity, atomicity, lack of ambiguity, completeness, consistency, feasibility, traceability, and verifiability. A user need may remain a concise outcome statement when forcing it into a technical EARS sentence would lose the user intent; apply SOPHIST quality checks and define its validation criteria.

## Select the operating mode

Infer the mode from the request, or ask only if the distinction changes the requested artifact:

| Mode | Purpose | Output and change rule |
| --- | --- | --- |
| `create` | Draft new requirements from supplied needs, risks, interfaces, use cases, or model context. | Produce a clearly labelled draft; do not imply approval. |
| `review` | Assess supplied requirements or a baseline. | Produce findings and suggested wording only. Do not rewrite or modify the source artifact. |
| `refine` | Improve supplied requirements after review. | First record the review findings, then provide a revised draft and a requirement-by-requirement change log. Preserve identifiers unless a change is explicitly approved. |

For approved or baselined content, `refine` produces a proposed revision, never a silent replacement. Identify every meaning-changing edit and the approval decision it needs.

## Start with the requirement context

Before drafting, obtain or state assumptions for:

- Intended use, indication, patient population, intended users, and use environment.
- Product boundary and the requirement level: user need, system, software, or hardware.
- Source, stakeholder, hazard or risk-control link, and any governing standards or company procedures.
- Units, tolerances, operating conditions, interfaces, data, and the verification method or success criterion.

### Use SysML v2 or MEMO model input

When the user references a SysML v2 or MEMO model that is available in the working context, inspect it and use it as evidence for terminology, element identity, hierarchy, allocation, interfaces, states, constraints, existing requirement relations, and traceability. Cite the relevant model element or qualified name in the source or trace link. Ask the user to attach, paste, or otherwise make the model accessible only when it cannot be reached from the supplied reference.

Do not infer intended use, clinical claims, hazards, risk controls, acceptance limits, or regulatory obligations merely from model structure. Flag model/text conflicts, missing allocations, broken trace links, and undefined terms. In `create` mode, produce requirements proposed from the model plus the stated external inputs; in `review` mode, report findings only; in `refine` mode, provide the proposed requirement and model-link updates as a change set.

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

Write the main sentence in EARS form. Choose the smallest fitting pattern from [EARS and SOPHIST patterns](references/ears-sophist-patterns.md), then apply its SOPHIST quality checks before presenting the result. Use a unique identifier and include the accompanying record fields below.

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

## Review and refine an existing set

Review in this order:

1. Classify each item by level and allocation; flag hierarchy leakage.
2. Map the sentence to an EARS pattern; rewrite only when the meaning is preserved.
3. Apply SOPHIST checks: atomic, necessary, unambiguous, feasible, consistent, complete, traceable, and verifiable.
4. Check parameters, units, tolerances, timing anchors, error behavior, interfaces, and defined terms.
5. Check parent/child traceability, risk-control linkage, and an objective verification or validation approach.
6. Return a review table with ID, finding, severity, proposed wording, reason, model link when applicable, and unresolved assumption.

In `review` mode, stop at the findings table. In `refine` mode, follow it with a revised requirements table and a change log containing the ID, old wording, proposed wording, change type, rationale, traceability impact, and required approval. Never silently change the intended meaning of an approved requirement.

## Deliverables

Unless the user specifies another format, return the parts applicable to the selected mode:

1. Assumptions and open questions.
2. For `create` or `refine`, a requirements table with ID, level, EARS requirement, rationale, source, links, and verification or validation.
3. For `review` or `refine`, a findings table; for `refine`, include the change log.
4. A traceability summary showing user need → system → software/hardware allocation → verification or validation evidence, including model links when supplied.
5. A concise review of gaps, conflicts, and compliance-sensitive items requiring quality or regulatory approval.

## Portability

This is intentionally a plain `SKILL.md` skill with relative Markdown references and no tool dependency. Copy the `memo-requirements/` folder into the target assistant's skills directory, or provide `SKILL.md` as the governing instruction file where the target platform uses another skill format.
