# Agent Forge

Agent Forge is a curated team of specialized GitHub Copilot agents for planning,
implementation, design, and project orchestration. This plugin packages four
independent specialists that can be used together as a lightweight software
delivery team or invoked individually when a single skill is required.

## Included agents

| Agent | Focus | Use it when you need to… |
| --- | --- | --- |
| **Planner** | Research and implementation planning | Understand a codebase, identify risks, and create an actionable plan. |
| **Coder** | Implementation and debugging | Write or modify code, fix defects, and improve code quality. |
| **Designer** | UI/UX and accessibility | Design user interfaces, interaction flows, and accessible experiences. |
| **Orchestrator** | Delegation and coordination | Break a larger request into specialist tasks and coordinate execution. |

## VS Code Chat Plugin

Install this plugin from the VS Code Chat Plugin entry point:

[![Install Chat Plugin VS Code](https://img.shields.io/badge/Install_Chat_Plugin-VS_Code-blue)](vscode://chat-plugin/install?source=dev-pods/agent-forge-plugin)

[![Install Chat Plugin VS Code Insiders](https://img.shields.io/badge/Install_Chat_Plugin-VS_Code_Insiders-24BFA5)](vscode-insiders://chat-plugin/install?source=dev-pods/agent-forge-plugin)

## Repository layout

```text
.
├── README.md                  # Project overview and usage guidance
├── plugin.json                # Plugin manifest and agent metadata
├── mcp.json                   # MCP server registrations for documentation access
├── agents/
│   ├── coder.agent.md         # Coder definition
│   ├── designer.agent.md      # Designer definition
│   ├── orchestrator.agent.md   # Orchestrator definition
│   └── planner.agent.md       # Planner definition
└── .git/                      # Repository metadata
```

## Use locally

1. Open this repository in VS Code Insiders with GitHub Copilot enabled.
2. Open the Chat agent picker.
3. Select the agent that best matches the task, or choose **Orchestrator** when a request spans multiple areas.

The source definitions live in `agents/`, while the plugin metadata in
`plugin.json` defines the agent catalog, capabilities, supported models, and
required tools.

## Recommended workflow

For a multi-step change, use the agents in this order:

1. **Planner** — research the request and define the implementation steps.
2. **Designer** — shape the user experience when the work includes UI or UX.
3. **Coder** — implement and test the approved changes.
4. **Orchestrator** — coordinate the sequence when several specialists or phases are involved.

For smaller tasks, invoke **Coder** or **Designer** directly. The agents are
independent, so you can choose only the expertise the task requires.

## Maintaining the plugin

When adding or changing an agent:

- Update the matching `.agent.md` definition in `agents/`.
- Update the matching entry in `plugin.json` so metadata stays accurate.
- Keep each `id` stable once it has been published.
- Keep the plugin and agent versions aligned when metadata or behavior changes.
- Confirm every `source` path resolves to an existing agent file.
- Review declared tools and models before publishing.

## License

This plugin is currently marked `UNLICENSED` in its manifests.
