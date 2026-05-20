# Security Policy

This skill is instruction-only by default.

It should not:

- execute shell commands automatically
- download external files automatically
- modify files outside the active mod repository
- copy proprietary HOI4 or DLC assets into this repository
- ask agents to ignore user, system, or platform safety instructions
- accept contributions that add instructions to bypass user, system, platform, repository, or safety constraints
- hide instructions in metadata or adapter files
- require binaries or dependency installation for the MVP

## Reporting Issues

Report suspicious behavior, unsafe instructions, or supply-chain concerns through GitHub issues.

When reporting, include:

- the affected file
- the instruction or behavior that looks unsafe
- why it could cause unexpected agent behavior

## Maintainer Expectations

Keep this repository auditable. Prefer plain Markdown, concise instructions, and no hidden execution paths. Any future scripts must be optional, documented, and reviewed as executable code rather than passive documentation. Future validation scripts must be optional and must not run automatically from `SKILL.md`.
