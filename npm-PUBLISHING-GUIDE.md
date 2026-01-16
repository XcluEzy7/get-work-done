# GWD npm Package Publishing Guide

## Overview

This guide explains how to publish the `get-work-done-cc` package to npm, separate from the Ralph system components.

## Package Structure

The current repository contains multiple products:
- **GWD CLI Tool**: `get-work-done-cc` (ready for npm)
- **Ralph System**: Autonomous agent loop (separate)
- **Flowchart**: React visualization app (separate)

## Ready for npm Publishing

### Files Included
The `package.json` is configured to include only GWD-related files:
```json
{
  "files": [
    "bin",
    "commands/gwd", 
    "get-work-done",
    "agents",
    "GWD-STYLE.md",
    "CHANGELOG.md",
    "LICENSE"
  ]
}
```

### Files Excluded
These files are NOT part of the npm package:
- `ralph.sh` - Ralph loop script
- `prompt.md` - Ralph instructions
- `README.md` - Ralph documentation
- `flowchart/` - React app
- `skills/` - Claude skills
- `test-*.sh` - Test scripts
- `.planning/` - Planning files

## Publishing Steps

### 1. Prerequisites
```bash
# Check npm authentication
npm whoami

# If not logged in:
npm login
```

### 2. Test Package
```bash
# Dry run to verify files
npm pack --dry-run

# Create actual package
npm pack

# Test installation locally
npm install ./get-work-done-cc-1.5.15.tgz
```

### 3. Publish
```bash
# Publish to public registry
npm publish --access public

# Verify publication
npm view get-work-done-cc
```

### 4. Post-Publishing Verification
```bash
# Test via npx
npx get-work-done-cc@latest --help

# Test in clean directory
mkdir /tmp/gwd-test
cd /tmp/gwd-test
npx get-work-done-cc@latest
ls .claude/get-work-done/  # Should contain installed files
```

## Version Strategy

### Current Version
- Package: `1.5.15`
- Last published version: None (first time)

### Recommendations
- **Option 1**: Keep `1.5.15` if positioning as direct replacement
- **Option 2**: Bump to `2.0.0` due to breaking command name changes:
  - `gsd:*` → `gwd:*` commands
  - User workflows need updating

## Breaking Changes Notice

### Command Names
All commands changed from `gsd:*` to `gwd:*`:
```bash
# Old commands (deprecated)
gsd:help
gsd:new-project
gsd:execute-plan
# ... (28 total)

# New commands (current)
gwd:help
gwd:new-project  
gwd:execute-plan
# ... (28 total)
```

### Migration Guide for Users
Users updating from old package should:
1. Update command references in workflows
2. Reinstall package: `npm install get-work-done-cc@latest`
3. Update any hardcoded paths

## Repository Structure for Publishing

The repository structure is optimized for:
1. **npm Package**: Root directory files
2. **Development**: Full repository with all components
3. **Documentation**: Comprehensive in GWD-STYLE.md

## Quality Assurance

### Tests Completed
- ✅ All 38 functionality tests pass
- ✅ Package validation successful
- ✅ No broken file references
- ✅ Clean package scope

### Pre-Publish Checklist
- [ ] npm account authenticated
- [ ] Repository pushed to GitHub
- [ ] Version strategy decided
- [ ] npm pack --dry-run successful
- [ ] Local installation tested
- [ ] Breaking changes documented

## Migration Summary

For complete migration details, see: [GSD-TO-GWD-MIGRATION.md](./GSD-TO-GWD-MIGRATION.md)

The `get-work-done-cc` package is ready for npm publication with clean scope and comprehensive testing.