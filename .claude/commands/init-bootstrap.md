---
name: init-bootstrap
description: Interactive setup wizard that helps new users create a personalized CLAUDE.md file based on their Obsidian workflow preferences
allowed-tools: [Read, Write, MultiEdit, Bash, Task]
argument-hint: "(optional) path to existing vault or 'new' for fresh setup"
---

# Initialize Bootstrap Configuration

This command helps you create a personalized CLAUDE.md configuration file by asking questions about your Obsidian workflow and preferences.

## Task

Read the CLAUDE-BOOTSTRAP.md template and interactively gather information about the user's:
- Existing vault structure (if any)
- Workflow preferences
- Note-taking style
- Organization methods
- Specific requirements

Then generate a customized CLAUDE.md file tailored to their needs.

## Process

1. **Initial Environment Setup**
   - Check current folder name and ask if they want to rename it
   - If yes, guide them through renaming (handle parent directory move)
   - Check for package.json and install dependencies:
     - Try `pnpm install` first (faster, better)
     - Fall back to `npm install` if pnpm not available
   - Verify core dependencies are installed
   - Check git status:
     - If no .git folder: Initialize git repository
     - If has remote origin: Remove it to disconnect from claudesidian
     - If clean local repo: Ready to go
   - Create base folder structure (00_Inbox through 06_Metadata)

2. **Check Existing Configuration**
   - Look for existing CLAUDE.md
   - If exists, ask if they want to update or start fresh
   - Check for CLAUDE-BOOTSTRAP.md template

3. **Gather Vault Information**
   - Search common locations for existing Obsidian vaults (.obsidian folder)
   - Check: ~/Documents, ~/Desktop, home directory, current directory parent
   - If found, ask: "Found Obsidian vault at [path]. Is this the vault you want to import?"
   - Count files correctly: `find [path] -type f -name "*.md" | wc -l` (no depth limit)
   - Show vault size: `du -sh [path]`
   - Analyze file naming patterns: check for dates (YYYY-MM-DD), kebab-case, Title Case, etc.
   - Detect folder organization: PARA, Zettelkasten, custom structure
   - Check for daily notes pattern, templates folder, attachments location
   - If not the right one or none found, ask for path to existing vault
   - If no existing vault, they're starting fresh

4. **Ask Configuration Questions**
   - "What's your name?" (for personalization)
   - "Would you like me to research your public work to better understand your context?"
     - If yes: Search and show findings, ask "Is this you?" to disambiguate
     - Save relevant context about their work, writing style, areas of expertise
   - "Do you follow the PARA method or have a different organization system?"
   - "What are your main use cases? (research, writing, project management, knowledge base, daily notes)"

   **If using PARA, ask specific setup questions:**
   [PARA Method by Tiago Forte](https://fortelabs.com/blog/para/)
   - "What active projects are you working on?" (Create folders in 01_Projects)
   - "What areas of responsibility do you maintain?" (e.g., Work, Health, Finance, Family)
   - "What topics do you research frequently?" (Set up in 03_Resources)
   - "Any projects you recently completed?" (Can archive with summaries)

   **General preferences:**
   - "Do you use any specific plugins or tools with Obsidian?"
   - Analyze existing files to detect naming convention automatically
   - "Do you work with attachments frequently? (images, PDFs, etc.)"
   - "Do you use git for version control?"
   - "Any specific websites or resources you reference often?"
   - "Do you have any specific writing style preferences?"
   - "Are there any workflows or patterns you want Claude to follow?"
   - "Would you like a weekly review ritual? (e.g., Thursday project review)"
   - "Do you prefer 'thinking mode' (questions/exploration) vs 'writing mode'?"

5. **Optional Tool Setup**

   **Gemini Vision (already included)**
   - Ask: "Gemini Vision is already included for analyzing images, PDFs, and videos. Would you like to activate it?"
   - Explain: "You just need a free API key from Google. This lets Claude analyze any visual content in your vault."
   - If yes:
     - Guide to get API key from https://aistudio.google.com/apikey (free, takes 30 seconds)
     - Help add to shell profile (.zshrc, .bashrc, etc.)
     - Run `claude mcp add --scope project gemini-vision node .claude/mcp-servers/gemini-vision.mjs`
     - Configure .mcp.json with API key
     - Test the connection with a sample command

   **Firecrawl (already included)**
   - Ask: "Firecrawl scripts are included for saving web content. Would you like to set them up?"
   - Explain: "This lets you save entire websites as markdown. You just need a free API key from firecrawl.dev"
   - If yes:
     - Guide to get API key from https://firecrawl.dev (free tier available)
     - Help configure the scripts in .scripts/
     - Show example usage: `.scripts/firecrawl-scrape.sh https://example.com`

6. **Generate Custom Configuration**
   - Save preferences to `.claude/vault-config.json`:
     ```json
     {
       "user": {
         "name": "Jane Smith",
         "context": "Tech writer, founder of XYZ startup, author of...",
         "publicProfile": true
       },
       "vaultPath": "/path/to/existing/vault",
       "fileNamingPattern": "detected-pattern",
       "organizationMethod": "PARA",
       "primaryUses": ["research", "writing", "projects"],
       "tools": {
         "geminiVision": true,
         "firecrawl": false
       },
       "projects": ["Book - Productivity", "SaaS App"],
       "areas": ["Newsletter", "Health"],
       "importedAt": "2025-01-13"
     }
     ```
   - Start with CLAUDE-BOOTSTRAP.md as base
   - Add user-specific sections:
     - Custom folder structure with their actual projects/areas
     - Personal workflows
     - Preferred tools and scripts
     - Specific guidelines
     - MCP configuration if set up
   - Include their websites/resources if provided
   - Add any custom naming conventions
   - Pre-populate with their projects and areas:
     - Create project folders in 01_Projects/
     - Create area folders in 02_Areas/
     - Create resource topics in 03_Resources/
     - Add README files explaining each project/area

7. **Import Existing Vault (if applicable)**
   - If user has existing vault:
     - Create OLD_VAULT folder: `mkdir OLD_VAULT`
     - Copy entire vault preserving structure: `cp -r [vault-path]/* ./OLD_VAULT/`
     - Copy Obsidian configuration: `cp -r [vault-path]/.obsidian ./`
     - Check for and copy other important files:
       - `.trash/` (Obsidian's trash folder)
       - `.smart-connections/` (if using that plugin)
       - Any workspace files: `.obsidian.vimrc`, etc.
     - Skip copying: `.git/` (they'll have their own), `.claude/` (using ours)
     - Show summary: "Imported your vault to OLD_VAULT/ (X files, Y folders)"
     - Explain: "Your original structure is preserved in OLD_VAULT. You can gradually migrate files to the PARA folders as needed."

8. **Create Supporting Files**
   - Generate initial folder structure if new vault
   - Create README files for main folders
   - For each project folder, create subfolders:
     - Research/ (source materials)
     - Chats/ (AI conversations)
     - Daily Progress/ (running log)
   - Create 05_Attachments/Organized/ directory
   - Set up .gitignore if using git (include .mcp.json, node_modules)
   - Create initial templates if requested
   - Create WEEKLY_REVIEW.md if user wants review ritual
   - Remove FIRST_RUN marker file if it exists
   - Make initial git commit if repository was initialized

9. **Run Test Commands**
   - Execute `pnpm vault:stats` to verify scripts work
   - Test attachment commands if folders exist
   - Test MCP tools if configured
   - Verify git is tracking files correctly

10. **Provide Next Steps**
   - Summary of what was created and configured
   - Quick start guide specific to their setup
   - List of available commands they can use
   - Test commands to verify everything works
   - Suggestions for first tasks based on their use cases
   - How to modify configuration later

## Example Output

```markdown
# Your Obsidian Vault Configuration

Generated on: [Date]
Based on your preferences for: [main use cases]
Setup completed with: ✅ Dependencies ✅ Folder structure ✅ Git initialized

## Your Custom Folder Structure

[Their specific structure with explanations]

## Your Workflows

### Daily Routine
[Based on their answers]

### Project Management
[Their specific approach]

### Research Method (Noah Brier Style)
- Capture everything you read
- Let important ideas naturally resurface
- Start with writing to test understanding
- Use search, not tags, to find things
- [Learn more from Noah's system](https://every.to/superorganizers/ceo-by-day-internet-sleuth-by-night-267452)

### Weekly Review Ritual
[If enabled: Every Thursday at 4pm, review all projects]

## Your Preferences

### File Naming
- Pattern: [their convention]
- Examples: [specific examples]

### Tools & Scripts
[Relevant scripts for their workflow]

## MCP Servers (if configured)

### Gemini Vision
- Status: ✅ Configured and tested
- API Key: Set in .mcp.json
- Test with: `Use gemini-vision to analyze [image path]`

## Available Commands

### Vault Management
- `pnpm vault:stats` - Show vault statistics
- `pnpm attachments:list` - List unprocessed attachments
- `pnpm attachments:organized` - Count organized files

### Claude Commands
- `claude run thinking-partner` - Collaborative thinking mode
- `claude run daily-review` - Review your day
- `claude run init-bootstrap` - Re-run this setup

## Quick Start

1. [Personalized first step]
2. [Next action based on their goals]
3. [Specific to their workflow]

## Pro Tips from Research Masters

- **Be a token maximalist**: Provide lots of context to Claude
- **Writing scales**: Document everything for future reference ([Noah Brier](https://every.to/superorganizers/ceo-by-day-internet-sleuth-by-night-267452))
- **Trust emergence**: Important ideas will keep surfacing
- **Start with writing**: Always begin projects in text form
- **Review regularly**: Set aside time weekly to prune and update
- **PARA Method**: Projects, Areas, Resources, Archive ([Tiago Forte](https://fortelabs.com/blog/para/))

## Setup Summary

✅ Dependencies installed (pnpm/npm)
✅ Folder structure created
✅ Git repository initialized and disconnected from original
✅ CLAUDE.md personalized
✅ First-run setup completed
[✅ MCP Gemini Vision configured - if set up]
[✅ First commit made - if git was initialized]
```

## Interactive Example

```
User: claude run init-bootstrap
Assistant: Welcome! I'll help you set up your personalized Obsidian + Claude configuration.

First, let me check your setup...

📁 **Folder Name Check**
Current folder: claudesidian
Would you like to rename this folder to something more personal? (e.g., my-vault, knowledge-base, obsidian-notes)
*Why: Your vault should have a name that makes sense to you - you'll see it every day!*

[If yes: Handles the rename by moving to parent directory and back]

Now setting up your environment...

📦 **Installing Dependencies**
[Checks for pnpm, uses npm if not available]
[Installs dependencies with pnpm/npm]
*Why: These tools enable Claude Code to work with your vault effectively*

🔓 **Disconnecting from Original Repository**
[Removes git remote to disconnect from original]
*Why: This ensures you won't accidentally push your personal notes to the public repo*

📂 **Creating PARA Folder Structure**
[Creates folders: 00_Inbox through 06_Metadata]
*Why: PARA method helps organize your knowledge into Projects, Areas, Resources, and Archive*

🎯 **Finalizing Setup**
[Checks git status and removes first-run marker]
*Why: Git gives you version control, and removing the marker ensures you won't see the welcome message again*

✅ Folder renamed (if requested)
✅ Dependencies installed
✅ Core folders created
✅ Git repository ready (disconnected from original claudesidian)
✅ First-run marker removed

Now let me ask you a few questions to customize your setup:

🔍 **Searching for existing Obsidian vaults...**
[Searches ~/Documents, ~/Desktop, ~/, and parent directories]

Found Obsidian vault at: ~/Documents/MyNotes
📊 Vault stats: 2,517 markdown files, 1.1GB total size
Is this the vault you'd like to import? (yes/no/different path)

User: yes

Great! I'll help you import your existing notes into the PARA structure.

1. **What's your name?** (This helps me personalize your experience)

User: Noah Brier

2. **Would you like me to research your public work?**
   This helps me better understand your context and tailor the setup to your needs.

User: Yes

[Searches for information]

I found several Noah Briers online:
- Noah Brier, co-founder of Variance and Percolate, writer at every.to
- Noah Brier, photographer based in Portland
- Noah Brier, data scientist at Microsoft

Which one is you? (or none of these)

User: The first one - Variance and Percolate

Great! I see you write about technology, creativity, and building products. I'll keep this context in mind.

3. **What will you primarily use this vault for?**
   (research, writing, project management, daily notes, knowledge base, or combination?)

User: I'll use it for research and writing, plus managing client projects

Assistant: Great! I'll configure your vault for research, writing, and client project management.

2. **What specific projects are you currently working on?**
   (I'll create folders for each in 01_Projects)

User: I'm writing a book about productivity systems, building a SaaS app, and planning a conference talk

Assistant: Perfect! I'll set up project folders for:
   - 01_Projects/Book - Productivity Systems/
   - 01_Projects/SaaS App Development/
   - 01_Projects/Conference Talk/

3. **What ongoing areas of responsibility do you maintain?**
   (These go in 02_Areas - things without an end date)

User: My newsletter, health & fitness, personal finances, and family activities

Assistant: I'll create area folders for:
   - 02_Areas/Newsletter/
   - 02_Areas/Health & Fitness/
   - 02_Areas/Finances/
   - 02_Areas/Family/

4. **What topics do you frequently research or reference?**
   (I'll organize these in 03_Resources)

User: AI tools, productivity methods, SaaS metrics, and writing techniques

Assistant: Setting up resource folders for:
   - 03_Resources/AI Tools/
   - 03_Resources/Productivity Methods/
   - 03_Resources/SaaS Metrics/
   - 03_Resources/Writing Techniques/

[Continues with questions...]

**Gemini Vision Setup**
Gemini Vision is already included in claudesidian! It can analyze images, PDFs, and videos in your vault.
To activate it, you just need a free Google API key (takes 30 seconds).
Would you like to set it up now?

User: Yes, that sounds useful

Assistant: Excellent! Here's how to get your API key:
1. Go to https://aistudio.google.com/apikey
2. Click "Create API Key"
3. Copy the key (starts with AIzaSy...)

Once you have it, paste it here and I'll configure everything for you.