# Notebooks Agent Skills Marketplace

[![Agent Skills compatible](https://img.shields.io/badge/spec-agentskills.io-7dd3fc)](https://agentskills.io/specification)
[![Claude Code marketplace](https://img.shields.io/badge/Claude_Code-marketplace-a78bfa)](https://docs.claude.com/en/docs/claude-code/plugin-marketplaces)

Agent Skills for **OpenDataHub/RHOAI Notebooks** — CVE resolution, dependency management, and development workflows.

## Quick Start

### Claude Code CLI

```bash
# Add this marketplace
/plugin marketplace add opendatahub-io/notebooks-agent-skills

# Install CVE resolution plugin
/plugin install cve-resolution@notebooks-agent-skills

# Use the skill
/fix-cve
```

### Cursor IDE

```bash
# Install via plugin manager
/plugin marketplace add opendatahub-io/notebooks-agent-skills
/plugin install cve-resolution@notebooks-agent-skills
```

### Manual Installation (Any Agent)

Copy the skill files to your agent's skills directory:

```bash
# Clone and copy to personal skills folder
git clone https://github.com/opendatahub-io/notebooks-agent-skills
cp -r notebooks-agent-skills/plugins/cve-resolution/skills/cve-resolution ~/.claude/skills/
```

## Available Plugins

### CVE Resolution (`cve-resolution`)

Complete CVE resolution workflow for RHAIENG tickets:

- **Autonomous execution** — No confirmation prompts
- **Multi-branch support** — Works on any rhoai-X.Y branch
- **Jira integration** — Search, assign, comment via MCP
- **PR automation** — Creates PRs with proper formatting
- **Slack summaries** — Generates team update messages

**Commands:**
| Command | Description |
|---------|-------------|
| `/fix-cve` | Full workflow - assign and fix CVEs |
| `/fix-cve plan` | Sprint planning - same as above |
| `/fix-cve <TICKET>` | Fix specific RHAIENG ticket |
| `/fix-cve status` | Show assigned CVE status |

**Prerequisites:**
- Atlassian MCP configured for Jira access
- GitHub CLI (`gh`) authenticated
- Write access to notebooks repository

## Supported Platforms

These skills follow the open [Agent Skills specification](https://agentskills.io) and work with:

- **Claude Code** (Anthropic)
- **Cursor IDE**
- **GitHub Copilot**
- **Gemini CLI**
- **OpenCode, Goose, Amp, Roo Code** and [30+ more](https://agentskills.io/clients)

## MCP Requirements

The CVE resolution skill requires the **Atlassian MCP** for Jira integration.

### Official Atlassian MCP (Recommended)

Uses OAuth authentication — no API token needed:

1. Go to [Cursor Settings] > [MCP] > [Add Server]
2. Add: `https://mcp.atlassian.com/v1/mcp`
3. Authenticate via browser when prompted

### Alternative: NPM Package

```json
{
  "mcpServers": {
    "atlassian": {
      "command": "npx",
      "args": ["-y", "mcp-atlassian"],
      "env": {
        "ATLASSIAN_SITE_URL": "https://redhat.atlassian.net",
        "ATLASSIAN_EMAIL": "your-email@redhat.com",
        "ATLASSIAN_API_TOKEN": "your-api-token"
      }
    }
  }
}
```

## Contributing

### Adding a New Skill

1. Create a new plugin directory:
   ```
   plugins/your-skill/
   ├── .claude-plugin/
   │   └── plugin.json
   ├── skills/
   │   └── your-skill/
   │       └── SKILL.md
   └── commands/
       └── your-command.md
   ```

2. Add to `.claude-plugin/marketplace.json`

3. Submit a PR

### Skill Specification

Skills must follow the [Agent Skills specification](https://agentskills.io/specification):

- `SKILL.md` with YAML frontmatter (`name`, `description`)
- Optional `commands/`, `scripts/`, `references/` directories
- Use Markdown for instructions

## Repository Structure

```
.
├── .claude-plugin/
│   └── marketplace.json       # Plugin catalog
├── plugins/
│   └── cve-resolution/
│       ├── .claude-plugin/
│       │   └── plugin.json    # Plugin manifest
│       ├── skills/
│       │   └── cve-resolution/
│       │       └── SKILL.md   # Skill definition
│       └── commands/
│           └── fix-cve.md     # Command definition
└── README.md
```

## Related Projects

- [opendatahub-io/notebooks](https://github.com/opendatahub-io/notebooks) — Main notebooks repository
- [red-hat-data-services/notebooks](https://github.com/red-hat-data-services/notebooks) — Downstream RHOAI repository
- [agentskills.io](https://agentskills.io) — Agent Skills specification

## License

MIT License — see [LICENSE](LICENSE)
