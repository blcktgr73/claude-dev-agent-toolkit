# Debugging Toolkit Plugin

## Overview
Systematic debugging workflow with specialized agents for bug analysis, error detection, code diagnosis, solution design, implementation, and validation.

## Features

### Specialized Agents
- **bug-analyst**: Issue triage and classification
- **error-detective**: Log analysis and error tracking
- **code-diagnostician**: Code quality and pattern analysis
- **fix-architect**: Solution design with minimal side effects
- **bugfix-implementer**: Fix implementation with proper standards
- **fix-validator**: Testing and quality assurance for fixes
- **bug-documenter**: Documentation and knowledge management

### Slash Commands
- `/bugfix-workflow`: Complete debugging workflow from analysis to documentation

## Usage Example

```
/bugfix-workflow Button not responding to clicks --type=ui --scope=file
```

This orchestrates:
1. **Bug Analyst** - Analyzes issue and gathers context
2. **Error Detective** - Investigates error logs and stack traces
3. **Code Diagnostician** - Examines code quality and patterns
4. **Fix Architect** - Designs optimal fix strategy
5. **Bugfix Implementer** - Implements the fix
6. **Fix Validator** - Validates fix and ensures no regressions
7. **Bug Documenter** - Documents fix and prevention guidelines

## Workflow Parameters

```bash
/bugfix-workflow [description] [--severity=low|medium|high|critical]
                 [--scope=local|file|module|global]
                 [--type=logic|syntax|runtime|performance|ui]
```

### Severity Levels
- **critical**: Production-breaking issues (max 30min)
- **high**: Major functionality issues (max 20min)
- **medium**: Moderate issues (max 15min)
- **low**: Minor issues (max 10min)

### Scope Levels
- **local**: Single function bug
- **file**: File-level issue
- **module**: Module-wide problem
- **global**: Architectural/system-wide issue

### Bug Types
- **logic**: Business logic errors
- **syntax**: Code syntax problems
- **runtime**: Runtime errors and exceptions
- **performance**: Performance bottlenecks
- **ui**: User interface issues

## Quality Gates

### Gate 1: Issue Understanding
- ✅ Root cause identified
- ✅ Reproduction steps confirmed
- ✅ Impact scope defined

### Gate 2: Solution Validation
- ✅ Multiple approaches evaluated
- ✅ Risk assessment completed
- ✅ Performance impact considered

### Gate 3: Implementation Quality
- ✅ All tests passing
- ✅ Code quality standards met
- ✅ No new vulnerabilities
- ✅ No performance regressions

## Example Scenarios

### React Component Bug
```
/bugfix-workflow useState hook not updating component --type=ui --scope=file
```

### Python API Error
```
/bugfix-workflow 500 error on POST /api/users --severity=high --type=runtime --scope=module
```

### Performance Issue
```
/bugfix-workflow App becomes slow after 10 minutes --type=performance --scope=global
```

## Installation

Copy the `03-debugging` folder to `.claude/plugins/` and restart Claude Code.

## Related Plugins

- **04-language-tools**: Language-specific debugging tools
- **02-development**: Testing and quality practices
