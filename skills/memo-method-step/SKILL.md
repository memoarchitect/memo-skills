---
name: memo-method-step
description: Work one step of a MEMO model's method, such as declaring the systems, describing operational use, decomposing functions, allocating them, identifying hazards or deciding controls. Use when the user asks to work on a layer or a method step, to complete what the method says is open, or to carry out an intake plan's rows for a step. Reads the step from the model's own method, makes or proposes the changes, and checks the result against the model's rules.
---

# Work one method step

A MEMO model's method lists its steps per stage (context, operational, functional, logical, risk,
verification and so on), and for each step its objective, entry and exit criteria, the element kinds
it uses and produces, and the rules that say it is done and linked to other layers. Work from that,
never from a generic idea of the layer.

## Tools

With the MEMO MCP server connected, the server also offers a prompt for each step; this skill does
the same work when the prompt is not used. Use `memo_guide` (with `stage`) for the step,
`memo_ontology` for kinds and relationships, `memo_search_elements`, `memo_get_element`, `memo_trace`,
`memo_allocation` and `memo_interfaces` for what exists, and `memo_validate` to check. Without the
server, read the methodology package's `MethodologyWorkflowStep` declarations and the `.sysml` source,
and run `memo validate` if it is available.

## 1. Read the step

Name the step and, when the model has several systems, the system (`memo_select_system`). From the
guide, state the objective, entry and exit criteria, the kinds the step produces, the rules that mark
it done, the links it needs to other layers, and where it stands: open, waiting or done, with the
reasons. If the entry criteria are not met, say which earlier step to work first and stop.

## 2. Find what exists

Search before adding. For every element the step needs, look for an existing one by name, by
documentation and through the relationships of its neighbours. Reuse an element rather than create a
near duplicate. An element of the step's kind that belongs to another system is not this step's work.

## 3. Make the changes

Only kinds and relationships the ontology lists, in the direction it gives. Use the ontology's
terms exactly; terms from a standard (ISO 14971, IEC 62304) carry regulatory meaning.

- When the `propose_*` tools are available, propose each change with them. A proposal waits for the
  engineer to apply it in MEMO Architect (AI Tools › Pending changes). Say what you proposed; never
  say the model changed.
- Otherwise edit the `.sysml` source: put a new element in the file that holds elements of its kind,
  and relate it from the element that owns the relationship.

Keep each change small enough to review. Do not move an element between layers or systems as a side
effect.

## 4. Check

Run `memo_validate` (narrowed with `element` for what you touched) and `memo_guide` again. Resolve the
errors your change introduced; findings that predate it are not yours unless asked. A rule with no
subject has not run: it is not evidence the step is done.

## 5. Report

State what the step now has, which done-rules and link-rules hold, what is still open with its
reason, what waits on another layer or team, and every proposal or edit made, with the element ids.
Name the next step the method puts after this one.
