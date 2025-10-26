# Claude Code Agents Workflow - Plugin Collection

A comprehensive collection of specialized Claude Code plugins for product development, software architecture, debugging, and content creation. This repository demonstrates advanced workflow orchestration using the Claude Code plugin system with specialized agents, commands, and knowledge skills.

**[한국어 문서](README_KR.md)**

## 🙏 Credits

This project is inspired by and based on the original work from [omersaraf/claude-code-agents-workflow](https://github.com/omersaraf/claude-code-agents-workflow). While this repository is structured as a plugin collection, the core ideas and workflow concepts are derived from the original project.

## 🎯 Overview

This repository provides a complete toolkit organized as modular plugins, each focused on specific aspects of software development:

- **Product Design & Architecture** - Strategic planning and system design
- **Development & Quality** - Implementation and code quality practices
- **Debugging & Diagnostics** - Systematic bug fixing workflows
- **Language-Specific Tools** - Python, React, TypeScript optimizations
- **Content Marketing** - Technical content and marketing materials

## 📦 Plugin Architecture

The repository is organized into 5 independent plugins that can be installed together or separately:

```
plugins/
├── 01-product-design/        # Product strategy, UX, architecture
├── 02-development/            # Implementation, testing, API design
├── 03-debugging/              # Systematic debugging workflows
├── 04-language-tools/         # Python, React, TypeScript tools
└── 05-content-marketing/      # Content creation and SEO
```

Each plugin follows the Claude Code plugin structure:
```
plugin-name/
├── .claude-plugin/
│   └── plugin.json           # Plugin metadata
├── agents/                   # Specialized agents
│   └── agent-name.md
├── commands/                 # Slash commands
│   └── command-name.md
├── skills/                   # Knowledge base
│   └── skill-name/
│       └── SKILL.md
└── README.md                 # Plugin documentation
```

## 🚀 Quick Start

### Installation from GitHub Marketplace

This is the recommended installation method, especially for Windows users.

#### Step 1: Add Marketplace
```bash
/plugin marketplace add https://github.com/blcktgr73/claude-dev-agent-toolkit
```

#### Step 2: Install Plugins
You can install all plugins or only the ones you need:

```bash
# Install all plugins (recommended)
/plugin install product-design-toolkit@claude-dev-agent-toolkit
/plugin install development-toolkit@claude-dev-agent-toolkit
/plugin install debugging-toolkit@claude-dev-agent-toolkit
/plugin install language-tools@claude-dev-agent-toolkit
/plugin install content-marketing-toolkit@claude-dev-agent-toolkit

# Or install only what you need
/plugin install product-design-toolkit@claude-dev-agent-toolkit
/plugin install debugging-toolkit@claude-dev-agent-toolkit
```

#### Step 3: Verify Installation
```bash
# Check installed plugins
/plugin list

# Available commands should now include:
# - /feature-workflow
# - /design-workflow
# - /tech-request
# - /bugfix-workflow
```

#### Step 4: Start Using
```bash
# Try a feature workflow
/feature-workflow Add user authentication with OAuth2

# Try a design workflow
/design-workflow Redesign analytics dashboard

# Try a debugging workflow
/bugfix-workflow Login button not responding --type=ui --scope=file
```

### Alternative: Manual Installation (Advanced Users)

If you prefer to install manually:

1. **Clone this repository**
   ```bash
   git clone https://github.com/blcktgr73/claude-dev-agent-toolkit.git
   cd claude-dev-agent-toolkit
   ```

2. **Copy plugins to Claude Code directory**
   ```bash
   # Windows (PowerShell)
   Copy-Item -Recurse -Force plugins\* ~\.claude\plugins\

   # macOS/Linux
   cp -r plugins/* ~/.claude/plugins/
   ```

3. **Restart Claude Code** to load the plugins

## 📚 Plugins Overview

### 1. Product Design Toolkit (`01-product-design`)

**Purpose:** Product strategy, UX design, and software architecture with design pattern knowledge

**Agents:**
- `agile-product-strategist` - Product planning, user stories, MVP definition
- `software-architect-designer` - Technical architecture following SOLID principles
- `ux-design-specialist` - UI/UX design, wireframes, accessibility

**Commands:**
- `/feature-workflow` - Complete feature development lifecycle
- `/design-workflow` - UI/UX design implementation workflow
- `/tech-request` - Technical request handling

**Skills:**
- **SOLID Principles** - Five core OOP design principles
- **Gang of Four Patterns** - 23 classic design patterns
- **OORP Patterns** - Reengineering patterns for legacy systems

**Example Usage:**
```
/feature-workflow Add user authentication with OAuth2 and JWT tokens
```

---

### 2. Development Toolkit (`02-development`)

**Purpose:** Implementation best practices, testing strategies, and API design

**Agents:**
- `implementation-engineer` - Clean code implementation with design patterns
- `code-quality-inspector` - Comprehensive code review and quality checks
- `qa-test-engineer` - Testing, QA, and test automation

**Skills:**
- **Testing Best Practices** - Unit, integration, E2E testing strategies
- **Code Review Checklist** - Systematic review covering all quality aspects
- **API Design Principles** - RESTful API design and best practices

**Example Usage:**
```
# Use the implementation engineer agent
Implement a payment processing service following SOLID principles
and the Strategy pattern for different payment methods
```

---

### 3. Debugging Toolkit (`03-debugging`)

**Purpose:** Systematic debugging with specialized diagnostic agents

**Agents:**
- `bug-analyst` - Issue triage and classification
- `error-detective` - Log analysis and error tracking
- `code-diagnostician` - Code quality and pattern analysis
- `fix-architect` - Solution design with minimal side effects
- `bugfix-implementer` - Fix implementation
- `fix-validator` - Testing and validation
- `bug-documenter` - Documentation and knowledge management

**Commands:**
- `/bugfix-workflow` - Complete debugging workflow from analysis to documentation

**Example Usage:**
```bash
/bugfix-workflow "Button not responding to clicks" --type=ui --scope=file

/bugfix-workflow "500 error on POST /api/users" --severity=critical --type=runtime
```

---

### 4. Language Tools (`04-language-tools`)

**Purpose:** Language-specific debugging and optimization

**Agents:**
- `python-debugger` - Python-specific debugging and profiling
- `react-debugger` - React component and state debugging
- `typescript-analyzer` - TypeScript type error analysis
- `performance-profiler` - Performance bottleneck identification

**Example Usage:**
```
# Automatically invoked based on file type during debugging
/bugfix-workflow "Memory leak in data processing" --type=runtime
```

---

### 5. Content Marketing Toolkit (`05-content-marketing`)

**Purpose:** Content creation and marketing materials

**Agents:**
- `content-marketer` - Blog posts, social media, SEO-optimized content

**Example Usage:**
```
Create a technical blog post about microservices architecture,
targeting senior developers, 1500 words, SEO-optimized for
"microservices best practices"
```

## 🎓 Skills System

Skills provide reusable knowledge that agents can access automatically. Each skill is a focused knowledge domain:

### Design & Architecture Skills
- **SOLID Principles** - Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion
- **Gang of Four Patterns** - Creational, Structural, and Behavioral patterns
- **OORP Patterns** - First Contact, Analysis, Planning, Testing, Migration, Transformation

### Development Skills
- **Testing Best Practices** - Testing pyramid, AAA pattern, fixtures, mocking, coverage
- **Code Review Checklist** - Functionality, security, performance, testing review guidelines
- **API Design Principles** - RESTful conventions, HTTP methods, status codes, versioning

## 🔄 Workflow Examples

### Complete Feature Development

```
/feature-workflow Add user profile image upload with thumbnail generation
```

**This orchestrates:**
1. **Product Strategist** creates specification with user stories
2. **Architect** designs technical solution and breaks into tasks
3. **Implementation Engineer** builds each component
4. **Code Quality Inspector** reviews each implementation
5. **QA Engineer** validates functionality and runs tests

### UI/UX Design Implementation

```
/design-workflow Redesign analytics dashboard with improved data visualization
```

**This orchestrates:**
1. **UX Designer** creates design solution with wireframes
2. **Architect** creates technical implementation plan
3. **Implementation Engineer** builds UI components
4. **Code Quality Inspector** reviews implementation
5. **QA Engineer** tests across devices and browsers
6. **UX Designer** validates final design matches specifications

### Systematic Debugging

```
/bugfix-workflow "App crashes when processing large datasets" --severity=high --type=runtime --scope=module
```

**This orchestrates:**
1. **Bug Analyst** analyzes and classifies the issue
2. **Error Detective** investigates logs and stack traces
3. **Code Diagnostician** examines code patterns
4. **Fix Architect** designs optimal solution
5. **Bugfix Implementer** implements the fix
6. **Fix Validator** validates fix and runs regression tests
7. **Bug Documenter** documents solution and prevention

## 🛠️ Customization

### Adding New Skills

1. Create skill directory: `.claude/plugins/{plugin-name}/skills/{skill-name}/`
2. Add `SKILL.md` with frontmatter:
   ```yaml
   ---
   name: my-skill
   description: When and how to use this skill
   ---
   # Skill Content
   ```

### Creating New Agents

1. Add agent file: `.claude/plugins/{plugin-name}/agents/my-agent.md`
2. Define agent with YAML frontmatter and prompt

### Adding Slash Commands

1. Create command file: `.claude/plugins/{plugin-name}/commands/my-command.md`
2. Define workflow orchestration logic

## 📊 Plugin Comparison

| Plugin | Agents | Commands | Skills | Primary Use Case |
|--------|--------|----------|--------|------------------|
| Product Design | 3 | 3 | 3 | Strategy, architecture, UX |
| Development | 3 | 0 | 3 | Implementation, testing, APIs |
| Debugging | 7 | 1 | 0 | Bug fixing, diagnostics |
| Language Tools | 4 | 0 | 0 | Language-specific debugging |
| Content Marketing | 1 | 0 | 0 | Content creation, SEO |

## 🎯 Token Optimization Benefits

The plugin architecture optimizes token usage by:

1. **Modular Loading**: Only active plugin content is loaded
2. **Skill Referencing**: Agents reference skills instead of embedding knowledge
3. **Progressive Disclosure**: Skills load detailed info only when needed
4. **Focused Contexts**: Each plugin has targeted domain knowledge

**Token Savings**: Up to 60-70% reduction compared to monolithic agent files.

## 💡 Best Practices

### When to Use Which Plugin

- **Planning new feature?** → Product Design (feature-workflow)
- **Implementing code?** → Development (agents + skills)
- **Bug in production?** → Debugging (bugfix-workflow)
- **Language-specific issue?** → Language Tools (auto-invoked)
- **Writing content?** → Content Marketing (content-marketer)

### Combining Plugins

Plugins work together seamlessly:
```
# Start with product design
/feature-workflow Add real-time notifications

# Development plugin handles implementation
# Debugging plugin handles any issues
# Language tools optimize language-specific code
```

## 📖 Documentation

- [Product Design Plugin](.claude/plugins/01-product-design/README.md)
- [Development Plugin](.claude/plugins/02-development/README.md)
- [Debugging Plugin](.claude/plugins/03-debugging/README.md)
- [Language Tools Plugin](.claude/plugins/04-language-tools/README.md)
- [Content Marketing Plugin](.claude/plugins/05-content-marketing/README.md)

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-skill`)
3. Add your skill/agent/command following the plugin structure
4. Test thoroughly
5. Submit a pull request

### Contribution Ideas

- Add new skills (e.g., security best practices, performance optimization)
- Create language-specific skills (Go, Rust, Java)
- Add domain-specific agents (DevOps, Data Science, Mobile)
- Improve existing workflows
- Add more comprehensive examples

## 📋 Roadmap & TODO

### Planned Skills (Future Additions)

#### Security & Best Practices
- [ ] **Security Best Practices** - OWASP Top 10, secure coding guidelines, vulnerability prevention
- [ ] **Authentication & Authorization** - OAuth, JWT, session management best practices
- [ ] **Data Protection** - Encryption, GDPR compliance, PII handling

#### Performance & Optimization
- [ ] **Performance Optimization** - Profiling, caching strategies, query optimization
- [ ] **Database Design** - Normalization, indexing strategies, query performance
- [ ] **Scalability Patterns** - Load balancing, caching, horizontal scaling

#### Code Quality & Maintenance
- [ ] **Clean Code Principles** - Robert C. Martin's principles, naming conventions, code smells
- [ ] **Refactoring Catalog** - Martin Fowler's refactoring patterns, when and how to refactor
- [ ] **Technical Debt Management** - Identifying, tracking, and paying down technical debt

#### Language-Specific Skills
- [ ] **Go Best Practices** - Idiomatic Go, concurrency patterns, error handling
- [ ] **Rust Patterns** - Ownership, borrowing, lifetime management
- [ ] **Java Design Patterns** - Enterprise patterns, Spring framework best practices

#### Domain-Specific
- [ ] **DevOps Practices** - CI/CD pipelines, infrastructure as code, monitoring
- [ ] **Microservices Patterns** - Service communication, data consistency, deployment
- [ ] **Event-Driven Architecture** - Event sourcing, CQRS, message queues

### Planned Agents
- [ ] **Security Specialist** - Security vulnerability analysis and recommendations
- [ ] **Database Optimizer** - Query optimization and schema design
- [ ] **DevOps Engineer** - CI/CD setup and infrastructure automation
- [ ] **Mobile Developer** - iOS/Android development best practices

### Planned Commands
- [ ] `/security-audit` - Comprehensive security audit workflow
- [ ] `/performance-optimization` - Performance analysis and optimization workflow
- [ ] `/refactoring-workflow` - Systematic refactoring workflow

## 📦 Publishing to Claude Code Marketplace

### Prerequisites for Marketplace Submission

To publish these plugins to the Claude Code Marketplace, you need to:

1. **GitHub Repository Setup**
   - Host plugins in a public GitHub repository
   - Each plugin should have proper documentation
   - Include clear installation instructions
   - Add LICENSE file (MIT recommended)

2. **Plugin Structure Requirements**
   ```
   your-repo/
   ├── .claude-plugin/
   │   └── marketplace.json    # Marketplace metadata
   ├── plugins/
   │   ├── plugin-1/
   │   │   ├── .claude-plugin/
   │   │   │   └── plugin.json
   │   │   ├── agents/
   │   │   ├── commands/
   │   │   └── skills/
   │   └── plugin-2/
   └── README.md
   ```

3. **Marketplace Manifest** (`.claude-plugin/marketplace.json`)
   ```json
   {
     "name": "claude-code-agents-workflow",
     "description": "Comprehensive development workflow plugins",
     "author": "Your Name",
     "homepage": "https://github.com/your-username/claude-code-agents-workflow",
     "plugins": [
       {
         "name": "product-design-toolkit",
         "path": ".claude/plugins/01-product-design"
       },
       {
         "name": "development-toolkit",
         "path": ".claude/plugins/02-development"
       },
       {
         "name": "debugging-toolkit",
         "path": ".claude/plugins/03-debugging"
       },
       {
         "name": "language-tools",
         "path": ".claude/plugins/04-language-tools"
       },
       {
         "name": "content-marketing-toolkit",
         "path": ".claude/plugins/05-content-marketing"
       }
     ]
   }
   ```

4. **Publishing Options**

   **Option A: Individual Plugin Repositories** (Recommended for marketplace)
   - Create separate repositories for each plugin
   - Each repository contains one focused plugin
   - Easier for users to install only what they need
   - Example:
     - `claude-code-product-design-toolkit`
     - `claude-code-development-toolkit`
     - `claude-code-debugging-toolkit`

   **Option B: Monorepo with Multiple Plugins**
   - Single repository with all plugins
   - Users can choose which plugins to install
   - Better for maintaining related plugins together
   - Use marketplace.json to list all available plugins

5. **Submission Process**
   - Ensure all plugins follow Claude Code plugin standards
   - Test plugins thoroughly in your local environment
   - Create proper documentation with examples
   - Submit to Claude Code Marketplace (when available)
   - Community can install via: `claude plugin install your-username/repo-name`

### Current Status

**✅ Ready for GitHub**: Plugins are properly structured and documented
**⏳ Marketplace**: Awaiting official Claude Code Marketplace launch

For now, users can install by:
```bash
git clone https://github.com/your-username/claude-code-agents-workflow.git
cp -r claude-code-agents-workflow/.claude/plugins/* ~/.claude/plugins/
```

### Publishing Checklist

- [ ] Create public GitHub repository
- [ ] Add comprehensive README with examples
- [ ] Include LICENSE file (MIT)
- [ ] Add `.claude-plugin/marketplace.json`
- [ ] Test all plugins in fresh Claude Code installation
- [ ] Create release tags for versioning
- [ ] Add GitHub topics: `claude-code`, `claude-plugin`, `ai-agents`
- [ ] Create example usage videos/GIFs
- [ ] Set up GitHub Discussions for community support

## 📝 License

MIT License - See [LICENSE](LICENSE) for details

## 🔗 Resources

- [Claude Code Documentation](https://docs.anthropic.com/claude-code)
- [Claude Code Plugins Guide](https://docs.claude.com/en/docs/claude-code/plugins)
- [Agent Skills Overview](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview)

## 💬 Support

- **Issues**: [GitHub Issues](https://github.com/your-username/claude-code-agents-workflow/issues)
- **Discussions**: [GitHub Discussions](https://github.com/your-username/claude-code-agents-workflow/discussions)

---

**Built with ❤️ for the Claude Code community**
