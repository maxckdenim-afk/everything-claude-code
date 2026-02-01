# everything-claude-code Development Patterns

> Auto-generated skill from repository analysis

## Overview

This codebase is a comprehensive Claude plugin system that provides skills, agents, commands, and hooks for enhanced development workflows. It's built in JavaScript without a specific framework, focusing on extensibility and cross-platform compatibility. The repository follows conventional commit patterns and emphasizes documentation-driven development with multi-language support.

## Coding Conventions

### File Naming
- Use **camelCase** for JavaScript files: `addNewSkill.js`, `crossPlatformUtils.js`
- Use **kebab-case** for directories and markdown files: `add-new-skill/`, `plugin-manifest.md`

### Import/Export Style
```javascript
// Mixed import styles - adapt to context
const { execFileSync } = require('child_process');
import fs from 'fs';

// Mixed export styles
module.exports = { functionName };
export default className;
```

### Commit Convention
- **Format:** `type: description (max 53 chars)`
- **Types:** `fix:`, `feat:`, `docs:`
- **Examples:**
  ```
  feat: add new skill documentation workflow
  fix: resolve plugin manifest validation errors
  docs: update README with new command list
  ```

## Workflows

### Add New Skill
**Trigger:** When someone wants to add a new coding skill or capability  
**Command:** `/add-skill`

1. Create `skills/{skill-name}/SKILL.md` with comprehensive documentation
2. Document skill patterns, examples, and use cases
3. Update `README.md` skills list with new entry
4. Optionally add related commands or agents that support the skill
5. Test skill integration with existing workflows

```markdown
# {Skill Name}

## Overview
Brief description of what this skill teaches

## Patterns
Code patterns and examples

## Commands
Related commands for this skill
```

### Add New Agent
**Trigger:** When someone wants to add a specialized code review or automation agent  
**Command:** `/add-agent`

1. Create `agents/{agent-name}.md` with agent specification
2. Define agent role, capabilities, and interaction patterns
3. Add agent to `.claude-plugin/plugin.json` agents array
4. Update `README.md` with agent description and usage
5. Test agent functionality and integration

```json
{
  "agents": [
    {
      "name": "agent-name",
      "description": "Agent purpose",
      "file": "agents/agent-name.md"
    }
  ]
}
```

### Add New Command
**Trigger:** When someone wants to add a new executable command  
**Command:** `/add-command`

1. Create `commands/{command-name}.md` with command documentation
2. Document command usage, parameters, and examples
3. Update `README.md` commands list with new entry
4. Add command to plugin manifest if needed
5. Test command execution and error handling

### Fix Plugin Manifest
**Trigger:** When plugin validation fails or schema needs updates  
**Command:** `/fix-plugin-manifest`

1. Update `.claude-plugin/plugin.json` structure to match schema
2. Fix field formats (ensure arrays vs strings are correct)
3. Add or remove required fields per validation errors
4. Test validation with Claude plugin system
5. Update documentation to reflect manifest changes

```json
{
  "name": "everything-claude-code",
  "version": "1.0.0",
  "skills": ["skill1", "skill2"],
  "agents": [{"name": "agent1", "file": "agents/agent1.md"}],
  "commands": [{"name": "/command", "description": "Purpose"}]
}
```

### Update Hooks
**Trigger:** When hook functionality needs modification or cross-platform fixes  
**Command:** `/update-hooks`

1. Update `hooks/hooks.json` with new hook configurations
2. Modify corresponding scripts in `scripts/hooks/{hook-name}.js`
3. Test hook execution across platforms (Windows/macOS/Linux)
4. Update hook documentation and usage examples
5. Ensure security best practices in hook scripts

### Documentation Translation
**Trigger:** When adding support for a new language in documentation  
**Command:** `/translate-docs`

1. Create `docs/{lang-code}/` directory structure matching English version
2. Translate all markdown files while maintaining structure and formatting
3. Update `README.md` with language switcher and new language option
4. Ensure consistent terminology across all translated files
5. Test language-specific documentation rendering

### Security Fixes
**Trigger:** When security issues are discovered in command execution or input handling  
**Command:** `/fix-security`

1. Identify vulnerable code patterns (unsafe exec, input validation gaps)
2. Replace unsafe functions: `execSync` → `execFileSync` with proper args
3. Add comprehensive input validation and sanitization
4. Update documentation with security notes and best practices
5. Test security fixes without breaking functionality

```javascript
// Before (unsafe)
const result = execSync(`command ${userInput}`);

// After (secure)
const result = execFileSync('command', [sanitizedInput], options);
```

### Cross-Platform Compatibility
**Trigger:** When bash-specific scripts need to work across all platforms  
**Command:** `/make-cross-platform`

1. Convert `.sh` scripts to `.js` using Node.js cross-platform APIs
2. Add cross-platform utilities in `scripts/lib/` directory
3. Update `hooks/hooks.json` references to point to new JS files
4. Add comprehensive tests in `tests/**/*.test.js` for all platforms
5. Document platform-specific considerations and fallbacks

## Testing Patterns

### Test File Structure
- Test files follow pattern: `*.test.js`
- Place tests in `tests/` directory or alongside source files
- Use descriptive test names that explain the scenario

```javascript
// Example test structure
describe('Skill Management', () => {
  test('should create new skill directory and files', () => {
    // Test implementation
  });
  
  test('should update README with new skill entry', () => {
    // Test implementation
  });
});
```

## Commands

| Command | Purpose |
|---------|---------|
| `/add-skill` | Add a new skill with documentation and examples |
| `/add-agent` | Create a specialized agent for code review or automation |
| `/add-command` | Add a new slash command with documentation |
| `/fix-plugin-manifest` | Fix plugin.json validation errors and schema compliance |
| `/update-hooks` | Update or fix hook configurations and scripts |
| `/translate-docs` | Add complete documentation translations for new languages |
| `/fix-security` | Fix security vulnerabilities in scripts and commands |
| `/make-cross-platform` | Convert bash scripts to Node.js for cross-platform support |