# User-level skills

Drop personal skills here. Each skill gets its own subdirectory containing a `SKILL.md`:

```
skills/
├── your-skill/
│   └── SKILL.md
└── another-skill/
    └── SKILL.md
```

## SKILL.md shape

```markdown
---
name: your-skill
description: When Claude should invoke this skill. Be specific — this is what Claude reads to decide.
user-invocable: true
---

# Body

Plain-prose instructions Claude will follow when this skill is active. Include
examples, gotchas, and any commands to run.
```

## Scope

Skills here apply to every project on your machine. For project-specific skills, put them in `.claude/skills/` inside the repo instead.

## Invocation

- Manual: type `/your-skill` in a Claude session.
- Automatic: when the description matches the task, Claude loads the skill on its own.
- Set `disable-model-invocation: true` in the frontmatter to restrict a skill to manual invocation — useful for destructive workflows.

## References

- [Skills](https://code.claude.com/docs/en/skills)
