# Custom Claude Code Agents

A collection of specialized AI sub-agents and custom commands for Claude Code, designed to enhance software development workflows through intelligent task delegation and automation.

## Overview

This repository contains custom sub-agents that extend Claude Code's capabilities by providing specialized expertise for different aspects of software development. Each agent is designed to handle specific types of tasks, enabling more efficient and focused development workflows.

## Sub-Agents

### 🟡 code-implementation-specialist
**Purpose**: Single-component code implementation tasks with clear, specific requirements.

**When to use**:
- Atomic coding tasks like "Add validation to the login form"
- Bug fixes with clear specifications ("Fix the database connection timeout bug")
- Refactoring specific components ("Refactor the UserService class for better error handling")
- Small, well-defined implementation tasks

**Tools**: Glob, Grep, LS, Read, Edit, MultiEdit, Write, NotebookRead, NotebookEdit

**Key Features**:
- Focuses on single-component implementations
- Requires 100% clarity on requirements before starting
- Cannot ask for clarification - requirements must be crystal clear
- Perfect for atomic coding tasks with specific outcomes

### 📊 codebase-analyzer
**Purpose**: Comprehensive architectural analysis of existing codebases to understand how systems work.

**When to use**:
- Understanding unfamiliar code before making changes
- Codebase onboarding and system architecture analysis
- Analyzing component interactions, data flow, and design patterns
- Generating detailed reports about system structure

**Tools**: Read, Glob, Grep, LS, WebFetch, WebSearch

**Key Features**:
- Specialist for generating architectural analysis reports
- Maps component interactions and data flow patterns
- Identifies design patterns and system structure
- Does NOT perform code quality assessment or production readiness reviews

### 🟣 code-executor
**Purpose**: Execute code, run scripts, or test functionality without any code modification.

**When to use**: 
- Running Python scripts, development servers, or applications
- Executing test suites and checking functionality
- Starting services to verify changes work correctly
- Running commands without modifying any code

**Tools**: Bash, Glob, Grep, LS, Read, NotebookRead

**Key Features**:
- Purely execution-focused - never modifies code
- Analyzes project structure to determine correct commands
- Captures and reports complete output including errors
- Perfect for testing and verification workflows

### 🎯 feature-implementation-lead
**Purpose**: Implement complete features requiring multiple components or coordination between different parts of the system.

**When to use**:
- Complex features like "user authentication system" or "payment processing"
- Features involving 3+ files or multiple implementation phases
- Tasks requiring research/architectural decisions
- Features needing coordination between different system parts

**Tools**: Glob, Grep, LS, Read, NotebookRead, WebFetch, TodoWrite, WebSearch

**Key Features**:
- Manages complex features requiring multiple components
- Handles features needing research and architectural decisions
- Coordinates implementation phases and file dependencies
- Use for features, not single-component tasks

### 🚀 project-coordinator
**Purpose**: Coordinate multiple features, complex multi-stage projects, or high-level project planning spanning multiple components/systems.

**When to use**:
- Building complete applications ("social media platform with user management, posting, and messaging")
- Major architectural changes ("migrate entire backend from REST API to GraphQL")
- Complex projects requiring multiple features working together
- Enterprise-level implementations requiring multiple workstreams

**Tools**: Glob, Grep, LS, Read, NotebookRead, WebFetch, TodoWrite, WebSearch

**Key Features**:
- Handles project-level orchestration beyond individual features
- Coordinates multiple feature-implementation-lead agents
- Manages complex project phases and dependencies
- Provides comprehensive project reports upon completion

### 🧪 testing-specialist
**Purpose**: Comprehensive testing support including unit tests, integration tests, end-to-end tests, testing strategies, and test infrastructure.

**When to use**:
- Writing and maintaining test suites (unit, integration, e2e)
- Analyzing test coverage and identifying testing gaps
- Setting up testing infrastructure and CI/CD integration
- Debugging test failures and optimizing test performance
- Establishing testing best practices

**Tools**: Read, Write, Edit, MultiEdit, Bash, Glob, Grep, LS, WebSearch, WebFetch

**Key Features**:
- Expert in all aspects of software testing and QA
- Handles testing across any programming language or framework
- Designs comprehensive testing strategies and infrastructure
- Focuses exclusively on testing-related activities

### 🔬 technical-research-consultant
**Purpose**: Expert research and guidance on software engineering technologies, implementation strategies, and technical decision-making.

**When to use**:
- Technology evaluation and comparison ("What's the best approach for X?")
- Implementation strategy research ("How do I implement Y?")
- Technical decision-making ("What are the trade-offs between A and B?")
- Industry best practices and actionable recommendations

**Tools**: WebFetch, WebSearch

**Key Features**:
- Specializes in technology evaluation and research
- Provides actionable recommendations for technical choices
- Focuses on implementation strategies and best practices
- Does NOT analyze existing codebases (use codebase-analyzer for that)

### 📚 codebase-documenter
**Purpose**: Create or update documentation for new features, refactored code, or existing codebase components.

**When to use**:
- After implementing new functionality that needs documentation
- Following refactoring work that requires updated docs
- When existing documentation becomes outdated
- Creating comprehensive system documentation

**Tools**: Glob, Grep, LS, Read, Edit, MultiEdit, Write, WebSearch

**Key Features**:
- Works with existing code only - does not write or modify code
- Creates comprehensive documentation including README files, API docs, and architectural guides
- Analyzes system architecture to understand component interactions
- Should be called AFTER code implementation is complete

### 🟢 production-code-reviewer
**Purpose**: Comprehensive QUALITY and PRODUCTION READINESS review of completed code.

**When to use**:
- After code implementation is complete and needs quality assessment
- Before code deployment to check production readiness
- When comprehensive security, performance, and best practices review is needed
- Evaluating code for bugs, security issues, and production safety

**Tools**: Glob, Grep, LS, Read, NotebookRead, WebFetch, WebSearch

**Key Features**:
- Use ONLY after code implementation is complete
- Evaluates code for production readiness and quality
- Assesses security vulnerabilities and performance issues
- Does NOT analyze how existing code works (use codebase-analyzer for that)

### 🛡️ security-specialist
**Purpose**: Cybersecurity expertise including security audits, vulnerability assessments, threat modeling, and secure development practices.

**When to use**:
- Security audits and vulnerability assessments
- Implementing authentication, authorization, and encryption
- Compliance requirements (GDPR, SOC2, HIPAA, PCI-DSS)
- Code security reviews and penetration testing guidance
- Security hardening and incident response planning

**Tools**: Read, Write, Edit, Bash, Grep, Glob, LS, WebSearch, WebFetch

**Key Features**:
- Expert in all aspects of information security and cybersecurity
- Conducts thorough security assessments with risk ratings
- Implements security-by-design principles and defense-in-depth strategies
- Provides detailed remediation steps and compliance guidance
- Focuses exclusively on security aspects, not general code reviews

### ⚙️ devops-specialist
**Purpose**: DevOps expertise for infrastructure, CI/CD pipelines, containerization, deployment strategies, and operational concerns.

**When to use**:
- Infrastructure as Code (Terraform, CloudFormation, Ansible)
- CI/CD pipeline design and implementation
- Containerization and orchestration (Docker, Kubernetes)
- Cloud platforms (AWS, GCP, Azure) and deployment strategies
- Environment configuration, secrets management, and monitoring setup

**Tools**: Read, Write, Edit, Bash, Glob, Grep, WebSearch, WebFetch

**Key Features**:
- Expert in all aspects of DevOps and infrastructure management
- Designs scalable and maintainable infrastructure solutions
- Implements proper security, monitoring, and disaster recovery
- Provides production-ready solutions with clear implementation steps
- Use proactively for any infrastructure or operational tasks

### 📄 file-reader
**Purpose**: Generate detailed file summaries to preserve context for other agents without requiring them to read entire files.

**When to use**:
- When other agents need file context but files are too large to read completely
- Creating comprehensive summaries of complex codebases
- Preserving critical file information for efficient context management
- Memory optimization across agent interactions

**Tools**: Read, Glob, LS, Grep

**Key Features**:
- Specialist for reading any file type and generating structured summaries
- Captures key components, dependencies, and critical implementation details
- Provides context preservation for the entire agent ecosystem
- Enables other agents to work effectively without reading original files
- Focuses exclusively on file reading and summarization

### 🔵 meta-agent
**Purpose**: Create new custom sub-agents when explicitly requested by users.

**When to use**:
- User explicitly requests creation of a new agent
- Phrases like "create an agent", "build me an agent", "I need an agent that"
- Custom agent requirements for specific project needs

**Tools**: Write, WebFetch, WebSearch, LS, Read, Glob, Grep

**Key Features**:
- ONLY creates new agent definition files
- Use ONLY when user explicitly requests agent creation
- Does not perform any other tasks beyond agent creation
- Generates complete agent configurations with system prompts

## Custom Commands

### `/add-commit-push`
**Purpose**: Streamlined git workflow for adding, committing, and pushing changes.

**Functionality**:
- Adds all modified and new files to git staging
- Creates commits with clear, semantic commit messages
- Pushes changes to origin
- Asks user about files that shouldn't be in version control
- Handles separate commits for different file groups when appropriate

### `/all-tools`
**Purpose**: Display all available tools in Claude Code.

**Functionality**:
- Lists all available tools from the system prompt
- Displays tools in TypeScript function signature format
- Shows the purpose of each tool
- Formats output with proper spacing for readability

## Installation

1. Clone this repository to your local machine
2. Copy the desired agent files to your Claude Code agents directory:
   - Project-specific: `.claude/agents/`
   - Global: `~/.claude/agents/`
3. Copy custom commands to your Claude Code commands directory:
   - Project-specific: `.claude/commands/`
   - Global: `~/.claude/commands/`

## Usage

These agents are automatically available in Claude Code once installed. Claude will intelligently delegate tasks to the appropriate specialized agent based on the context and requirements of your requests.

### Example Workflows

**Single Component Implementation**:
```
User: "Add validation to the login form"
→ code-implementation-specialist implements the validation
→ code-executor runs tests to verify functionality
→ production-code-reviewer ensures quality before deployment
```

**Complex Feature Implementation**:
```
User: "Implement a user authentication system"
→ feature-implementation-lead coordinates the multi-component feature  
→ testing-specialist writes comprehensive test suites
→ codebase-documenter creates documentation
→ production-code-reviewer ensures production readiness
```

**Large-Scale Project**:
```
User: "Build a complete e-commerce platform"
→ project-coordinator manages the multi-feature project
→ Multiple feature-implementation-lead agents handle individual features
→ testing-specialist ensures comprehensive testing across features
→ codebase-documenter maintains project documentation
```

**Codebase Understanding**:
```
User: "Help me understand how this legacy system works"
→ codebase-analyzer provides comprehensive architectural analysis
→ technical-research-consultant offers modernization guidance
```

**Security and DevOps**:
```
User: "Set up secure CI/CD pipeline with vulnerability scanning"
→ devops-specialist designs the CI/CD infrastructure
→ security-specialist implements security scanning and hardening
→ testing-specialist integrates security tests into the pipeline
→ codebase-documenter creates operational documentation
```

**Documentation and Quality**:
```
User: "I just refactored the database layer, document the changes"
→ file-reader summarizes the refactored components for context
→ codebase-documenter analyzes the changes and updates docs
→ production-code-reviewer ensures the changes meet production standards
```

## Contributing

When creating new agents or commands:

1. Follow the established naming conventions (lowercase with hyphens)
2. Include comprehensive descriptions and clear "when to use" guidelines
3. Specify appropriate tools and maintain focused responsibilities
4. Test thoroughly before submitting

## License

This project is open source and available under the MIT License.