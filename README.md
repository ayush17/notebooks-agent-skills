# Notebooks Agent Skills

Agent Skills for OpenDataHub/RHOAI Notebooks - CVE resolution, dependency management, and development workflows.

## Installation

### Claude Code CLI

```bash
# Add this marketplace
/plugin marketplace add ayush17/notebooks-agent-skills

# Install the CVE resolution plugin
/plugin install cve-resolution@notebooks-agent-skills
```

### Manual Installation

```bash
# Clone and use directly
git clone https://github.com/ayush17/notebooks-agent-skills.git
cd your-project
claude --plugin-dir /path/to/notebooks-agent-skills
```

## Available Plugins

### CVE Resolution (`cve-resolution`)

Complete CVE resolution workflow for OpenDataHub/RHOAI Notebooks:
- Autonomous Jira ticket triage and assignment
- CVE research and fix identification
- Dependency constraint updates
- PR creation to downstream branches
- Jira comments and status updates
- Team Slack notifications

#### Usage

```bash
# In Claude Code CLI
/fix-cve              # Full workflow - assign AND fix CVEs
/fix-cve status       # Check status of assigned CVEs
/fix-cve RHAIENG-1234 # Fix a specific ticket
```

#### Requirements

- **MCP**: Atlassian (Jira) - for ticket management
- **Tools**: `git`, `gh` (GitHub CLI), `make`
- **Access**: Write access to `red-hat-data-services/notebooks` repository

## Plugin Structure

```
notebooks-agent-skills/
├── .claude-plugin/
│   ├── plugin.json       # Plugin manifest
│   └── marketplace.json  # Marketplace catalog
├── skills/
│   └── cve-resolution/
│       └── SKILL.md      # CVE resolution skill definition
├── commands/
│   └── fix-cve.md        # /fix-cve command definition
├── LICENSE
└── README.md
```

## Contributing

1. Fork this repository
2. Create a feature branch
3. Make your changes
4. Run `claude plugin validate .` to verify
5. Submit a pull request

## Publishing to Claude Community Marketplace

This plugin can be submitted to Claude's official community marketplace:

1. Validate: `claude plugin validate .`
2. Submit at: https://platform.claude.com/plugins/submit
3. After approval, users can install via:
   ```
   /plugin marketplace add anthropics/claude-plugins-community
   /plugin install cve-resolution@claude-community
   ```

## License

MIT License - see [LICENSE](LICENSE)
