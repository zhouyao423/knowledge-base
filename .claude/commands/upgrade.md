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

### 1. **Version Check & Setup**
   - Get current version from package.json
   - Fetch latest release from GitHub (heyitsnoah/claudesidian)
   - Create timestamped backup in `.backup/upgrade-YYYY-MM-DD-HHMMSS/`
   - Fetch upstream changes: `git fetch upstream --tags`

### 2. **Create Upgrade Checklist**
   - Get list of SYSTEM files that need checking (NOT user content):
     ```bash
     # Only check claudesidian system files, not user notes
     git diff HEAD upstream/main --name-only | grep -E '^(\.claude/|\.scripts/|package\.json|CHANGELOG\.md|README\.md|\.gitignore)'
     ```
   - Explicitly EXCLUDE:
     - User content folders (00_Inbox, 01_Projects, etc.)
     - User's CLAUDE.md (their personalized version)
     - vault-config.json (user's vault configuration)
     - .obsidian/ (user's Obsidian settings)
     - Any .md files in the root except README and CHANGELOG
   - Create `.upgrade-checklist.md` with only system files that differ
   - Mark each file with status: `[ ] pending`, `[x] updated`, `[-] skipped`
   - Group files by type for easier review:
     ```markdown
     ## Commands (12 files)
     [ ] .claude/commands/init-bootstrap.md
     [ ] .claude/commands/release.md
     [ ] .claude/commands/thinking-partner.md
     ...

     ## Settings (2 files)
     [ ] .claude/settings.json
     [ ] .claude/settings.local.json

     ## Core Files (3 files)
     [ ] package.json
     [ ] CHANGELOG.md
     [ ] README.md
     ```

### 3. **File-by-File Review**
   For EACH file in the checklist:
   1. Show the diff: `git diff HEAD upstream/main -- [file]`
   2. Determine update strategy:
      - **Direct replace**: Commands, agents, scripts with no user changes
      - **Skip**: User's CLAUDE.md, vault-config.json, .mcp.json
      - **Merge needed**: Files with both upstream and user changes
   3. Apply the update
   4. Mark complete in checklist: `[x]`
   5. Move to next file

### 4. **Update Types**
   - **Safe to replace**: `.claude/commands/*.md`, `.claude/agents/*.md`, `.scripts/*`
   - **Needs review**: `package.json` (preserve user's custom scripts)
   - **Never touch**: User content folders, CLAUDE.md, API configs

### 5. **Progress Tracking**
   - Save progress after each file in `.upgrade-checklist.md`
   - If interrupted, can resume from where you left off
   - Show progress: "Updating file 5 of 23..."
   - Clear indication of what's been done and what's remaining

### 6. **Final Steps**
   - Update version in package.json
   - Verify all commands work
   - Clean up checklist file (or keep for reference)
   - Show summary of what was updated

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

## Common Pitfalls to Avoid

### ⚠️ Selective Updates Problem
**Never cherry-pick files based only on release notes!** This leads to:
- Missing critical command updates
- Incomplete feature implementations
- Broken dependencies between files
- Users not getting all improvements

**Always use `git diff HEAD upstream/main --name-only`** to get the complete list of changed files, then update ALL relevant files systematically.

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
📦 Current version: 0.8.2
🆕 Latest version: 0.8.3

💾 Creating backup to .backup/upgrade-2025-09-13-142030/

📋 Creating upgrade checklist...
Checking system files only (not your personal notes)...
Found 15 system files with updates available

Created .upgrade-checklist.md to track updates:

## Commands (8 files)
[ ] .claude/commands/init-bootstrap.md
[ ] .claude/commands/release.md
[ ] .claude/commands/thinking-partner.md
[ ] .claude/commands/upgrade.md
[ ] .claude/commands/daily-review.md
[ ] .claude/commands/inbox-processor.md
[ ] .claude/commands/research-assistant.md
[ ] .claude/commands/weekly-synthesis.md

## Settings (1 file)
[ ] .claude/settings.json

## Core Files (3 files)
[ ] package.json
[ ] CHANGELOG.md
[ ] README.md

## Scripts (3 files)
[ ] .scripts/vault-stats.sh
[ ] .scripts/firecrawl-scrape.sh
[ ] .scripts/setup-mcp.sh

Starting file-by-file review...

📄 File 1/15: .claude/commands/init-bootstrap.md
   Status: No local changes detected
   Action: Direct update from upstream
   [x] Updated

📄 File 2/15: .claude/commands/release.md
   Status: No local changes detected
   Action: Direct update from upstream
   [x] Updated

📄 File 3/15: .claude/settings.json
   Status: Has local changes (your custom hooks)
   Showing diff...
   Action: Merge needed - preserving your hooks, adding new features
   [x] Merged

[... continues through all files ...]

🎉 Upgrade complete!
📈 claudesidian 0.8.2 → 0.8.3

✅ Updated: 14 files
⏭️ Skipped: 1 file (CLAUDE.md - user customization)

Summary of changes:
- Fixed init-bootstrap vault selection
- Improved SessionStart hooks
- Enhanced user identification prompts
- Updated all commands to latest versions
```

This intelligent upgrade system leverages Claude's semantic understanding to provide the smoothest possible upgrade experience while ensuring no user customizations are lost.