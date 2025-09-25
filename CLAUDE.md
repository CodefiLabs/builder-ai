# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What is Builder AI

Builder AI is a development framework and toolchain designed to transform AI coding agents from "confused interns into productive developers" through structured, spec-driven workflows. It's not a traditional application but rather a system that provides opinionated standards, detailed process documentation, and agent-specific instructions for consistent development practices.

## Installation and Setup Commands

### Global Installation
```bash
# Install Builder AI globally with Claude Code support
curl -sSL https://raw.githubusercontent.com/CodefiLabs/builder-ai/main/setup/base.sh | bash -s -- --claude-code

# Install with both Claude Code and Cursor support
curl -sSL https://raw.githubusercontent.com/CodefiLabs/builder-ai/main/setup/base.sh | bash -s -- --claude-code --cursor
```

### Project Installation
```bash
# Install Builder AI into a project (run from project root)
~/.builder-ai/setup/project.sh

# Install with specific options
~/.builder-ai/setup/project.sh --claude-code --overwrite-instructions --overwrite-standards
```

### Testing and Development
```bash
# Test shell script functions
bash setup/functions.sh

# Validate project installation
ls -la .builder-ai/
ls -la .claude/commands/
```

## Architecture Overview

### Core Directory Structure
- `/setup/` - Installation scripts (bash-based)
- `/instructions/core/` - Main workflow process definitions
- `/instructions/meta/` - Meta-instructions and utilities
- `/standards/` - Development standards and code style guides
- `/commands/` - Quick command references for Claude Code
- `/claude-code/agents/` - Specialized Claude Code agents
- `/config.yml` - System configuration and project type mappings

### Five-Phase Development Workflow
1. **Analyze Product** - Deep codebase analysis and Builder AI installation
2. **Plan Product** - Strategic planning and roadmap creation
3. **Create Spec** - Detailed feature specification generation
4. **Create Tasks** - Task breakdown and implementation planning
5. **Execute Tasks** - Three-phase implementation (pre-execution, execution loop, post-execution)

### Key Components

**Installation System:**
- `setup/base.sh` - Downloads and installs Builder AI globally to `~/.builder-ai/`
- `setup/project.sh` - Installs Builder AI into specific projects
- `setup/functions.sh` - Shared utility functions for installation

**Configuration Management:**
- `config.yml` - Controls agent enablement and project type mappings
- Version tracking (currently 1.4.1) for compatibility
- Support for custom project types with different instruction sets

**Specialized Agents (Claude Code):**
- `context-fetcher` - Gathers relevant project context
- `date-checker` - Validates temporal information
- `file-creator` - Manages file creation workflows
- `git-workflow` - Handles version control operations
- `project-manager` - Oversees project coordination
- `test-runner` - Manages testing workflows

## Default Tech Stack (Standards)

When Builder AI creates new projects or provides guidance, it uses these opinionated defaults:

- **Backend**: Ruby on Rails 8.0+, Ruby 3.2+, PostgreSQL 17+
- **Frontend**: React (latest), Vite build tool, TailwindCSS 4.0+
- **Package Management**: npm, Node.js 22 LTS
- **UI**: Instrumental Components, Lucide React icons
- **Infrastructure**: Digital Ocean, S3/CloudFront, GitHub Actions CI/CD

These can be overridden in project-specific `.builder-ai/product/tech-stack.md`.

## Command Usage Patterns

### Claude Code Commands
When Builder AI is installed in a project, these commands become available:
- `/analyze-product` - Set up mission and roadmap for existing product
- `/plan-product` - Set mission & roadmap for new product
- `/create-spec` - Create spec for new feature
- `/create-tasks` - Break down feature into implementation tasks
- `/execute-tasks` - Build and ship code for feature

### File References
Commands reference instruction files using this pattern:
```markdown
Refer to the instructions located in this file:
@.builder-ai/instructions/core/analyze-product.md
```

## Development Practices

### Installation Script Patterns
- Use `set -e` for error handling
- Source shared functions from `setup/functions.sh`
- Support both base installation and direct GitHub installation modes
- Auto-enable tools based on existing configuration
- Provide detailed progress output with emojis and formatting

### Standards-Driven Development
- Extract repeated patterns to utility functions
- Prioritize code clarity over micro-optimizations
- Use conditional blocks to avoid re-reading context
- Keep files focused on single responsibility
- Follow established naming conventions

### Process Documentation Structure
Instructions use structured XML-like tags:
- `<pre_flight_check>` - Prerequisites and setup
- `<process_flow>` - Step-by-step workflow
- `<step>` - Individual process steps with subagent assignments
- `<instructions>` - Action items within steps
- `<conditional-block>` - Context-aware content loading

## Important Implementation Notes

### Agent Integration
- Configuration supports multiple agent types (Claude Code, Cursor)
- Agent-specific files are generated during project installation
- Commands can be converted between formats (e.g., Claude commands to Cursor rules)

### Project Types
- Default project type uses standard instructions and standards
- Custom project types can specify different instruction/standards paths
- Configuration in `config.yml` under `project_types` section

### Version Management
- Track Builder AI version in config.yml for compatibility
- Installation scripts handle version-specific behaviors
- Support for upgrading existing installations

This repository represents a meta-development tool - it's designed to improve how AI agents approach software development by providing structured workflows and consistent standards.