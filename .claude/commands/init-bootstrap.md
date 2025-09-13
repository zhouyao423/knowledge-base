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
   - Check for package.json and run `pnpm install` if needed
   - Verify core dependencies are installed
   - Check git status and initialize if needed
   - Create base folder structure (00_Inbox through 06_Metadata)

2. **Check Existing Configuration**
   - Look for existing CLAUDE.md
   - If exists, ask if they want to update or start fresh
   - Check for CLAUDE-BOOTSTRAP.md template

3. **Gather Vault Information**
   - Ask if they have an existing vault or starting new
   - If existing, explore current folder structure
   - Document any custom organization patterns

4. **Ask Configuration Questions**
   - "Do you follow the PARA method or have a different organization system?"
   - "What are your main use cases? (research, writing, project management, knowledge base, daily notes)"
   - "Do you use any specific plugins or tools with Obsidian?"
   - "What's your preferred naming convention for files?"
   - "Do you work with attachments frequently? (images, PDFs, etc.)"
   - "Do you use git for version control?"
   - "Any specific websites or resources you reference often?"
   - "Do you have any specific writing style preferences?"
   - "Are there any workflows or patterns you want Claude to follow?"

5. **Optional MCP Server Setup**
   - Ask: "Would you like to set up Gemini Vision for analyzing images and PDFs?"
   - If yes:
     - Guide to get API key from https://aistudio.google.com/apikey
     - Help add to shell profile (.zshrc, .bashrc, etc.)
     - Run `claude mcp add --scope project gemini-vision node .claude/mcp-servers/gemini-vision.mjs`
     - Configure .mcp.json with API key
     - Test the connection with a sample command

6. **Generate Custom Configuration**
   - Start with CLAUDE-BOOTSTRAP.md as base
   - Add user-specific sections:
     - Custom folder structure
     - Personal workflows
     - Preferred tools and scripts
     - Specific guidelines
     - MCP configuration if set up
   - Include their websites/resources if provided
   - Add any custom naming conventions

7. **Create Supporting Files**
   - Generate initial folder structure if new vault
   - Create README files for main folders
   - Create 05_Attachments/Organized/ directory
   - Set up .gitignore if using git (include .mcp.json, node_modules)
   - Create initial templates if requested
   - Make initial git commit if repository was initialized

8. **Run Test Commands**
   - Execute `pnpm vault:stats` to verify scripts work
   - Test attachment commands if folders exist
   - Test MCP tools if configured
   - Verify git is tracking files correctly

9. **Provide Next Steps**
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

## Setup Summary

✅ Dependencies installed (pnpm install)
✅ Folder structure created
✅ Git repository initialized
✅ CLAUDE.md personalized
[✅ MCP Gemini Vision configured - if set up]
[✅ First commit made - if git was initialized]
```

## Interactive Example

```
User: claude run init-bootstrap
Assistant: Welcome! I'll help you set up your personalized Obsidian + Claude configuration.

First, let me set up your environment...
[Runs pnpm install to install dependencies]
[Creates folder structure if missing]
[Checks git status]

✅ Dependencies installed
✅ Core folders created
✅ Git repository ready

Now let me ask you a few questions to customize your setup:

1. **What will you primarily use this vault for?**
   (research, writing, project management, daily notes, knowledge base, or combination?)

User: I'll use it for research and writing, plus managing client projects

Assistant: Great! I'll configure your vault for research, writing, and client project management.

[Continues with questions...]

Would you like to set up Gemini Vision for analyzing images and PDFs? This requires a Google API key.

User: Yes, that sounds useful

Assistant: Excellent! Here's how to get your API key:
1. Go to https://aistudio.google.com/apikey
2. Click "Create API Key"
3. Copy the key (starts with AIzaSy...)

Once you have it, paste it here and I'll configure everything for you.