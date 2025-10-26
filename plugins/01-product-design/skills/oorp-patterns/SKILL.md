---
name: oorp-patterns
description: Object-Oriented Reengineering Patterns for understanding, maintaining, and evolving legacy systems. Use when working with existing codebases, refactoring, or migrating legacy code.
---

# Object-Oriented Reengineering Patterns (OORP)

## When to Use This Skill
- Understanding unfamiliar legacy codebases
- Planning refactoring efforts
- Migrating or modernizing old systems
- Documenting existing systems
- Identifying technical debt

## Pattern Workflow Phases

### Phase 1: First Contact (Understanding)
- **Interview During Demo**: Learn from stakeholders
- **Read All Code in One Hour**: Get high-level overview
- **Skim the Documentation**: Assess doc quality
- **Chat with Maintainers**: Extract tacit knowledge

### Phase 2: Initial Understanding (Analysis)
- **Analyze Persistent Data**: Understand data model from database schema
- **Detect Duplicated Code**: Find copy-paste patterns
- **Analyze Flow of Data**: Track data transformations

### Phase 3: Setting Direction (Planning)
- **Most Valuable First**: Prioritize high-value, high-pain areas
- **Tie Code and Questions**: Organize investigation systematically
- **Keep It Simple**: Avoid over-engineering

### Phase 4: Tests (Safety Net)
- **Grow Test Base Incrementally**: Add tests gradually
- **Write Tests to Enable Refactoring**: Characterization tests
- **Regression Test After Every Change**: Prevent breaking changes

### Phase 5: Migration (Evolution)
- **Always Have Running Version**: Use feature flags, parallel implementations
- **Deprecate Obsolete Interfaces**: Phase out old code gradually
- **Involve the Users**: Beta testing, feedback loops

### Phase 6: Transformations (Improvement)
- **Refactor to Understand**: Clarify while reading
- **Move Behavior Close to Data**: Improve cohesion
- **Split Up God Class**: Break large classes
- **Replace Conditional with Polymorphism**: Eliminate type switches

## Quick Decision Guide

**New to codebase?** → Phase 1: First Contact patterns
**Need to understand structure?** → Phase 2: Analysis patterns
**Planning refactoring?** → Phase 3: Direction + Phase 4: Tests
**Making changes?** → Phase 4: Tests + Phase 5: Migration
**Improving design?** → Phase 6: Transformation patterns
