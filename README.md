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

## Installation

Copy a skill folder into the target platform's skills directory. The portable
contract is `SKILL.md` plus any files it references; no vendor-specific metadata
or tool dependency is required. For a platform that uses another skill format,
use `SKILL.md` as the governing instruction file and preserve its relative
`references/` directory.

## Contributing

Add each new skill under `skills/<kebab-case-name>/`. Keep it self-contained,
avoid platform-only dependencies unless explicitly documented, and validate its
frontmatter before publishing.
