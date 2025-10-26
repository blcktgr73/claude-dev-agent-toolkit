---
name: testing-best-practices
description: Comprehensive testing practices covering unit, integration, and E2E testing with test pyramid principles, AAA pattern, test organization, and CI/CD integration. Use when writing tests or reviewing test quality.
---

# Testing Best Practices

## When to Use This Skill
- Writing new tests for features
- Reviewing test code quality
- Organizing test suites
- Setting up CI/CD testing pipelines
- Improving test coverage meaningfully

## Testing Pyramid

```
     /E2E\      10% - Few, slow, expensive
    /-----\
   /  API  \    20% - Medium speed & quantity
  /---------\
 /   Unit    \  70% - Many, fast, cheap
/-------------\
```

## Core Testing Patterns

### AAA Pattern (Arrange, Act, Assert)
Structure every test clearly:
1. **Arrange**: Set up test data and dependencies
2. **Act**: Execute the behavior being tested
3. **Assert**: Verify the outcome

### Test Independence
- Tests run in any order
- No shared state between tests
- Each test sets up own data

### Descriptive Names
`test_[method]_[scenario]_[expected_result]()`

Example: `test_user_login_with_invalid_password_returns_error()`

## Test Types Quick Guide

**Unit Tests (70%)**
- Test single functions/methods
- Mock external dependencies
- Fast execution (<1ms each)
- High coverage of business logic

**Integration Tests (20%)**
- Test component interactions
- Use test databases
- Medium speed (10-100ms each)
- Verify integrations work

**E2E Tests (10%)**
- Test complete user flows
- Simulate real usage
- Slow (seconds-minutes)
- Verify critical paths

## Common Patterns

### Test Fixtures
Use for shared setup, but avoid over-sharing

### Edge Cases
Test boundaries, null values, empty collections, max limits

### Error Scenarios
Test exception handling, validation failures, timeouts

## Anti-Patterns to Avoid
- ❌ Ice Cream Cone (too many E2E tests)
- ❌ Testing implementation details
- ❌ Fragile tests (break on refactoring)
- ❌ Slow test suites
- ❌ Flaky tests
- ❌ Mystery Guest (hidden dependencies)

## Quick Checklist
- [ ] Tests pass locally
- [ ] AAA pattern followed
- [ ] Descriptive test names
- [ ] Tests are independent
- [ ] Edge cases covered
- [ ] Mocks used appropriately
- [ ] Fast execution
