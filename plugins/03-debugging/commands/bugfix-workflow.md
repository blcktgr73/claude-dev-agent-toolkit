---
description: Systematic debugging workflow from analysis to fix validation
argument-hint: [bug description] [--severity=low|medium|high|critical] [--scope=local|file|module|global] [--type=logic|syntax|runtime|performance|ui]
---

# /bugfix-workflow - Efficient Debugging Command

## Overview
A comprehensive debugging workflow command designed for efficient bug resolution during vibe coding sessions. This command orchestrates specialized agents to systematically identify, analyze, and fix bugs in Python and React codebases.

## Usage
```bash
/bugfix-workflow [description] [--severity=low|medium|high|critical] [--scope=local|file|module|global] [--type=logic|syntax|runtime|performance|ui]
```

## Parameters
- **description**: Brief description of the bug or issue
- **severity**: Bug severity level (default: medium)
- **scope**: Bug impact scope (default: local)  
- **type**: Bug category (default: logic)

## Examples
```bash
# Quick bug fix for React component
/bugfix-workflow "Button not responding to clicks" --type=ui --scope=file

# Critical Python runtime error
/bugfix-workflow "Server crashes on user login" --severity=critical --type=runtime --scope=module

# Performance issue debugging
/bugfix-workflow "Page loads slowly" --type=performance --scope=global
```

## Workflow Steps

### 1. Issue Analysis (bug-analyst)
- **Duration**: 2-5 minutes
- **Objective**: Analyze the reported issue and gather context
- **Deliverables**: 
  - Issue classification and severity assessment
  - Affected files and components identification
  - Reproduction steps (if applicable)
  - Initial hypothesis about root cause

### 2. Error Investigation (error-detective)
- **Duration**: 3-8 minutes  
- **Objective**: Deep dive into error logs, stack traces, and code flow
- **Deliverables**:
  - Comprehensive error analysis
  - Stack trace interpretation
  - Related code path mapping
  - Dependency impact assessment

### 3. Code Diagnosis (code-diagnostician)
- **Duration**: 5-10 minutes
- **Objective**: Examine code quality, patterns, and potential issues
- **Deliverables**:
  - Code smell detection
  - Anti-pattern identification
  - Logic flow analysis
  - Variable state tracking

### 4. Solution Design (fix-architect)
- **Duration**: 3-7 minutes
- **Objective**: Design optimal fix strategy with minimal side effects
- **Deliverables**:
  - Multiple solution approaches
  - Impact analysis for each approach
  - Recommended fix strategy
  - Risk assessment and mitigation

### 5. Implementation (bugfix-implementer)
- **Duration**: 5-15 minutes
- **Objective**: Implement the chosen solution with proper coding standards
- **Deliverables**:
  - Fixed code implementation
  - Inline documentation updates
  - Type safety improvements (Python/TypeScript)
  - Error handling enhancements

### 6. Testing & Validation (fix-validator)
- **Duration**: 3-10 minutes
- **Objective**: Ensure fix works correctly and doesn't introduce regressions
- **Deliverables**:
  - Unit tests for the fix
  - Integration test updates
  - Regression testing checklist
  - Performance impact validation

### 7. Documentation (bug-documenter)
- **Duration**: 2-5 minutes
- **Objective**: Document the fix and prevent similar issues
- **Deliverables**:
  - Fix summary and rationale
  - Updated code comments
  - Knowledge base entry
  - Prevention guidelines

## Quality Gates

### Gate 1: Issue Understanding (After Step 2)
- ✅ Root cause identified with 90%+ confidence
- ✅ Reproduction steps confirmed
- ✅ Impact scope clearly defined
- ✅ Dependencies mapped

### Gate 2: Solution Validation (After Step 4)
- ✅ Multiple solution approaches evaluated
- ✅ Risk assessment completed
- ✅ Performance impact considered
- ✅ Backward compatibility verified

### Gate 3: Implementation Quality (After Step 6)
- ✅ All tests passing
- ✅ Code quality standards met
- ✅ No new security vulnerabilities
- ✅ Performance regression checks passed

## Agent Coordination

### Primary Agents
- **bug-analyst**: Issue triage and classification expert
- **error-detective**: Log analysis and error tracking specialist
- **code-diagnostician**: Code quality and pattern analysis expert
- **fix-architect**: Solution design and architecture specialist
- **bugfix-implementer**: Code implementation and refactoring expert
- **fix-validator**: Testing and quality assurance specialist
- **bug-documenter**: Documentation and knowledge management expert

### Language-Specific Agents (Auto-detected)
- **python-debugger**: Python-specific debugging patterns and tools
- **react-debugger**: React component lifecycle and state debugging
- **typescript-analyzer**: TypeScript type safety and error analysis
- **performance-profiler**: Performance bottleneck identification

## Context Awareness
The workflow automatically adapts based on:
- **File Extensions**: .py, .jsx, .tsx, .ts detection for language-specific approaches
- **Project Structure**: React app vs Python backend vs full-stack detection  
- **Error Types**: Runtime, compile-time, logic, or UI-specific debugging strategies
- **Git History**: Recent changes analysis for regression debugging
- **Dependencies**: Package and version conflict detection

## Output Formats

### Quick Summary (Default)
```
🐛 Bug Fixed: [Issue Description]
⏱️  Time: [Duration]  
🎯 Root Cause: [Brief explanation]
✅ Solution: [Fix summary]  
🧪 Tests: [Test coverage added]
```

### Detailed Report (--verbose)
- Complete analysis timeline
- Decision rationale for each step
- Alternative approaches considered
- Performance impact measurements
- Future prevention recommendations

### Code-Only Output (--code-only)
- Only the fixed code
- Minimal explanatory comments
- Ready for immediate commit

## Integration Hooks

### Pre-Workflow
```bash
# Automatic backup creation
git stash push -m "Pre-bugfix backup: $(date)"

# Environment validation
npm test || python -m pytest --tb=short
```

### Post-Workflow  
```bash
# Automatic testing
npm test && npm run type-check
python -m pytest && python -m mypy .

# Git integration
git add . && git commit -m "fix: [generated commit message]"
```

## Configuration

### Severity Thresholds
```yaml
severity_config:
  critical: 
    max_time: 30min
    required_agents: all
    auto_escalate: true
  high:
    max_time: 20min  
    required_agents: [analyst, detective, architect, implementer, validator]
  medium:
    max_time: 15min
    required_agents: [analyst, detective, implementer]
  low:
    max_time: 10min
    required_agents: [detective, implementer]
```

### Framework Preferences
```yaml
python_tools: [pytest, mypy, black, flake8]
react_tools: [jest, typescript, eslint, prettier]
debugging_tools: [pdb, chrome_devtools, react_devtools]
```

## Tips for Effective Usage

1. **Be Specific**: Include error messages, file names, or component names in your description
2. **Set Appropriate Severity**: Use `--severity=critical` only for production-breaking issues  
3. **Scope Correctly**: `--scope=local` for single-function bugs, `--scope=global` for architectural issues
4. **Combine with Git**: Run on clean working directory for best results
5. **Iterative Usage**: For complex bugs, use multiple focused calls rather than one broad call

## Common Scenarios

### React Component Bug
```bash
/bugfix-workflow "useState hook not updating component" --type=ui --scope=file
```

### Python API Error  
```bash
/bugfix-workflow "500 error on POST /api/users" --severity=high --type=runtime --scope=module
```

### Performance Issue
```bash
/bugfix-workflow "App becomes slow after 10 minutes of use" --type=performance --scope=global
```

### Type Error
```bash  
/bugfix-workflow "TypeScript compilation fails on user interface" --type=syntax --scope=module
```

This workflow command provides a systematic approach to debugging that scales from quick fixes to complex issue resolution, ensuring consistent quality and thorough documentation of all bug fixes.

## Workflow Implementation

The `/bugfix-workflow` command executes the following automated sequence, calling each specialized agent in order:

### Step 1: Issue Analysis (2-5 minutes)
Execute the **bug-analyst** agent to classify and prioritize the issue:

```
Please analyze this bug report using systematic issue classification:

**Bug Description**: {description}
**Reported Severity**: {severity}
**Reported Scope**: {scope}
**Reported Type**: {type}

Provide:
1. Validated classification (severity, scope, type)
2. Affected components identification
3. Initial root cause hypothesis
4. Investigation priority recommendations
5. Estimated fix complexity

Focus on Python and React applications. Output in structured format for handoff to error-detective.
```

### Step 2: Error Investigation (3-8 minutes)
Execute the **error-detective** agent for deep technical analysis:

```
Based on the bug-analyst classification, perform deep error investigation:

**Issue Classification**: {classification_results}
**Priority Investigation Areas**: {investigation_priorities}

Analyze:
1. Stack traces and error logs
2. Timeline reconstruction
3. Dependency chain investigation
4. Error propagation patterns
5. Root cause identification with evidence

For Python: Focus on exceptions, memory issues, async/await problems
For React: Focus on component lifecycle, state management, rendering issues

Provide technical root cause analysis for code-diagnostician review.
```

### Step 3: Code Diagnosis (5-10 minutes)
Execute the **code-diagnostician** agent for structural analysis:

```
Perform comprehensive code quality analysis based on error investigation:

**Root Cause**: {root_cause}
**Affected Components**: {affected_components}

Examine:
1. Code quality issues contributing to the bug
2. Anti-patterns and code smells
3. Architecture violations
4. Performance implications
5. Security vulnerabilities

For Python: Check for resource leaks, exception handling, type issues
For React: Check for rendering patterns, state mutations, memory leaks

Provide structural improvement requirements for fix-architect.
```

### Step 4: Solution Design (3-7 minutes)
Execute the **fix-architect** agent for optimal solution design:

```
Design comprehensive fix strategy based on diagnostic analysis:

**Root Cause**: {root_cause}
**Structural Issues**: {structural_issues}
**Severity**: {severity}
**Scope**: {scope}

Create:
1. Multiple solution approaches (quick, comprehensive, preventive)
2. Risk assessment for each approach
3. Implementation complexity analysis
4. Performance and security impact
5. Backwards compatibility considerations

Recommend optimal solution with detailed implementation plan for bugfix-implementer.
```

### Step 5: Implementation (5-15 minutes)
Execute the **bugfix-implementer** agent for code implementation:

```
Implement the recommended solution with high code quality:

**Solution Architecture**: {solution_design}
**Implementation Plan**: {implementation_plan}
**Code Quality Requirements**: Python/React best practices

Implement:
1. Core bug fix logic with proper error handling
2. Type safety and input validation
3. Performance optimizations
4. Comprehensive logging and debugging
5. Code documentation and comments

For Python: Use proper exception handling, type hints, resource management
For React: Use proper state management, memoization, accessibility

Provide implemented code for fix-validator testing.
```

### Step 6: Testing & Validation (3-10 minutes)
Execute the **fix-validator** agent for comprehensive testing:

```
Perform comprehensive validation of the implemented fix:

**Implemented Solution**: {implemented_code}
**Original Issue**: {original_issue}
**Test Requirements**: {test_requirements}

Validate:
1. Original issue resolution
2. No regression in existing functionality  
3. Performance impact assessment
4. Security vulnerability check
5. Edge case and error handling

For Python: Unit tests, integration tests, performance tests
For React: Component tests, user interaction tests, accessibility tests

Provide validation report with deployment readiness assessment.
```

### Step 7: Documentation (2-5 minutes)
Execute the **bug-documenter** agent for knowledge management:

```
Create comprehensive documentation for the bug fix:

**Bug Fix Summary**: {fix_summary}
**Validation Results**: {validation_results}
**Root Cause**: {root_cause}
**Solution Implemented**: {solution}

Document:
1. Complete incident report with timeline
2. Root cause analysis and prevention measures
3. Code changes and architecture decisions
4. Testing strategy and results
5. Knowledge base articles for similar issues

Create searchable documentation to prevent similar future issues.
```

## Workflow Execution Logic

When `/bugfix-workflow` is executed, the system should:

1. **Parse Parameters**: Extract description, severity, scope, and type from user input
2. **Initialize Context**: Create shared context object for agent communication
3. **Execute Sequential Steps**: Call each agent in order, passing results to next agent
4. **Handle Quality Gates**: Ensure each step meets quality requirements before proceeding
5. **Generate Final Report**: Compile comprehensive bug fix report from all agents

## Agent Communication Protocol

Each agent receives:
- **Input Context**: Results from previous agents
- **Original Request**: User's bug description and parameters  
- **Shared State**: Accumulated findings and decisions
- **Quality Metrics**: Success criteria and thresholds

Each agent provides:
- **Structured Output**: Findings in standardized format
- **Next Step Recommendations**: Guidance for subsequent agents
- **Quality Indicators**: Confidence levels and completion status
- **Updated Context**: Enhanced shared state for workflow

## Error Handling

If any agent fails or produces low-confidence results:
1. **Retry Logic**: Attempt agent execution up to 2 times
2. **Fallback Strategy**: Use generalist approach if specialist fails  
3. **Quality Validation**: Ensure minimum quality thresholds are met
4. **User Notification**: Inform user of any workflow issues or limitations

## Specialized Agent Invocation

For Python-specific issues, also invoke:
- **python-debugger**: For runtime analysis and memory profiling
- **performance-profiler**: For performance bottleneck identification

For React-specific issues, also invoke:
- **react-debugger**: For component lifecycle and state analysis  
- **typescript-analyzer**: For type system and compilation issues
- **performance-profiler**: For rendering and bundle optimization

## Example Execution Flow

```
User Input: /bugfix-workflow "React component causing memory leak" --severity=high --type=performance

Step 1: bug-analyst → Classifies as high-severity React performance issue
Step 2: error-detective → Investigates component lifecycle and memory patterns  
Step 3: code-diagnostician → Identifies useEffect cleanup issues and prop mutations
Step 4: fix-architect → Designs solution with proper cleanup and memoization
Step 5: bugfix-implementer → Implements useCallback, cleanup functions, React.memo
Step 6: fix-validator → Tests memory usage, re-render frequency, functionality
Step 7: bug-documenter → Documents React memory management best practices

Additional: react-debugger → Analyzes component re-render patterns
Additional: performance-profiler → Validates memory leak resolution
```

This systematic workflow ensures that every bug fix follows a thorough, documented process that leverages specialized expertise while maintaining consistency and quality.
