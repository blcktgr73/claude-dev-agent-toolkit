---
description: Technical implementation workflow from requirements to code
argument-hint: [technical request]
---

# Tech Request Workflow Command

**Command:** `/tech-request`

**Purpose:** Orchestrates a technical implementation workflow for technical requests that go directly from technical requirements to implementation using specialized agents.

## Workflow Overview

```
graph LR
    C[Technical request] --> D(Architect Agent);
    D --> E{Create Tech Design & Task Breakdown};
    E -- "Take one small task" --> F[Developer Agents];
    F --> G(Reviewer Agent);
    G -- "Rejects" --> F;
    G -- "Approves" --> H(QA Agent);
    H -- "Bugs Found" --> F;
    H -- "QA Passes" --> I[Done];
    I -- "Trigger developer for next task" --> F
```

## Command Prompt

When the user types `/tech-request [technical request description]`, execute the following orchestrated workflow:

### Phase 1: Technical Design & Task Breakdown
Launch the **Software Architect Designer** agent with the task:
```
Analyze and create a comprehensive technical design for: [technical request description]

Requirements:
- Understand the technical requirements and constraints
- Design system architecture considering the bigger picture
- Identify integration points with existing system
- Consider performance, security, and scalability implications
- Break down the implementation into small, junior-developer-friendly tasks

Each task should be:
- Clearly defined and independent
- Completable in 1-2 hours
- Include specific acceptance criteria
- Ordered by dependency requirements
- Focus on technical implementation details

Return the technical design document and ordered task list.
```

### Phase 2: Implementation Cycle
For each task from the architect's breakdown, execute this cycle:

#### 2a: Development
Launch the **Implementation Engineer** agent with the task:
```
Implement the following technical task: [current task from breakdown]

Context:
- Technical Request: [original technical request]
- Technical Design: [tech design from Phase 1]
- Previous completed tasks: [list of completed tasks]

Requirements:
- Follow the technical design specifications exactly
- Write clean, efficient, and maintainable code
- Include appropriate error handling and logging
- Follow existing codebase patterns and conventions
- Ensure code is production-ready and optimized
- Include necessary documentation for technical implementation

Deliver working code that fulfills the technical task requirements.
```

#### 2b: Code Review
Launch the **Code Quality Inspector** agent with the task:
```
Review the technical implementation for task: [current task]

Code to review: [implemented code from 2a]
Technical requirements: [relevant sections from tech design]

Check for:
- Code compiles successfully
- All tests pass (run existing test suite)
- Technical implementation follows design specifications
- Code quality, performance, and security best practices
- Proper error handling and edge case coverage
- Integration compatibility with existing system
- Documentation adequacy for technical changes

If issues found: Return specific technical feedback for developer to address
If approved: Confirm code meets all technical standards and requirements
```

**If reviewer rejects**: Return to Phase 2a with detailed technical feedback
**If reviewer approves**: Continue to Phase 2c

#### 2c: Technical Quality Assurance
Launch the **QA Test Engineer** agent with the task:
```
Test the technical implementation for task: [current task]

Implementation: [approved code from 2b]
Technical Requirements: [original technical request]
Technical Specifications: [relevant specs from tech design]

Test for:
- Technical functionality works as specified
- Performance meets requirements
- Integration with existing system components
- Error handling and edge case scenarios
- System stability and reliability
- Technical acceptance criteria are met

If technical issues found: Document specific problems and return to developer
If technical QA passes: Confirm implementation meets all technical requirements
```

**If QA finds issues**: Return to Phase 2a with QA technical feedback
**If QA passes**: Mark task as complete and move to next task

### Phase 3: Task Completion Loop
After each task completion:
- Mark current technical task as done
- Check if more tasks remain from architect's breakdown
- If more tasks exist: Trigger Phase 2 for next task
- If all tasks complete: Technical request workflow complete

## Usage Examples

### Database Optimization Request
```
/tech-request Optimize database queries for user analytics dashboard to reduce load time from 5s to under 1s
```

### API Enhancement Request
```
/tech-request Add rate limiting and caching layer to user authentication API to handle 10x current traffic
```

### Infrastructure Request
```
/tech-request Implement automated backup system for production database with point-in-time recovery capability
```

### Security Enhancement Request
```
/tech-request Add OAuth2 integration with multi-factor authentication support for admin panel access
```

## Workflow Execution

This will:
1. Generate technical design and implementation plan for the request
2. Break down into specific technical tasks like:
   - Database schema optimizations
   - Query refactoring and indexing
   - Caching layer implementation
   - Performance monitoring setup
   - Load testing configuration
3. Implement each task through dev → review → QA cycle
4. Complete when all technical tasks are done and tested

## Success Criteria
- Technical design provides comprehensive implementation plan
- All technical tasks are completed and pass code review
- All implementations pass technical QA testing
- System integration is verified and stable
- Performance and technical requirements are met
- Code is production-ready and maintainable
- Technical documentation is complete and accurate