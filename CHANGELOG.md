# Changelog

All notable changes to claudesidian will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

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

[Unreleased]: https://github.com/heyitsnoah/claudesidian/compare/v0.2.3...HEAD
[0.2.3]: https://github.com/heyitsnoah/claudesidian/compare/v0.2.2...v0.2.3
[0.2.2]: https://github.com/heyitsnoah/claudesidian/compare/v0.2.1...v0.2.2
[0.2.1]: https://github.com/heyitsnoah/claudesidian/compare/v0.2.0...v0.2.1
[0.2.0]: https://github.com/heyitsnoah/claudesidian/compare/v0.1.0...v0.2.0
[0.1.0]: https://github.com/heyitsnoah/claudesidian/releases/tag/v0.1.0