# MEMO Skills

Portable, Markdown-first AI skills for the medical-device development lifecycle.
The collection will cover work from user needs and design inputs through risk,
architecture, implementation, verification, validation, and lifecycle change.
A repository can contain many skills; each immediate child of `skills/` is
self-contained and independently installable.

## Available skills

| Skill | Purpose |
| --- | --- |
| [`memo-requirements`](skills/memo-requirements/) | Create, review, and refine user needs plus system, software, and hardware requirements using EARS and SOPHIST; accepts SysML v2 and MEMO model context. |

## Using a skill

Each skill is a folder whose entry point is always named `SKILL.md`:

```text
skills/
  memo-requirements/
    SKILL.md
    references/
```

Add the complete skill folder through your assistant's skill, extension, or
instruction mechanism. The portable contract is `SKILL.md` plus the files it
references; no vendor-specific metadata or tool dependency is required. If an
assistant uses another skill format, use `SKILL.md` as the governing instruction
file and preserve its relative `references/` directory.

Adding this repository as a project submodule only makes the source available;
it does not automatically enable the skill in an assistant. Follow that
assistant's installation or import process, then begin a new conversation if it
does not refresh its skill list automatically.

EARS and SOPHIST are built into `memo-requirements`; do not repeat them in each
request. The skill writes technical requirements in EARS form and uses SOPHIST
to check their quality before returning them.

Use the same task examples with every assistant. If the assistant offers a
skill picker, type `/` (or use its equivalent), select `memo-requirements`, and
write only the task and its inputs:

```text
Create system requirements from these user needs for a home-use infusion pump:

- A patient must be able to start a prescribed infusion safely.
- A patient must be warned if an infusion is interrupted.
- The device must prevent delivery above the prescribed dose.
```

To review a baseline:

```text
Review these software requirements. Return findings and suggested wording only;
do not alter the source.

[paste requirements]
```

To refine a baseline:

```text
Refine this requirements baseline. Review it first, then provide proposed
revisions and a change log.

[paste requirements]
```

To use a SysML v2 or MEMO model as context:

```text
Refine requirement traceability and allocation using the SysML v2 model at
<model name or path> as context. Flag missing information rather than inventing
requirements.
```

Reference an available SysML v2 model by its name, path, or other
platform-specific identifier. A MEMO model is SysML v2 model context. Attach or
paste the model only when the assistant cannot otherwise access it.

In an assistant without a skill picker, invoke the installed skill by name where
supported and use the same prompt with the prefix `Use memo-requirements to`.
For example: `Use memo-requirements to create system requirements from these
user needs for a home-use infusion pump: ...`. If named invocation is not
available, attach the complete skill folder or provide its contents before using
the same task prompt.

Read the skill's `SKILL.md` before use. It states the required inputs, operating
modes, output format, and safety limits for that skill.

## Contributing

Add each new skill under `skills/<kebab-case-name>/`. Keep it self-contained,
avoid platform-only dependencies unless explicitly documented, and validate its
frontmatter before publishing.
