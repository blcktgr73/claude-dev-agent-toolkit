---
description: UI/UX design implementation workflow with specialized agents
argument-hint: [design request]
---

# Design Workflow Command

**Command:** `/design-workflow`

**Purpose:** Orchestrates a complete UI/UX design implementation workflow from design request to verified design solution using specialized agents.

## Workflow Overview

```
graph LR
    A[UI/UX design request] -- Design UI/UX solution for the request  --> B[UX Agent]
    B --> D(Architect Agent);
    D --> E{Create Tech Design & Task Breakdown};
    E -- "Take one small task" --> F[Developer Agents];
    F --> G(Reviewer Agent);
    G -- "Rejects" --> F;
    G -- "Approves" --> H(QA Agent);
    H -- "Bugs Found" --> F;
    H -- "QA Passes" --> I[Done];
    I -- "Trigger developer for next task" --> F
    I -- "When all tasks are done, verify results" --> J[UX/UI Agent]
```

## Command Prompt

When the user types `/design-workflow [UI/UX design request description]`, execute the following orchestrated workflow:

### Phase 1: UI/UX Design Solution
Launch the **UX Design Specialist** agent with the task:
```
Create a comprehensive UI/UX design solution for: [UI/UX design request description]

Requirements:
- Analyze user needs and design requirements
- Create user experience flows and wireframes
- Design user interface components and layouts
- Establish visual design system and style guide
- Consider accessibility and usability principles
- Define interaction patterns and micro-interactions
- Specify responsive design requirements
- Create design specifications for development

Return a detailed design document including:
- User experience flows
- Wireframes and mockups
- Component specifications
- Design system guidelines
- Technical design requirements
- Accessibility considerations
```

### Phase 2: Technical Design & Task Breakdown
Launch the **Software Architect Designer** agent with the task:
```
Based on the UI/UX design solution: [design solution from Phase 1]

Create a comprehensive technical implementation plan that includes:
- Frontend architecture for the design implementation
- Component structure and data flow
- Integration with existing design system
- State management for UI interactions
- API requirements for dynamic content
- Performance considerations for UI components
- Responsive implementation strategy
- Break down into small, junior-developer-friendly tasks

Each task should be:
- Clearly defined and independent
- Completable in 1-2 hours
- Include specific UI/UX acceptance criteria
- Ordered by dependency requirements
- Focus on design implementation details

Return the technical design document and ordered task list for UI/UX implementation.
```

### Phase 3: Implementation Cycle
For each task from the architect's breakdown, execute this cycle:

#### 3a: Development
Launch the **Implementation Engineer** agent with the task:
```
Implement the following UI/UX task: [current task from breakdown]

Context:
- Design Request: [original UI/UX design request]
- UX Design Solution: [design solution from Phase 1]
- Technical Design: [tech design from Phase 2]
- Previous completed tasks: [list of completed tasks]

Requirements:
- Follow the UI/UX design specifications exactly
- Implement responsive and accessible components
- Ensure pixel-perfect design implementation
- Follow existing design system patterns
- Write clean, maintainable frontend code
- Include appropriate animations and interactions
- Ensure cross-browser compatibility
- Optimize for performance and user experience

Deliver working UI/UX implementation that fulfills the design requirements.
```

#### 3b: Code Review
Launch the **Code Quality Inspector** agent with the task:
```
Review the UI/UX implementation for task: [current task]

Code to review: [implemented code from 3a]
Design requirements: [relevant sections from UX design and tech design]

Check for:
- Code compiles successfully
- All tests pass (including visual regression tests)
- Design implementation matches specifications
- Accessibility standards compliance (WCAG)
- Responsive design works across devices
- Performance optimization for UI components
- Code quality and frontend best practices
- Integration with existing design system

If issues found: Return specific design implementation feedback for developer
If approved: Confirm code meets all design and technical standards
```

**If reviewer rejects**: Return to Phase 3a with detailed design feedback
**If reviewer approves**: Continue to Phase 3c

#### 3c: Quality Assurance Testing
Launch the **QA Test Engineer** agent with the task:
```
Test the UI/UX implementation for task: [current task]

Implementation: [approved code from 3b]
Design Requirements: [UX design solution requirements]
Technical Specifications: [relevant specs from tech design]

Test for:
- Visual design matches mockups and specifications
- User interactions work as designed
- Responsive behavior across devices and screen sizes
- Accessibility features function correctly
- Performance meets user experience standards
- Cross-browser compatibility
- Integration with existing UI components

If design/UX issues found: Document problems and return to developer
If QA passes: Confirm implementation meets all design requirements
```

**If QA finds issues**: Return to Phase 3a with QA feedback
**If QA passes**: Mark task as complete and move to next task

### Phase 4: Task Completion Loop
After each task completion:
- Mark current UI/UX task as done
- Check if more tasks remain from architect's breakdown
- If more tasks exist: Trigger Phase 3 for next task
- If all tasks complete: Continue to Phase 5

### Phase 5: Final Design Verification
When all implementation tasks are complete, launch the **UX Design Specialist** agent with the task:
```
Verify the complete UI/UX implementation meets the original design requirements.

Original Request: [UI/UX design request]
Design Solution: [original design solution from Phase 1]
Completed Implementation: [all implemented features and components]

Verification checklist:
- Visual design matches original specifications
- User experience flows work as designed
- Accessibility requirements are met
- Responsive design functions correctly
- Design system consistency is maintained
- User interactions feel intuitive and smooth
- Overall design goals are achieved

If issues found: Document specific design problems for developer resolution
If verification passes: Confirm design workflow is complete and successful
```

**If verification finds issues**: Return to Phase 3 with design feedback
**If verification passes**: Design workflow complete

## Usage Examples

### Dashboard Redesign Request
```
/design-workflow Redesign the analytics dashboard with improved data visualization and better mobile responsiveness
```

### New Feature UI Request
```
/design-workflow Design user onboarding flow with progressive disclosure and interactive tutorials
```

### Accessibility Enhancement Request
```
/design-workflow Improve accessibility for visually impaired users in the checkout process with screen reader optimization
```

### Component Library Request
```
/design-workflow Create a consistent design system with reusable components for forms, buttons, and navigation elements
```

## Workflow Execution

This will:
1. Create comprehensive UI/UX design solution with mockups and specifications
2. Generate technical implementation plan breaking it into tasks like:
   - Create responsive layout components
   - Implement interactive elements
   - Add accessibility features
   - Integrate with design system
   - Optimize for performance
3. Implement each task through dev → review → QA cycle
4. Verify final implementation meets original design vision

## Success Criteria
- UX design solution addresses user needs and requirements
- Technical design provides comprehensive implementation plan
- All UI/UX tasks are completed and pass code review
- All implementations pass QA testing
- Final design verification confirms requirements are met
- User experience is intuitive and accessible
- Design system consistency is maintained
- Implementation is production-ready and performant