---
name: memo-flow-walkthrough
description: Build or review a flow in a MEMO model one section at a time with the user, such as a clinical workflow, an operational scenario, or a functional chain of a device. Use when the user wants to document how a procedure or a device behaviour unfolds step by step, to turn a narrative or a procedure document into a flow, or to check a flow against the model's functions, actors and parts.
---

# Flow walkthrough

Walk a flow with the user section by section, so each part is confirmed before the next is built.
The user leads; this skill structures, checks against the model, and records.

## Tools

With the MEMO MCP server connected, use `memo_ontology` for the flow and step kinds the model
offers at each level (clinical, operational, functional), `memo_search_elements` and
`memo_get_element` to point steps at existing actors, functions and parts, `memo_trace` and
`memo_allocation` to see what a function is allocated to, and `memo_validate` to check. Without the
server, read the `.sysml` source and the ontology the project imports.

## 1. Fix the flow

Agree with the user: the flow's name and level (a clinical workflow, an operational use case, a
functional chain), its system, its trigger, and its end. Find any existing flow of the same purpose
first; extend it rather than start another. At the operational level a workflow has no entry or exit
condition: say so if the user asks for one.

## 2. Split it into sections

Propose sections (for example: preparation, start, steady operation, alarms, stop) and confirm them
before any detail. Each section ends at a point the user can recognise in practice.

## 3. Walk each section

For each section, in order:

1. Ask the user to describe it, or read it from the source they gave.
2. Turn it into steps. A step is exactly one thing: one action of one performer, or one function.
   Point each step at an existing element when one fits; name a new one only when none does, and mark
   it new.
3. Show the section as a numbered list of steps with performers, and the branches (alternatives,
   repetition, alarms) as their own steps with the condition stated.
4. Ask for confirmation, change it, and only then go on.

Do not invent clinical steps, timings or limits. Mark unknowns `TBD`.

## 4. Check the whole flow

Check that every step's performer exists, every function is allocated, step names are unique, every
branch leads somewhere, and the flow ends where agreed. Report gaps against the model: a step whose
function nothing performs, an actor no interface reaches.

## 5. Record it

With the `propose_*` tools available, propose the new elements and relationships; they wait for the
engineer in MEMO Architect. Otherwise write the flow into the `.sysml` source in the file that holds
the model's flows of that level. Then run `memo_validate` on what changed and report the flow, the
new elements, and the open `TBD`s.
