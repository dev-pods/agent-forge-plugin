# Agent Forge

Agent Forge is a curated team of specialized GitHub Copilot agents for planning,
implementation, design, and project orchestration. The plugin packages four
agents that can be used independently or together as a lightweight software
delivery team.

## Included agents

| Agent | Focus | Use it when you need to… |
| --- | --- | --- |
| **Planner** | Research and implementation planning | Understand a codebase, identify risks, and create an actionable plan. |
| **Coder** | Implementation and debugging | Write or modify code, fix defects, and improve code quality. |
| **Designer** | UI/UX and accessibility | Design user interfaces, interaction flows, and accessible experiences. |
| **Orchestrator** | Delegation and coordination | Break a larger request into specialist tasks and coordinate execution. |

## VSCode Chat Plug-in

You can install this Agent and Skill by VSCode Chat Plug-in

[![Install Chat Plugin VS Code](https://img.shields.io/badge/Install_Chat_Plugin-VS_Code-blue)](vscode://chat-plugin/install?source=dev-pods/agent-forge-plugin)

[![Install Chat Plugin VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-Install_Chat_Plugin-24BFA5)](vscode-insiders://chat-plugin/install?source=dev-pods/agent-forge-plugin)


## Repository layout

```text
.
├── .plugin/
│   └── plugin.json              # Plugin metadata
├── agents/
│   ├── coder.agent.md           # Coder definition
│   ├── designer.agent.md        # Designer definition
│   ├── orchestrator.agent.md    # Orchestrator definition
│   └── planner.agent.md         # Planner definition
├── marketplace/
│   ├── marketplace.json         # Machine-readable agent catalog
│   └── README.md                # Catalog usage and publishing notes
└── README.md
```

## Use locally

1. Open this repository in VS Code Insiders with GitHub Copilot enabled.
2. Open the agent picker in Chat.
3. Select the agent that best matches the task, or select **Orchestrator** when the request spans multiple areas.

The source definitions live in `agents/`. The catalog in
`marketplace/marketplace.json` provides discoverable metadata such as each
agent's stable ID, capabilities, supported models, and required tools.

## Recommended workflow

For a multi-step change, use the agents in this order:

1. **Planner** — research the request and define the implementation steps.
2. **Designer** — shape the user experience when the work includes UI or UX.
3. **Coder** — implement and test the approved changes.
4. **Orchestrator** — coordinate the sequence when several specialists or phases are involved.

For smaller tasks, invoke **Coder** or **Designer** directly. The agents are
independent, so you can choose only the expertise the task requires.

## Maintaining the catalog

When adding or changing an agent:

- Update the matching `.agent.md` definition in `agents/`.
- Update its entry in `marketplace/marketplace.json`.
- Keep the `id` stable once published.
- Keep the plugin and agent versions aligned for catalog or definition changes.
- Confirm every catalog `source` path resolves to an existing agent file.
- Review declared tools and models for accuracy before publishing.

See [`marketplace/README.md`](marketplace/README.md) for the complete catalog
contract and security review checklist.

## License

This plugin is currently marked `UNLICENSED` in its manifests.
