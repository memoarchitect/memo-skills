# MEMO Skills

Portable, Markdown-first AI skills for the medical-device development lifecycle.
The collection will cover work from user needs and design inputs through risk,
architecture, implementation, verification, validation, and lifecycle change.
A repository can contain many skills; each immediate child of `skills/` is
self-contained and independently installable.

## Available skills

| Skill | Purpose |
| --- | --- |
| [`medical-device-requirements`](skills/medical-device-requirements/) | Create, review, and refine user needs plus system, software, and hardware requirements using EARS and SOPHIST; accepts SysML v2 and MEMO model context. |

## Using a skill

Each skill is a folder whose entry point is always named `SKILL.md`:

```text
skills/
  medical-device-requirements/
    SKILL.md
    references/
```

Copy the complete skill folder into the target platform's skills directory. The
portable contract is `SKILL.md` plus the files it references; no vendor-specific
metadata or tool dependency is required. If a platform uses another skill
format, provide `SKILL.md` as the governing instruction file and preserve its
relative `references/` directory.

Invoke the installed skill by name where the platform supports skill invocation,
or describe the requested task and attach the skill contents. For example:

```text
Use medical-device-requirements to create system requirements for a home-use
device from these user needs and risk controls.

Use medical-device-requirements to review these software requirements. Return
findings and suggestions only; do not alter the source.

Use medical-device-requirements to refine this requirements baseline. Review it
first, then provide proposed revisions and a change log.

Use medical-device-requirements with this SysML v2 or MEMO model as context to
refine requirement traceability and allocation. Flag missing information rather
than inventing requirements.
```

Read the skill's `SKILL.md` before use. It states the required inputs, operating
modes, output format, and safety limits for that skill.

## Contributing

Add each new skill under `skills/<kebab-case-name>/`. Keep it self-contained,
avoid platform-only dependencies unless explicitly documented, and validate its
frontmatter before publishing.
