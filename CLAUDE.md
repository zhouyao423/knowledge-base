# Claudesidian Repository Management

**⚠️ IMPORTANT: This CLAUDE.md is for maintaining the claudesidian repository itself.**

**If you're a user setting up your own Obsidian vault:**
- Run `claude run init-bootstrap` to create your personalized CLAUDE.md
- That command will overwrite this file with your custom configuration
- This file is only for contributors working on the claudesidian project

---

## Repository Overview

Claudesidian is a starter kit that combines Claude Code with Obsidian for AI-powered knowledge management. This document contains guidelines for maintaining and developing the repository.

## Version Management

This project uses:
- **Semantic Versioning** (MAJOR.MINOR.PATCH)
- **Keep a Changelog** format in CHANGELOG.md
- **Conventional Commits** for commit messages
- **GitHub Releases** for distribution

### Commit Message Format
```
feat: add new feature
fix: resolve bug
docs: update documentation
chore: maintenance tasks
```

### Release Process
1. Update version in `package.json`
2. Move "Unreleased" items to new version in `CHANGELOG.md`
3. Commit: `git commit -m "chore: release v0.2.0"`
4. Tag: `git tag v0.2.0`
5. Push: `git push && git push --tags`
6. GitHub automatically creates release from tag

## Project Structure

```
claudesidian/
├── .claude/
│   ├── agents/          # Claude Code agents
│   ├── commands/        # Slash commands
│   └── mcp-servers/     # MCP server implementations
├── .scripts/            # Helper bash/js scripts
├── 00_Inbox/ through 06_Metadata/  # Template PARA folders
├── CHANGELOG.md         # Version history
├── CONTRIBUTING.md      # Contribution guidelines
├── README.md           # User documentation
├── CLAUDE-BOOTSTRAP.md # Template for user CLAUDE.md
└── package.json        # Dependencies and version
```

## Key Components

### Commands
- `init-bootstrap` - Main setup wizard that overwrites this file
- `thinking-partner` - Collaborative thinking mode
- `create-command` - Generate new commands
- Other pre-configured commands for vault management

### Scripts
- Installation and setup scripts
- Attachment management utilities
- Web scraping tools (firecrawl)
- Link maintenance utilities

### MCP Servers
- Gemini Vision for image/PDF analysis
- Configured during init-bootstrap if user chooses

## Development Guidelines

### Adding New Features
1. Create feature in appropriate directory
2. Update CHANGELOG.md under "Unreleased"
3. Update README if user-facing
4. Test with fresh clone

### Testing Changes
```bash
# Clone fresh copy
git clone https://github.com/heyitsnoah/claudesidian.git test-claudesidian
cd test-claudesidian
pnpm install
claude run init-bootstrap  # Test the setup flow
```

### Important Files
- **CLAUDE-BOOTSTRAP.md** - Template that init-bootstrap uses
- **package.json** - Version and dependencies
- **.github/release.yml** - GitHub release categorization

## Maintenance Tasks

### Regular Updates
- Review and update dependencies
- Test init-bootstrap flow
- Update documentation for clarity
- Check for broken scripts

### User Support
- Issues at: https://github.com/heyitsnoah/claudesidian/issues
- Keep README clear and comprehensive
- Ensure init-bootstrap handles edge cases

## Note for Contributors

Remember that users will run `init-bootstrap` which:
1. Reads CLAUDE-BOOTSTRAP.md as template
2. Asks personalization questions
3. **Overwrites this CLAUDE.md** with user's configuration
4. Sets up their personal Obsidian vault

This separation ensures the repository maintenance instructions (this file) don't interfere with user's personal vault configuration.