# Get Work Done CLI

A meta-prompting, context engineering and spec-driven development system for Claude Code by TÂCHES.

## Overview

**Get Work Done (GWD)** is a comprehensive CLI system that helps developers build software systematically using Claude Code. It provides structured workflows, commands, templates, and specialized agents for efficient development.

## Installation

### Global Installation
```bash
npx get-work-done-cc@latest --global
```

### Local Installation
```bash
npx get-work-done-cc@latest --local
```

## Quick Start

```bash
# Start a new project
/gwd:new-project

# Show all available commands
/gwd:help

# Check project progress
/gwd:progress
```

## What's Included

The `get-work-done-cc` package includes:

### CLI Commands (28 commands)
- **Project Management**: `gwd:new-project`, `gwd:progress`, `gwd:pause-work`, `gwd:resume-work`
- **Planning**: `gwd:plan-phase`, `gwd:research-phase`, `gwd:discuss-phase`
- **Execution**: `gwd:execute-plan`, `gwd:execute-phase`, `gwd:verify-work`
- **Milestones**: `gwd:new-milestone`, `gwd:complete-milestone`, `gwd:audit-milestone`
- **Utilities**: `gwd:help`, `gwd:whats-new`, `gwd:add-todo`, `gwd:check-todos`
- **Debugging**: `gwd:debug`, `gwd:map-codebase`

### Specialized Agents (4 agents)
- **gwd-executor**: Executes plans with atomic commits and checkpoint handling
- **gwd-verifier**: Goal-backward verification of phase completion
- **gwd-integration-checker**: Validates integration across phases
- **gwd-milestone-auditor**: Audits milestone completeness

### Templates & Workflows
- **Planning templates**: Roadmap, requirements, project setup
- **Development templates**: Phase plans, research documentation
- **Verification templates**: User acceptance testing, milestone archives
- **Reference documentation**: Best practices, patterns, guidelines

### Style Guide
Comprehensive development patterns and conventions in `GWD-STYLE.md`.

## Core Concepts

### Meta-Prompting System
Every file is both implementation and specification. Templates teach Claude how to build software systematically through structured prompts and progressive disclosure.

### Context Engineering
- **Size constraints**: Plans optimized for Claude's context window
- **Fresh instances**: Each command spawns clean context
- **Memory persistence**: Via git history and structured files

### Spec-Driven Development
- **Hierarchical planning**: Project → phases → plans → tasks
- **Goal-backward approach**: Start from desired outcomes
- **Atomic execution**: One commit per task with verification

## Usage Examples

### Starting a New Project
```bash
/gwd:new-project
# Follow prompts to define project scope
/gwd:create-roadmap
# Break down into manageable phases
/gwd:plan-phase 1
# Create detailed execution plans
/gwd:execute-phase 1
# Execute the first phase
```

### Brownfield Projects
```bash
/gwd:map-codebase
# Analyze existing codebase first
/gwd:new-project
# Then continue with standard workflow
```

### Debugging Issues
```bash
/gwd:debug "login button doesn't work"
# Interactive debugging with systematic investigation
```

## Repository Structure

```
get-work-done-cc/
├── bin/install.js                 # Installation script
├── commands/gwd/                 # All CLI commands (28 files)
├── get-work-done/               # Templates, workflows, references
│   ├── templates/               # Template files
│   ├── workflows/               # Implementation guides
│   └── references/              # Best practices
├── agents/gwd-*.md              # Specialized agents
├── GWD-STYLE.md                 # Development style guide
├── CHANGELOG.md                   # Version history
└── LICENSE                        # MIT license
```

## Version Information

**Current Version**: 1.5.15
**Breaking Changes**: Yes - commands changed from `gsd:*` to `gwd:*`
**Migration**: See [GSD-TO-GWD-MIGRATION.md](./GSD-TO-GWD-MIGRATION.md)

## Related Projects

This repository is part of a larger development ecosystem:

- **Ralph**: Autonomous AI agent loop for continuous development
  - Uses PRD files for autonomous execution
  - Available at: https://github.com/XcluEzy7/get-work-done

- **Flowchart**: Interactive React visualization of Ralph workflow
  - Demonstrates how the autonomous system works
  - Available at: https://snarktank.github.io/ralph/

## Contributing

When contributing to Get Work Done:
1. Follow patterns in `GWD-STYLE.md`
2. Test all changes with provided test suites
3. Update documentation as needed
4. Maintain backward compatibility where possible

## License

MIT License - see [LICENSE](./LICENSE) file for details.

## Support

- **Documentation**: [GWD-STYLE.md](./GWD-STYLE.md)
- **Change History**: [CHANGELOG.md](./CHANGELOG.md)
- **Migration Guide**: [GSD-TO-GWD-MIGRATION.md](./GSD-TO-GWD-MIGRATION.md)

---

*Get Work Done* - Systematic software development with Claude Code.*