# Claudesidian: Claude Code + Obsidian Starter Kit

Turn your Obsidian vault into an AI-powered second brain using Claude Code.

## What is this?

This is a pre-configured Obsidian vault structure designed to work seamlessly with Claude Code, enabling you to:
- Use AI as a thinking partner, not just a writing assistant
- Organize knowledge using the PARA method
- Maintain version control with Git
- Access your vault from anywhere (including mobile)

## Quick Start

### 1. Clone and Install
```bash
git clone https://github.com/heyitsnoah/claudesidian.git
cd claudesidian
./install.sh  # Automated setup script
```

Or manually:
```bash
pnpm install  # Install dependencies
mkdir -p 05_Attachments/Organized  # Create organized folder
```

### 2. Open in Obsidian (Optional but Recommended)
- Download [Obsidian](https://obsidian.md)
- Open vault from the claudesidian folder
- This gives you a visual interface alongside Claude Code

### 3. Start Claude Code
```bash
# Make sure you have Claude Code installed
# Start it in the vault directory
claude
```

### 4. Your First Session
Tell Claude Code:
```
I'm starting a new project about [topic]. 
I'm in thinking mode, not writing mode.
Please search my vault for any relevant existing notes, 
then help me explore this topic by asking questions.
```

## Folder Structure

```
claudesidian/
├── 00_Inbox/           # Temporary capture point for new ideas
├── 01_Projects/        # Active, time-bound initiatives
├── 02_Areas/           # Ongoing responsibilities
├── 03_Resources/       # Reference materials and knowledge base
├── 04_Archive/         # Completed projects and inactive items
├── 05_Attachments/     # Images, PDFs, and other files
├── 06_Metadata/        # Vault configuration and templates
│   ├── Reference/      # Documentation and guides
│   └── Templates/      # Reusable note templates
└── .scripts/           # Helper scripts for automation
```

## Key Concepts

### Thinking Mode vs Writing Mode

**Thinking Mode** (Research & Exploration):
- Claude asks questions to understand your goals
- Searches existing notes for relevant content
- Helps make connections between ideas
- Maintains a log of insights and progress

**Writing Mode** (Content Creation):
- Generates drafts based on your research
- Helps structure and edit content
- Creates final deliverables

### The PARA Method

**Projects**: Have a deadline and specific outcome
- Example: "Q4 2025 Marketing Strategy"
- Create a folder in `01_Projects/`

**Areas**: Ongoing without an end date
- Example: "Health", "Finances", "Team Management"
- Lives in `02_Areas/`

**Resources**: Topics of ongoing interest
- Example: "AI Research", "Writing Tips"
- Store in `03_Resources/`

**Archive**: Inactive items
- Completed projects with their outputs
- Old notes no longer relevant

## Essential Workflows

### Starting a Research Project

1. Create project folder:
```bash
mkdir -p "01_Projects/My_New_Project/{Research,Chats,Daily_Progress}"
```

2. Tell Claude Code:
```
I'm starting a project on [topic] in 01_Projects/My_New_Project.
I'm in thinking mode. Help me explore this topic.
```

3. Let Claude search your vault and ask clarifying questions

### Daily Capture

1. Create a daily note in `00_Inbox/`
2. Dump thoughts, links, ideas throughout the day
3. Weekly: Process inbox items to appropriate folders

### Synthesizing Research

Ask Claude Code:
```
Can you review all notes in [project folder] 
and create a synthesis of the key themes and insights?
```

## Claude Code Commands

Pre-configured AI assistants ready to use:

- `thinking-partner` - Explore ideas through questions
- `inbox-processor` - Organize your captures  
- `research-assistant` - Deep dive into topics
- `daily-review` - End of day reflection
- `weekly-synthesis` - Find patterns in your week
- `create-command` - Build new custom commands
- `de-ai-ify` - Remove AI writing patterns from text

Run with: `claude run [command-name]`

## Vision & Document Analysis (Optional)

With Gemini MCP configured, you can:
- Analyze images and screenshots
- Extract text from PDFs
- Compare multiple images
- Generate smart filenames
- Process documents

See `.claude/mcp-servers/README.md` for setup

## Helper Scripts

Run these with `pnpm`:

- `attachments:list` - Show unprocessed attachments
- `attachments:organized` - Count organized files
- `attachments:sizes` - Find large files
- `attachments:orphans` - Find unreferenced attachments
- `vault:stats` - Show vault statistics

## Advanced Setup

### Git Integration

Initialize Git for version control:
```bash
git init
git add .
git commit -m "Initial vault setup"
git remote add origin your-repo-url
git push -u origin main
```

Best practices:
- Commit after each work session
- Use descriptive commit messages
- Pull before starting work

### Mobile Access

1. Set up a small server (mini PC, cloud VPS, or home server)
2. Install Tailscale for secure VPN access
3. Clone your vault to the server
4. Use Termius or similar SSH client on mobile
5. Run Claude Code remotely

### Custom Agents

Create specialized agents by saving instructions:

**Thinking Partner** (`06_Metadata/Agents/thinking-partner.md`):
```markdown
You are a collaborative thinking partner.
- Ask clarifying questions
- Help explore connections
- Track insights in a running log
- Never jump to solutions too quickly
```

**Research Assistant** (`06_Metadata/Agents/research-assistant.md`):
```markdown
You are a research assistant.
- Search the vault for relevant information
- Synthesize findings from multiple sources
- Identify gaps in knowledge
- Suggest areas for further exploration
```

## Tips & Best Practices

### From Experience

1. **Start in thinking mode**: Resist the urge to generate content immediately
2. **Be a token maximalist**: More context = better results
3. **Save everything**: Capture chats, fragments, partial thoughts
4. **Trust but verify**: Always read AI-generated content
5. **Break your flow**: AI helps you resume easily

### Common Patterns

**The Daily Review**:
```
What new notes were created today?
What connections can you see between today's work and my existing notes?
```

**The Weekly Synthesis**:
```
Review all notes from this week.
What are the key themes and insights?
What questions remain unanswered?
```

**The Project Retrospective**:
```
This project is complete.
Create a summary of what was learned and accomplished.
What should be archived vs kept accessible?
```

## Troubleshooting

### Claude Code can't find my notes
- Make sure you're running Claude Code from the vault root directory
- Check file permissions
- Verify markdown files have `.md` extension

### Git conflicts
- Always pull before starting work
- Commit frequently with clear messages
- Use branches for experimental changes

### Attachment management
- Run `npm run attachments:create-organized` to set up folders
- Use helper scripts to find orphaned files
- Keep attachments under 10MB for Git

## Philosophy

This setup is based on key principles:

1. **AI amplifies thinking, not just writing**
2. **Local files = full control**
3. **Structure enables creativity**
4. **Iteration beats perfection**
5. **The goal is insight, not just information**

## Contributing

This is a living template. As you develop workflows that work for you:
1. Document them in `06_Metadata/Reference/`
2. Share back with the community
3. Remember: best practices emerge from use, not theory

## Resources

- [Obsidian Documentation](https://help.obsidian.md)
- [PARA Method](https://fortelabs.com/blog/para/)
- [Claude Code Documentation](https://claude.ai/docs)

## Inspiration

This starter kit was inspired by the workflows discussed in:
- [How to Use Claude Code as a Second Brain](https://every.to/podcast/how-to-use-claude-code-as-a-thinking-partner) - Noah Brier's interview with Dan Shipper
- Built by the team at [Alephic](https://alephic.com) - an AI-first strategy and software partner that helps organizations solve complex challenges through custom AI systems

## License

MIT - Use this however you want. Make it your own.

---

*Remember: The bicycle feels wobbly at first, then you forget it was ever hard.*