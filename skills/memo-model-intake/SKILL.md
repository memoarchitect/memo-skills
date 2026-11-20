---
name: memo-model-intake
description: Bring existing material into a MEMO model as a reviewed plan. Use when the user wants to model a device from a codebase, design documents, spreadsheets, an existing SysML or C4 model, or notes; when they ask to reconcile such material with a MEMO model; or when they ask what the model is missing compared with a source. Produces a plan of what to add, change, or investigate, settled with the user one structural question at a time, and hands authoring to memo-method-step.
---

# Model intake

Turn source material into a plan for the MEMO model, agree the plan with the user, then hand the
authoring to `memo-method-step`, one method step at a time. This skill plans; it does not write
SysML and it never deletes anything from the model.

## Tools

When the MEMO MCP server is connected (tools named `memo_*`), use it: `memo_project_summary` to
orient, `memo_ontology` for the kinds and relationships the model may use, `memo_search_elements`
and `memo_get_element` to find what already exists, `memo_systems` for the systems, and `memo_guide`
for the method's steps. Without it, read the `.sysml` files and the ontology package the project
imports. Never use a kind or relationship the ontology does not define; if the source needs one,
record it as an open question.

## 1. Locate and inventory

Find the model (the folder with `memo.package.yaml`) and the source material. List what the source
contains, grouped the way the model is: systems and their parts, functions and flows, interfaces,
requirements, hazards and controls, verification. Cite each item with its location
(`file:line`, document section, sheet and row). Do not open the model's generated or cached files.

## 2. Reconcile

For every source item decide one status against the model:

| Status | Meaning |
| --- | --- |
| `new` | Nothing in the model represents it. |
| `update` | An element represents it, and the source says something the model does not. |
| `unchanged` | The model already says it. |
| `investigate` | It cannot be settled without the user: conflicting sources, unclear boundary, unclear layer. |

Match by meaning, not by name: search by name, then by the element's documentation and relationships.
An element the source does not mention is not a candidate for removal; leave it out of the plan.

## 3. Settle structure with the user

Ask only structural questions, one at a time, each with your recommended answer and the evidence for
it (`file:line` or the model element). Structural means: where a system boundary is, which part a
function is allocated to, whether two source items are one element, which layer something belongs
to, whether a source term is the ontology's regulated term. Do not ask about individual attribute
values; mark those `TBD` in the plan. After about fifteen questions, stop and offer to continue
later with the rest marked `investigate`.

## 4. Write the plan

Write `memo-intake-plan.md` at the model root:

```markdown
# Intake plan: <source>
Model: <model name> · Source: <what was read> · Date: <YYYY-MM-DD>

## Decisions
- <question>: <answer> (<evidence>)

## By method step
### <step label> (<stage>)
| Status | Item | Kind | Model element | Evidence | Notes |
| --- | --- | --- | --- | --- | --- |

## To investigate
- <item>: <why>
```

Group rows by the method step that produces the element's kind (`memo_guide` lists each step's
kinds), in the method's order. Show the plan to the user and change it until they accept it.

## 5. Hand off

For each method step with `new` or `update` rows, in the method's order, use `memo-method-step` on
that step with the plan as its input. Report `investigate` items as open, never as done.
