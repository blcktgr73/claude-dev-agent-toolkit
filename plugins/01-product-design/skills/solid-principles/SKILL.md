---
name: solid-principles
description: SOLID principles (Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion) for object-oriented design. Use when designing class structures, refactoring code, or evaluating architectural decisions.
---

# SOLID Principles

## When to Use This Skill
- Designing new class hierarchies or system architecture
- Refactoring existing code to improve maintainability
- Code reviews focusing on design quality
- Breaking down monolithic classes
- Evaluating whether code follows best practices

## Core Principles

### 1. Single Responsibility Principle (SRP)
A class should have only one reason to change.

**Apply when:** Class has multiple responsibilities, becomes too large (>200 lines), or changes for unrelated reasons.

### 2. Open/Closed Principle (OCP)
Software entities should be open for extension but closed for modification.

**Apply when:** Adding new features requires modifying existing code, or you have switch/if-else chains based on type.

### 3. Liskov Substitution Principle (LSP)
Objects of a superclass should be replaceable with objects of subclasses without breaking functionality.

**Apply when:** Designing inheritance hierarchies or finding runtime type checks.

### 4. Interface Segregation Principle (ISP)
No client should be forced to depend on methods it doesn't use.

**Apply when:** Interfaces have many methods, or implementations throw "not supported" exceptions.

### 5. Dependency Inversion Principle (DIP)
Depend on abstractions, not concretions.

**Apply when:** Unit testing is difficult, or you need to swap implementations (e.g., databases, external services).

## Quick Decision Guide

**Problem: Class is too large**
→ Apply SRP: Break into focused classes

**Problem: Adding features breaks existing code**
→ Apply OCP: Use abstractions/interfaces

**Problem: Subclass can't properly replace parent**
→ Apply LSP: Fix inheritance hierarchy

**Problem: Implementing unused interface methods**
→ Apply ISP: Split into smaller interfaces

**Problem: Hard to test or swap dependencies**
→ Apply DIP: Inject dependencies, use interfaces
