---
description: Complete feature development workflow from idea to production
argument-hint: [feature description]
---

# Feature Workflow Command

**Command:** `/feature-workflow`

**Purpose:** Orchestrates a complete feature development workflow from user idea to production-ready implementation using specialized agents.

## Workflow Overview

```
graph LR
    A[User Idea] --> B(Product Manager Agent);
    B --> C{Create Spec};
    C --> D(Architect Agent);
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

When the user types `/feature-workflow [feature description]`, execute the following orchestrated workflow:

### Phase 1: Product Specification
Launch the **Agile Product Strategist** agent with the task:
```
Create a comprehensive product specification for: [feature description]

Requirements:
- Define user stories and acceptance criteria
- Identify business value and success metrics  
- Specify functional and non-functional requirements
- Consider edge cases and error scenarios
- Provide clear scope and boundaries

Return a detailed product specification document that can be used by technical teams for implementation planning.
```

### Phase 2: Technical Design & Task Breakdown
Launch the **Software Architect Designer** agent with the task:
```
Based on the product specification: [product spec from Phase 1]

Create a comprehensive technical design that includes:
- System architecture overview considering the bigger picture
- Database schema changes (if needed)
- API endpoints and data flow
- Integration points with existing system
- Security and performance considerations
- Break down the implementation into small, junior-developer-friendly tasks

Each task should be:
- Clearly defined and independent
- Completable in 1-2 hours
- Include specific acceptance criteria
- Ordered by dependency requirements

Return the technical design document and ordered task list.
```

### Phase 3: Implementation Cycle
For each task from the architect's breakdown, execute this cycle:

#### 3a: Development
Launch the **Implementation Engineer** agent with the task:
```
Implement the following task: [current task from breakdown]

Context:
- Product Spec: [product spec]
- Technical Design: [tech design]
- Previous completed tasks: [list of completed tasks]

Requirements:
- Follow the technical design specifications
- Write clean, maintainable code
- Include appropriate error handling
- Follow existing codebase patterns and conventions
- Ensure code is production-ready

Deliver working code that fulfills the task requirements.
```

#### 3b: Code Review
Launch the **Code Quality Inspector** agent with the task:
```
Review the implementation for task: [current task]

Code to review: [implemented code from 3a]
Technical requirements: [relevant sections from tech design]

Check for:
- Code compiles successfully
- All tests pass (run existing test suite)
- Code quality and best practices
- Security considerations
- Performance implications
- Adherence to technical design
- Integration with existing codebase

If issues found: Return specific feedback for developer to address
If approved: Confirm code meets all standards and requirements
```

**If reviewer rejects**: Return to Phase 3a with reviewer feedback
**If reviewer approves**: Continue to Phase 3c

#### 3c: Quality Assurance
Launch the **QA Test Engineer** agent with the task:
```
Test the implemented feature for task: [current task]

Implementation: [approved code from 3b]
Product Requirements: [relevant requirements from product spec]
Technical Specifications: [relevant specs from tech design]

Test for:
- Functional requirements are met
- Feature works as specified in product spec
- Integration with existing system
- Error handling and edge cases
- User experience flows
- Performance under normal conditions

If bugs found: Document issues and return to developer
If QA passes: Confirm feature meets all product requirements
```

**If QA finds issues**: Return to Phase 3a with QA feedback
**If QA passes**: Mark task as complete and move to next task

### Phase 4: Task Completion Loop
After each task completion:
- Mark current task as done
- Check if more tasks remain from architect's breakdown
- If more tasks exist: Trigger Phase 3 for next task
- If all tasks complete: Feature workflow complete

## Usage Example
```
/feature-workflow Add user profile image upload functionality with thumbnail generation
```

This will:
1. Generate product spec for image upload feature
2. Create technical design breaking it into small tasks like:
   - Create file upload endpoint
   - Implement image validation
   - Add thumbnail generation service
   - Update user profile UI
   - Write tests for upload flow
3. Implement each task through dev → review → QA cycle
4. Complete when all tasks are done and tested

## Success Criteria
- Product spec clearly defines requirements
- Technical design provides comprehensive implementation plan
- All tasks are completed and pass code review
- All features pass QA testing
- Integration with existing system is verified
- Code is production-ready and maintainable