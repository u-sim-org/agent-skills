# u-sim agent skills

Create and review fictional u-sim Suite scenarios with an agent that supports the Agent Skills format.

## Install

Run in your project directory with Node.js and npm installed. Choose your agent and one or both skills:

```sh
npx skills add u-sim-org/agent-skills
```

Or paste this into your agent:

> Install the u-sim scenario authoring and scenario review skills from https://github.com/u-sim-org/agent-skills for this agent. Use this project's skill scope. If you have a terminal, run npx skills add u-sim-org/agent-skills and select this agent and both skills. Otherwise, read the repository's installation instructions and tell me the supported next step.

The [skills CLI](https://skills.sh/docs/cli) supports agents including Claude Code, Codex, Cursor, and GitHub Copilot. Installation depends on your agent's capabilities; a chat-only interface may require a manual upload.

## Included skills

- [Scenario authoring](skills/usim-scenario-authoring/SKILL.md): Turn a teaching brief into a fictional Suite scenario, or revise an existing case while preserving its authored behavior.
- [Scenario review](skills/usim-scenario-review/SKILL.md): Check an existing scenario’s structure, decision paths, timing, resources, and assessment. Get findings tied to specific fields and actions.

Each skill includes a Suite profile manifest, JSON Schema, field inventory, fictional example, and behavior/validation guidance. Keep the full skill folder together when installing manually. Match the bundled profile to your target Suite version.

These skills provide instructions and reference data. They do not provide an MCP server, connect to an account, or authorize publication. Raw scenario JSON is not a published Suite import package. Technical validation does not establish clinical correctness.

## Updates

Run `npx skills update` to check installed skills for updates. Review changes and the profile manifest before using a new version with existing scenarios.
