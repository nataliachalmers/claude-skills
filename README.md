# Claude skills

Custom skills for Claude, written for dental and health-policy work. Each folder holds one skill: a `SKILL.md` with YAML frontmatter (`name`, `description`) followed by the instructions Claude follows when the skill runs.

| Skill | One line | Use it when |
|---|---|---|
| [`superb-prompt`](superb-prompt/SKILL.md) | Build or fix a prompt that names its reader and asks for one insight, from the five parts (role, task, context, constraints, format) and five prompt types, checked against the "superb test" before it goes out. | Shaping the ask, before any other step. |
| [`claim-audit`](claim-audit/SKILL.md) | Audit AI-written text claim by claim: ten hallucination patterns, primary-source verification, a verdict, a flagged table and a fix-it prompt to send back to the model. | Before citing, forwarding or presenting anything an AI wrote. |
| [`plain-and-precise`](plain-and-precise/SKILL.md) | Rewrite expert writing for non-experts without letting the claims drift: every change explained, every drift flagged; tuned to four readers (general public, payer and Hill, lay-science, clinician and coalition); editor by default, coach on request. | Making a draft land with its reader. |

Typical order: `superb-prompt` to frame the request, `claim-audit` on anything AI-drafted, `plain-and-precise` for the reader.

## Using a skill

- **Claude Code:** copy a skill's folder into `~/.claude/skills/` (personal) or `.claude/skills/` inside a project, then invoke it with `/skill-name` or just describe the task; the `description` in the frontmatter is what makes it trigger.
- **Claude apps (claude.ai, desktop):** add the skill from the Skills section of Settings, or paste the `SKILL.md` contents when creating a new skill.

## Adapting them

These are written for one person's work: the audiences, examples and vocabulary tables reflect U.S. dental and Medicaid/Medicare policy. To reuse a skill, keep the structure (framing, steps, output format, rules with their reasons) and replace the audience tables and examples with your own.
