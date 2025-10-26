---
name: gang-of-four-patterns
description: Classic design patterns from the Gang of Four book. Includes Creational (Singleton, Factory, Builder), Structural (Adapter, Decorator, Facade), and Behavioral (Strategy, Observer, Command) patterns. Use when solving common design problems.
---

# Gang of Four Design Patterns

## When to Use This Skill
- Solving recurring design problems
- Improving code flexibility and maintainability
- Communicating design intent clearly
- Refactoring to well-known patterns

## Pattern Categories

### Creational Patterns (Object Creation)
- **Singleton**: Ensure only one instance exists
- **Factory Method**: Let subclasses decide which class to instantiate
- **Abstract Factory**: Create families of related objects
- **Builder**: Construct complex objects step by step
- **Prototype**: Clone existing objects

### Structural Patterns (Object Composition)
- **Adapter**: Convert interface to expected format
- **Bridge**: Separate abstraction from implementation
- **Composite**: Treat individual objects and compositions uniformly
- **Decorator**: Add responsibilities dynamically
- **Facade**: Provide simple interface to complex subsystem
- **Proxy**: Control access to objects

### Behavioral Patterns (Object Interaction)
- **Strategy**: Encapsulate interchangeable algorithms
- **Observer**: Notify dependents of state changes
- **Command**: Encapsulate requests as objects
- **Template Method**: Define algorithm skeleton, let subclasses fill in steps
- **State**: Change behavior based on internal state
- **Chain of Responsibility**: Pass requests along handler chain

## Quick Selection Guide

**Need only one instance?** → Singleton
**Creating objects based on type?** → Factory Method
**Complex object construction?** → Builder
**Incompatible interfaces?** → Adapter
**Add features without subclassing?** → Decorator
**Simplify complex system?** → Facade
**Interchangeable algorithms?** → Strategy
**Notify multiple objects?** → Observer
**Undo/redo functionality?** → Command
**Behavior depends on state?** → State
