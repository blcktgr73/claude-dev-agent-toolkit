# Development Toolkit Plugin

## Overview
Development best practices plugin providing comprehensive guidance on testing strategies, code review processes, and API design principles.

## Features

### Specialized Agents
- **implementation-engineer**: Feature implementation following SOLID principles and design patterns
- **code-quality-inspector**: Comprehensive code review and quality assessment
- **qa-test-engineer**: Testing, quality assurance, and test automation

### Skills (Knowledge Base)
- **testing-best-practices**: Unit, integration, E2E testing with testing pyramid principles
- **code-review-checklist**: Systematic code review covering all quality aspects
- **api-design-principles**: RESTful API design, HTTP methods, status codes, versioning

## Usage Examples

### Code Implementation
Use the `implementation-engineer` agent for:
- Implementing new features with clean code
- Refactoring existing code
- Applying design patterns
- Following SOLID principles

### Code Review
Use the `code-quality-inspector` agent to:
- Review pull requests systematically
- Check code quality and standards
- Verify test coverage
- Ensure security best practices

### Quality Assurance
Use the `qa-test-engineer` agent for:
- Writing comprehensive tests
- Verifying functionality
- Performance testing
- User experience validation

## Skills Integration

Skills provide knowledge that agents can reference:

- **Testing Best Practices**: AAA pattern, test pyramid, fixtures, mocking
- **Code Review Checklist**: Functionality, security, performance, testing checks
- **API Design Principles**: RESTful conventions, status codes, versioning strategies

## Best Practices Quick Reference

### Testing Pyramid
```
     /E2E\      10% - Few, slow, expensive
    /-----\
   /  API  \    20% - Medium speed
  /---------\
 /   Unit    \  70% - Many, fast
/-------------\
```

### Code Review Priority
- **[Critical]**: Security, correctness bugs
- **[Important]**: Performance, maintainability
- **[Nit]**: Style, minor improvements

### API Design
- Use nouns for resources
- Plural names for collections
- Appropriate HTTP methods
- Meaningful status codes
- Version from day one

## Installation

Copy the `02-development` folder to `.claude/plugins/` and restart Claude Code.

## Related Plugins

- **01-product-design**: Product strategy and architecture
- **03-debugging**: Bug fixing and diagnostics
