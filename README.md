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

Copy the complete skill folder into the target platform's skills directory. The
portable contract is `SKILL.md` plus the files it references; no vendor-specific
metadata or tool dependency is required. If a platform uses another skill
format, provide `SKILL.md` as the governing instruction file and preserve its
relative `references/` directory.

For Codex, install a copy or symlink at `~/.codex/skills/memo-requirements/`,
then start a new task or refresh the skill list. Adding this repository as a
project submodule keeps the source available; it does not itself install the
skill into Codex.

In Codex desktop, type `/` in the prompt, search for and select
`memo-requirements`, then write the request. If it is not listed, confirm that
the complete folder is installed at the location above and start a new task.

EARS and SOPHIST are built into `memo-requirements`; do not repeat them in each
request. The skill writes technical requirements in EARS form and uses SOPHIST
to check their quality before returning them.

Use the same task examples on every platform. After selecting the skill with
`/`, write only the task and its inputs:

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
Refine requirement traceability and allocation using this SysML v2 or MEMO
model as context. Flag missing information rather than inventing requirements.

[attach or paste model]
```

On platforms without a slash menu, invoke the installed skill by name where
supported and use the same prompt with the prefix `Use memo-requirements to`.
For example: `Use memo-requirements to create system requirements from these
user needs for a home-use infusion pump: ...`. If named invocation is not
available, attach the complete skill folder and use the same task prompt.

Read the skill's `SKILL.md` before use. It states the required inputs, operating
modes, output format, and safety limits for that skill.

## Contributing

Add each new skill under `skills/<kebab-case-name>/`. Keep it self-contained,
avoid platform-only dependencies unless explicitly documented, and validate its
frontmatter before publishing.
