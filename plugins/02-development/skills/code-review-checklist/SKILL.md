---
name: code-review-checklist
description: Systematic code review checklist covering functionality, design, quality, security, performance, and testing. Use when reviewing pull requests or conducting code reviews.
---

# Code Review Checklist

## When to Use This Skill
- Reviewing pull requests
- Conducting peer code reviews
- Self-reviewing before committing
- Establishing review standards

## Priority Levels

**[Critical]** - Must fix (security, correctness bugs)
**[Important]** - Should fix (performance, maintainability)
**[Nit]** - Nice to have (style, minor improvements)
**[Question]** - Seeking clarification
**[Praise]** - Positive feedback

## Quick Review Categories

### 1. Functionality (Critical)
- [ ] Code works as intended
- [ ] Business logic correct
- [ ] Edge cases handled
- [ ] Error scenarios covered
- [ ] Input validation present

### 2. Design & Architecture (Important)
- [ ] SOLID principles followed
- [ ] Appropriate patterns used
- [ ] Separation of concerns
- [ ] No anti-patterns
- [ ] Consistent with codebase

### 3. Code Quality (Important)
- [ ] Readable and self-documenting
- [ ] Functions < 50 lines
- [ ] Classes < 300 lines
- [ ] Low complexity (<10 cyclomatic)
- [ ] No code duplication (DRY)
- [ ] Meaningful names

### 4. Security (Critical)
- [ ] Input validation
- [ ] No SQL injection risk
- [ ] No XSS vulnerabilities
- [ ] Authentication/authorization
- [ ] Secrets not in code
- [ ] Sensitive data encrypted

### 5. Performance (Important)
- [ ] Efficient algorithms
- [ ] No N+1 queries
- [ ] Proper indexing
- [ ] Resource cleanup
- [ ] Caching where appropriate

### 6. Testing (Critical)
- [ ] Tests present
- [ ] Tests pass
- [ ] Coverage adequate (>80%)
- [ ] Edge cases tested
- [ ] Error paths tested

### 7. Documentation (Nit)
- [ ] Complex logic explained
- [ ] Public APIs documented
- [ ] TODOs have owners
- [ ] No outdated comments

## Feedback Best Practices

### Be Specific
✅ "Consider extracting this 50-line function into smaller, focused functions"
❌ "This is too complex"

### Use Questions
✅ "Have you considered what happens if the API times out?"
❌ "This will fail on timeout"

### Praise Good Work
✅ "Nice use of the Strategy pattern here!"

## Common Code Smells
- God Class (too many responsibilities)
- Long Method (>50 lines)
- Long Parameter List (>4 parameters)
- Duplicate Code
- Magic Numbers
- Dead Code
- Feature Envy

## Review Time Guidelines
- Small (<200 lines): 15-30 min
- Medium (200-400 lines): 30-60 min
- Large (400+ lines): Split into smaller reviews

## Quick Decision Guide

**Security issue?** → [Critical] Must fix immediately
**Breaks SOLID principles?** → [Important] Should fix
**Naming unclear?** → [Nit] or [Question]
**Good implementation?** → [Praise]
