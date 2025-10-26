# Language Tools Plugin

## Overview
Language-specific debugging and optimization tools for Python, React, TypeScript, and performance profiling.

## Features

### Specialized Agents
- **python-debugger**: Python-specific debugging patterns, tools, and optimization
- **react-debugger**: React component lifecycle and state debugging
- **typescript-analyzer**: TypeScript type safety and error analysis
- **performance-profiler**: Performance bottleneck identification and optimization

## Agent Capabilities

### Python Debugger
- Python-specific debugging patterns
- Common Python pitfalls
- Performance optimization
- Memory management
- Async/await debugging
- Type hint analysis with mypy

### React Debugger
- Component lifecycle issues
- State management debugging
- Hook dependencies and effects
- Re-render optimization
- Context and prop drilling
- React DevTools usage

### TypeScript Analyzer
- Type error diagnosis
- Type inference issues
- Generic type problems
- Interface vs. type decisions
- Strict mode compliance
- tsconfig optimization

### Performance Profiler
- Performance bottleneck identification
- Database query optimization
- Memory leak detection
- CPU profiling
- Network request optimization
- Caching strategies

## Usage

These agents are automatically available and work in conjunction with the debugging workflow:

### Python Projects
When debugging Python code, the **python-debugger** agent provides:
- Stack trace analysis
- Common Python error patterns
- Performance profiling with cProfile
- Memory profiling with memory_profiler
- Type checking with mypy

### React Applications
The **react-debugger** agent helps with:
- Component re-render analysis
- State update debugging
- useEffect dependency issues
- Performance optimization with React.memo
- Context performance problems

### TypeScript Codebases
The **typescript-analyzer** assists with:
- Type error resolution
- Complex type inference
- Generic constraints
- Type narrowing
- Utility type usage

### Performance Issues
The **performance-profiler** identifies:
- Slow database queries
- N+1 query problems
- Memory leaks
- CPU-intensive operations
- Network bottlenecks

## Integration with Debugging Workflow

These agents are automatically invoked by the `/bugfix-workflow` command based on file extensions:

- `.py` files → python-debugger
- `.jsx`, `.tsx` files → react-debugger
- `.ts`, `.tsx` files → typescript-analyzer
- Performance flags → performance-profiler

## Example Usage

```bash
# Python debugging
/bugfix-workflow Memory leak in data processing --type=runtime --scope=module

# React debugging
/bugfix-workflow Component re-renders too frequently --type=performance --scope=file

# TypeScript analysis
/bugfix-workflow Type error in generic function --type=syntax --scope=file
```

## Installation

Copy the `04-language-tools` folder to `.claude/plugins/` and restart Claude Code.

## Related Plugins

- **03-debugging**: Core debugging workflow
- **02-development**: General development practices
