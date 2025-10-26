# Product Design Toolkit Plugin

## Overview
Comprehensive toolkit for product strategy, UX design, and software architecture with deep knowledge of SOLID principles, Gang of Four design patterns, and Object-Oriented Reengineering Patterns (OORP).

## Features

### Specialized Agents
- **agile-product-strategist**: Product planning, user stories, sprint planning, MVP definition
- **software-architect-designer**: Technical architecture, SOLID principles, task decomposition
- **ux-design-specialist**: UI/UX design, wireframes, accessibility, user flows

### Slash Commands
- `/design-workflow`: Complete UI/UX design implementation workflow
- `/feature-workflow`: Full feature development from idea to production
- `/tech-request`: Technical request handling workflow

### Skills (Knowledge Base)
- **solid-principles**: SOLID design principles for clean architecture
- **gang-of-four-patterns**: 23 classic design patterns (Creational, Structural, Behavioral)
- **oorp-patterns**: Reengineering patterns for legacy system improvement

## Usage Examples

### Feature Development
```
/feature-workflow Add user authentication with OAuth2 and JWT tokens
```

This orchestrates:
1. Product strategist creates specification
2. Architect designs technical solution
3. Implementation engineer builds features
4. Code reviewer ensures quality
5. QA engineer validates functionality

### UI/UX Design
```
/design-workflow Redesign dashboard with improved data visualization
```

### Architecture Design
Use the `software-architect-designer` agent for:
- Breaking down complex requirements
- Designing system architecture
- Applying SOLID principles
- Creating implementation task lists

## Skills Integration

Skills are automatically available to agents in this plugin:

- Agents can reference **SOLID principles** when designing architecture
- Use **Gang of Four patterns** to solve common design problems
- Apply **OORP patterns** when working with legacy code

## Installation

This plugin is part of the Claude Code Agents Workflow collection. Install by:

1. Copying the entire `01-product-design` folder to `.claude/plugins/`
2. Restarting Claude Code
3. Commands and agents will be available immediately

## Related Plugins

- **02-development**: Implementation and testing practices
- **03-debugging**: Systematic debugging workflows
