# Changelog

All notable changes to claudesidian will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.6.0] - 2025-01-13

### Added
- Intelligent vault import that preserves existing structure in OLD_VAULT folder
- Auto-detection of existing Obsidian vaults by searching for .obsidian folders
- User research and disambiguation for personalized setup
- Automatic detection of file naming patterns and folder organization
- Vault configuration saved to .claude/vault-config.json for future reference
- Educational explanations during each setup step
- Support for both pnpm and npm package managers
- Comprehensive Obsidian file copying (plugins, trash, settings)
- Clear examples for folder naming when cloning repository

### Changed
- init-bootstrap now imports entire vault structure safely without data loss
- Gemini Vision and Firecrawl prompts clarify tools are already included
- README includes examples of custom folder names when cloning
- Removed unnecessary questions by detecting patterns automatically

## [0.5.0] - 2025-01-13

### Added
- First-run welcome message using SessionStart hook
- FIRST_RUN marker file to detect fresh installations
- Markdown-formatted welcome prompt with setup instructions
- Automatic detection and guidance for new users

### Changed
- init-bootstrap now removes FIRST_RUN marker after setup completion
- Hook configuration uses inline commands (no external scripts needed)

## [0.4.0] - 2025-01-13

### Added
- Simplified setup process with enhanced init-bootstrap command:
  - Automatic disconnection from original repository
  - Folder rename assistance for non-git users
  - Support for both git clone and ZIP download methods
  - Clear prompts for importing existing Obsidian vaults
- Multiple setup paths in README for different user skill levels

### Changed
- init-bootstrap now handles complete environment setup including git management
- README updated with clearer Quick Start instructions for both technical and non-technical users

## [0.3.1] - 2025-01-13

### Fixed
- Removed CLAUDE.md and settings.local.json from repository tracking
- These user-specific files are now generated locally by init-bootstrap
- Added both files to .gitignore to prevent accidental commits
- Clean repository structure for new users

## [0.3.0] - 2025-01-13

### Added
- Intelligent upgrade command (`/upgrade`) with AI-powered semantic merging
- Smart conflict resolution that preserves user customizations while adding new features
- Automatic backup system with rollback capabilities
- Selective update categories (AI-mergeable, auto-safe, protected)
- Based on 2025 best practices for LLM-powered code migration

## [0.2.3] - 2025-01-13

### Changed
- Updated init-bootstrap command and settings configuration

## [0.2.2] - 2025-01-13

### Fixed
- Corrected all documentation to use proper slash command syntax (/command-name)
- Fixed examples showing incorrect 'claude run' syntax
- Updated README, CLAUDE.md, install.sh, and command docs

## [0.2.1] - 2025-01-13

### Changed
- Updated README to use init-bootstrap command instead of install.sh
- Simplified Quick Start instructions to 2-step process
- Added examples of pre-configured commands in README

## [0.2.0] - 2025-01-13

### Added
- Release command for automated version management and releases
- Gemini Vision video analysis support:
  - Local video files (MP4, AVI, MOV, WebM, MKV, WMV, FLV, 3GP, M4V)
  - Direct YouTube URL analysis without download
  - Automatic video processing state detection
- Updated documentation with video analysis examples

### Changed
- Enhanced init-bootstrap command with full environment setup including MCP configuration
- Updated Gemini Vision MCP server to support video formats

## [0.1.0] - 2025-01-13

### Added
- Initial release of claudesidian - Claude Code + Obsidian starter kit
- PARA method folder structure (00_Inbox through 06_Metadata)
- Bootstrap initialization system via `claude run init-bootstrap`
- Pre-configured Claude Code commands:
  - thinking-partner - Collaborative thinking mode
  - inbox-processor - Organize captures
  - research-assistant - Deep dive into topics
  - daily-review - End of day reflection
  - weekly-synthesis - Find patterns in your week
  - create-command - Build new custom commands
  - de-ai-ify - Remove AI writing patterns
  - add-frontmatter - Add metadata to notes
  - init-bootstrap - Interactive setup wizard
- Claude Code agents:
  - thinking-partner agent for exploration and brainstorming
- Helper scripts:
  - firecrawl-batch.sh - Batch web scraping
  - firecrawl-scrape.sh - Single URL scraping
  - fix-renamed-links.js - Fix broken links after renames
  - update-attachment-links.js - Update attachment references
  - transcript-extract.sh - Extract YouTube transcripts
  - vault-stats.sh - Show vault statistics
- Attachment management commands via pnpm
- Gemini Vision MCP server for image/PDF analysis (optional)
- CLAUDE-BOOTSTRAP.md template for configuration
- Comprehensive README with setup instructions
- Install script for automated setup
- Git integration with proper .gitignore

### Changed
- Replaced static CLAUDE.md with dynamic init-bootstrap command

### Security
- API keys stored in environment variables
- .mcp.json gitignored for security

[Unreleased]: https://github.com/heyitsnoah/claudesidian/compare/v0.6.0...HEAD
[0.6.0]: https://github.com/heyitsnoah/claudesidian/compare/v0.5.0...v0.6.0
[0.5.0]: https://github.com/heyitsnoah/claudesidian/compare/v0.4.0...v0.5.0
[0.4.0]: https://github.com/heyitsnoah/claudesidian/compare/v0.3.1...v0.4.0
[0.3.1]: https://github.com/heyitsnoah/claudesidian/compare/v0.3.0...v0.3.1
[0.3.0]: https://github.com/heyitsnoah/claudesidian/compare/v0.2.3...v0.3.0
[0.2.3]: https://github.com/heyitsnoah/claudesidian/compare/v0.2.2...v0.2.3
[0.2.2]: https://github.com/heyitsnoah/claudesidian/compare/v0.2.1...v0.2.2
[0.2.1]: https://github.com/heyitsnoah/claudesidian/compare/v0.2.0...v0.2.1
[0.2.0]: https://github.com/heyitsnoah/claudesidian/compare/v0.1.0...v0.2.0
[0.1.0]: https://github.com/heyitsnoah/claudesidian/releases/tag/v0.1.0