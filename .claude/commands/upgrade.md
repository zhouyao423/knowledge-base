---
name: upgrade
description: Intelligently upgrade claudesidian with new features while preserving user customizations using AI-powered semantic analysis
allowed-tools: [Read, Write, Edit, MultiEdit, Bash, WebFetch, Grep, Glob]
argument-hint: "(optional) 'check' to preview changes, 'force' to skip confirmations"
---

# Smart Upgrade Command

Intelligently upgrades your claudesidian installation by fetching the latest release from GitHub and using AI-powered semantic analysis to merge new features with your existing customizations. Preserves user intent while adding new capabilities.

## Task

1. Check GitHub for the latest claudesidian release
2. Download and analyze what has changed since your version
3. Use Claude's semantic understanding to identify user customizations
4. Intelligently merge new features with existing customizations
5. Safely apply updates while preserving user data and preferences
6. Create backups and provide rollback options

## Process

### 1. **Version Check & Release Fetch**
   - Get current version from package.json
   - Fetch latest release from GitHub API (heyitsnoah/claudesidian)
   - Compare versions and show what updates are available
   - Download changelog to understand what's new

### 2. **Smart File Analysis**
   - Scan for files that have changed between versions
   - Categorize files into update safety levels:
     - 🤖 **AI-Mergeable**: Commands, agents, templates (analyze for customizations)
     - ⚡ **Auto-Safe**: New files, scripts, dependencies
     - 🛡️ **Never Touch**: User content, CLAUDE.md, .mcp.json

### 3. **Semantic Customization Detection**
   For each AI-mergeable file, Claude analyzes:
   - "What customizations has the user made?"
   - "What's the user's intent behind these changes?"
   - "What new features are being added upstream?"
   - "How can I preserve their style/preferences while adding new capabilities?"

### 4. **Intelligent Merge Generation**
   - Create hybrid versions that combine:
     - User's writing style and preferences
     - User's custom prompts and workflows
     - New upstream features and capabilities
     - Improved functionality from latest version
   - Generate preview of proposed changes

### 5. **Safe Application**
   - Create timestamped backup in `.backup/upgrade-YYYY-MM-DD-HHMMSS/`
   - Apply updates incrementally with validation
   - Test critical functionality after each change
   - Provide rollback instructions if issues occur

### 6. **Post-Upgrade Verification**
   - Verify all commands still work
   - Check that MCP servers are still configured
   - Test custom workflows are preserved
   - Update version tracking

## Update Categories

### 🤖 AI-Powered Intelligent Merge
**Commands** (`.claude/commands/*.md`):
- Analyze user's prompt style, output preferences, workflow modifications
- Merge new features with existing customizations
- Preserve user's tone, structure, and specific requirements

**Agents** (`.claude/agents/*.md`):
- Understand user's interaction preferences
- Combine new capabilities with existing personality
- Maintain user's established workflows

**Templates** (`06_Metadata/Templates/*.md`):
- Preserve custom fields and structure
- Add new template features
- Maintain user's formatting preferences

### ⚡ Automatic Safe Updates
- **New commands/agents**: Purely additive, no conflicts
- **Scripts** (`.scripts/*`): Utility functions, safe to replace
- **Dependencies** (`package.json`): Security and feature updates
- **Documentation**: README, CONTRIBUTING updates

### 🛡️ Never Modified
- **User content**: All `00_*` through `06_*` folders (except templates)
- **Personal config**: User's `CLAUDE.md`
- **API keys**: `.mcp.json`, environment variables
- **Git history**: User's commits and branches

## Smart Conflict Resolution

When Claude detects conflicts:

### Example Scenarios:

**Scenario 1: Command Enhancement**
```
📝 thinking-partner command has updates:

YOUR VERSION: Custom concise output format, specific industry focus
NEW VERSION: Added video analysis capability, improved questioning flow

🤖 SMART MERGE PROPOSAL:
✅ Keep your concise output style
✅ Keep your industry-specific prompts
✅ Add new video analysis features
✅ Integrate improved questioning (adapted to your style)

Options:
1. 🎯 Apply smart merge (recommended)
2. 👀 Show detailed diff first
3. 🚫 Skip this update
4. 💾 Replace with new version (backup yours)
```

**Scenario 2: Template Updates**
```
📋 Project Template has changes:

YOUR VERSION: Added custom fields for client info, budget tracking
NEW VERSION: Enhanced metadata structure, new automation hooks

🤖 SMART MERGE PROPOSAL:
✅ Preserve your custom client/budget fields
✅ Add new metadata enhancements
✅ Integrate automation hooks
✅ Maintain your field ordering

Apply merge? (y/n/preview)
```

## Command Usage

### Preview Mode (Recommended First Run)
```
/upgrade check
```
- Shows what would be updated
- Displays intelligent merge previews
- No changes made to files
- Safe to run anytime

### Interactive Upgrade
```
/upgrade
```
- Step-by-step confirmation for each change
- Shows before/after for modified files
- Allows selective application of updates
- Creates automatic backups

### Batch Upgrade (Advanced)
```
/upgrade force
```
- Applies all safe updates automatically
- Still prompts for complex merges
- Faster for users comfortable with the process
- Full backup created before starting

## Safety Features

### Automatic Backups
- Complete backup before any changes: `.backup/upgrade-[timestamp]/`
- Individual file backups for each modification
- Backup includes current git state and uncommitted changes

### Rollback Support
```
# If upgrade causes issues:
/rollback-upgrade [timestamp]
# Restores from specific backup
```

### Verification Steps
- Post-upgrade functionality testing
- Command validation (runs test commands)
- MCP server connectivity check
- Git repository integrity verification

### Incremental Application
- Updates applied one file at a time
- Validation after each critical change
- Stops on first error with clear diagnostics
- Easy to identify which change caused issues

## Error Handling

### Common Scenarios
- **No internet connection**: Graceful failure with offline options
- **GitHub API rate limits**: Intelligent retry with backoff
- **Merge conflicts**: Clear explanation and manual resolution options
- **Permission issues**: Helpful guidance on fixing file permissions

### Recovery Options
- **Partial failure**: Continue from last successful step
- **Complete failure**: Full rollback to pre-upgrade state
- **Git conflicts**: Merge upstream changes with local commits
- **Dependency issues**: Fallback to previous working versions

## Advanced Features

### Custom Merge Rules
Users can create `.upgrade-rules.json` to specify:
- Files to always skip
- Custom merge preferences
- Automatic approval for specific change types
- Backup retention policies

### Integration with Git
- Commits each major change separately
- Meaningful commit messages describing updates
- Preserves user's branch structure
- Handles git conflicts intelligently

### Selective Updates
```
/upgrade commands-only    # Update just commands
/upgrade agents-only      # Update just agents
/upgrade scripts-only     # Update just scripts
/upgrade deps-only        # Update just dependencies
```

## Example Session

```
> /upgrade

🔍 Checking for updates...
📦 Current version: 0.2.3
🆕 Latest version: 0.3.1 (3 updates available)

📋 Changes detected:
✨ 2 new commands: /export-notes, /sync-mobile
🔧 3 enhanced commands: /thinking-partner, /daily-review, /research-assistant
🤖 1 new agent: productivity-coach
📚 Updated templates with new automation features
⚡ Security updates to dependencies

🤖 Smart merge analysis:
- thinking-partner: Detected your custom concise style → will preserve + add new features
- daily-review: Found your custom questions → will merge with new reflection prompts
- Project Template: Your budget fields + new automation = perfect combination

💾 Creating backup to .backup/upgrade-2025-09-13-142030/

Proceed with intelligent upgrade? (y/n/preview) > y

🎯 Applying smart merges...
✅ thinking-partner: Merged new video analysis with your style
✅ daily-review: Combined new prompts with your custom questions
✅ Added 2 new commands (no conflicts)
✅ Updated dependencies (5 security fixes)

🎉 Upgrade complete!
📈 claudesidian 0.2.3 → 0.3.1

🧪 Testing functionality...
✅ All commands working
✅ MCP servers connected
✅ Git repository clean

New features to try:
- /export-notes - Export your vault to various formats
- Enhanced video analysis in /thinking-partner
- Mobile sync capabilities (see updated README)
```

This intelligent upgrade system leverages Claude's semantic understanding to provide the smoothest possible upgrade experience while ensuring no user customizations are lost.