# Agent Skills by Paddy

*Thanks to my employer, [Medfin AI](https://medfin.ai/), for permitting me to share certain of these agent skills.*

---

My personal skills for agentic coding, in the [Agent Skills](https://agentskills.io/) format. Every skill is defined by a folder holding a `SKILL.md` file: instructions the agent loads when a task calls for them.

## Notes

These skills are designed to work the tools I use at work:

- **[Conductor](https://conductor.build/)** for agentic coding. It runs several coding agents in parallel, each in its own git worktree.
- **[Linear](https://linear.app/)** for projects and issues.
- **[Graphite](https://graphite.dev/)** for version control: stacked pull requests.

Each skill below lists what it needs.

I tend to use [Claude Code](https://code.claude.com/). Some skill details are specific to it (such as the `/shipshape` command and some frontmatter fields). They should still work with other agents that support the format.

## Skills

### [shipshape](skills/shipshape/SKILL.md)

Tidies up after a Graphite stack enters the merge queue. It confirms each PR landed on `main` and deletes the shipped local branches. Then it comments on each Linear ticket, sets its status and proposes follow-up tickets. If a PR fails to land, it reports why and leaves Linear alone.

**Needs:** Graphite CLI (`gt`), GitHub CLI (`gh`), a Linear connection. You run it yourself with `/shipshape`; the agent won't start it unprompted. Before first use, replace the `[your ...]` placeholders with your own Linear statuses and projects.

### [write-better](skills/write-better/SKILL.md)

Makes prose shorter and clearer. Intended for tickets, RFCs, docs, ADRs and PR descriptions (and this README ;) ). It leads with a summary, applies Orwell's rules for writing and bans common AI-isms (reflexive lists of three, em-dashes everywhere). It writes British English.

**Needs:** nothing.

*Acknowledgements: partly derived from George Orwell's well-known writing rules and Wayne Sutton's [write](https://github.com/waynesutton/waynesutton-ai/blob/main/.claude/skills/write/SKILL.md) skill.*

## Installation

Copy a folder from `skills/` into your agent's skills directory (`.agents/skills/` or `.claude/skills/`). Rewrite the skills for your use case (some placeholder text is included).

## Licence

[MIT](LICENSE)
