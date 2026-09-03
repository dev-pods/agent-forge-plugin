# Agent Forge

Agent Forge is a curated team of specialized GitHub Copilot agents for planning,
implementation, design, and project orchestration. Use the four specialists
together as a lightweight software delivery team, or invoke one directly when
you need a single area of expertise.

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
├── plugin.json                # Plugin name, version, and description
├── mcp.json                   # MCP server registrations for documentation access
├── agents/
│   ├── coder.agent.md         # Coder definition
│   ├── designer.agent.md      # Designer definition
│   ├── orchestrator.agent.md   # Orchestrator definition
│   └── planner.agent.md       # Planner definition
└── com.github.copilot/
	└── agents/                # Packaged copies of the agent definitions
```

The canonical agent definitions live in `agents/`. The matching files under
`com.github.copilot/agents/` are included for the packaged Copilot layout; keep
both locations synchronized when an agent changes.

## Use locally

1. Open this repository in VS Code Insiders with GitHub Copilot enabled.
2. Open the Chat agent picker.
3. Select the agent that best matches the task, or choose **Orchestrator** when a request spans multiple areas.

The agent front matter declares each agent’s description, supported models, and
tools. `mcp.json` registers the documentation services used by the agents,
including GitHub Support Docs Search and Context7.

## Recommended workflow

For a multi-step change, use the agents in this order:

1. **Orchestrator** — coordinate the work when several specialists or phases are involved.
2. **Planner** — research the request and define the implementation steps.
3. **Designer** — shape the user experience when the work includes UI or UX.
4. **Coder** — implement and test the approved changes.

For smaller tasks, invoke **Planner**, **Coder**, or **Designer** directly. The
agents are independent, so you can choose only the expertise the task requires.

## Maintaining the plugin

When adding or changing an agent:

- Update the matching `.agent.md` definition in `agents/`.
- Update the matching packaged copy in `com.github.copilot/agents/`.
- Keep the plugin version in `plugin.json` aligned with published changes.
- Review each agent’s declared tools and supported models before publishing.
- Confirm the MCP registrations in `mcp.json` are still available and required.

## License

This plugin is currently marked `UNLICENSED` in its manifests.
