# Custom Claude Code Agents

A collection of specialized AI sub-agents and custom commands for Claude Code, designed to enhance software development workflows through intelligent task delegation and automation.

## Overview

This repository contains custom sub-agents that extend Claude Code's capabilities by providing specialized expertise for different aspects of software development. Each agent is designed to handle specific types of tasks, enabling more efficient and focused development workflows.

## Sub-Agents

### 🟣 code-executor
**Purpose**: Execute code, run scripts, and test functionality without any code modification.

**When to use**: 
- Running Python scripts, Node.js applications, or shell scripts
- Executing test suites (pytest, jest, mocha, etc.)
- Starting development servers and build processes
- Running database migrations and deployment scripts
- Executing linting tools and formatters

**Tools**: Bash, Glob, Grep, LS, ExitPlanMode, Read, NotebookRead, WebFetch, TodoWrite, WebSearch

**Key Features**:
- Analyzes project structure to determine appropriate execution methods
- Generates correct commands based on file extensions and project dependencies
- Captures and reports complete output including errors and warnings
- Never modifies code - purely focused on execution

### 🟡 code-implementation-specialist
**Purpose**: Implement, refactor, and debug code based on specific requirements and instructions.

**When to use**:
- Implementing code solutions from defined specifications
- Refactoring existing code for better maintainability
- Debugging and fixing issues in codebases
- Creating functional UI prototypes

**Key Features**:
- Writes modular, reusable code following SOLID principles
- Ensures proper separation of concerns and error handling
- Follows language-specific conventions and best practices
- Focuses on production-ready implementation without testing or reviews

### 📊 codebase-analyzer
**Purpose**: Comprehensive analysis of codebases including component interactions, data flow, and architectural patterns.

**When to use**:
- Understanding complex codebases before making modifications
- Code reviews and onboarding new developers
- Analyzing component interactions and dependencies
- Identifying potential gotchas and architectural patterns

**Tools**: Read, Glob, Grep, LS, WebFetch, WebSearch

**Key Features**:
- Maps component interactions and data flow patterns
- Identifies architectural decisions and design patterns
- Highlights potential pitfalls and areas requiring special attention
- Generates detailed reports for developer understanding

### 🎯 feature-implementation-lead
**Purpose**: Coordinate the complete implementation of individual features through specialized sub-agents.

**When to use**:
- Implementing complete features broken down from larger requests
- Coordinating multiple implementation phases and tasks
- Managing feature integration with existing codebase

**Tools**: Glob, Grep, LS, ExitPlanMode, Read, NotebookRead, WebFetch, TodoWrite, WebSearch

**Key Features**:
- Never writes code directly - orchestrates through delegation
- Breaks features into logical implementation phases
- Coordinates specialized sub-agents for all technical work
- Ensures feature completeness and quality integration

### 🔵 meta-agent
**Purpose**: Create new specialized sub-agents based on user requirements.

**When to use**:
- User requests creation of new agents ("create an agent that...")
- Need for specialized agents for specific tasks
- Custom agent requirements for project-specific needs

**Tools**: Write, WebFetch, WebSearch, LS, Read, Glob, Grep

**Key Features**:
- Analyzes requirements and generates complete agent configurations
- Creates unique identifiers and appropriate tool selections
- Generates comprehensive Markdown files with system prompts
- Ensures agents are production-ready specialists

### 🟢 production-code-reviewer
**Purpose**: Comprehensive quality review of completed code features to ensure production-level standards.

**When to use**:
- After logical chunks of code are written
- Before code is merged to production
- When comprehensive quality assurance is needed

**Tools**: Glob, Grep, LS, ExitPlanMode, Read, NotebookRead, WebFetch, TodoWrite, WebSearch

**Key Features**:
- Systematic evaluation of architecture, structure, and best practices
- Security vulnerability assessment and performance analysis
- Provides structured review reports with clear recommendations
- Distinguishes between critical issues and improvements

### 🔬 technical-research-consultant
**Purpose**: Comprehensive, expert-level analysis and guidance on software engineering topics and implementation strategies.

**When to use**:
- Need for deep technical research on specific topics
- Evaluating different technologies or implementation approaches
- Seeking expert analysis with practical recommendations

**Tools**: Bash, Glob, Grep, LS, Read, NotebookRead, WebFetch, WebSearch, mcp__ide__getDiagnostics

**Key Features**:
- Provides research-backed analysis and practical guidance
- Considers scalability, maintainability, and performance implications
- Offers context-specific advice tailored to existing codebase
- Prioritizes open-source and accessible solutions

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

**Code Implementation**:
```
User: "Implement a user authentication system"
→ feature-implementation-lead coordinates the feature
→ code-implementation-specialist handles the actual coding
→ production-code-reviewer ensures quality
→ code-executor runs tests
```

**Codebase Understanding**:
```
User: "Help me understand how this legacy system works"
→ codebase-analyzer provides comprehensive analysis
→ technical-research-consultant offers implementation guidance
```

**Custom Agent Creation**:
```
User: "Create an agent that generates API documentation"
→ meta-agent analyzes requirements and creates new specialized agent
```

## Contributing

When creating new agents or commands:

1. Follow the established naming conventions (lowercase with hyphens)
2. Include comprehensive descriptions and clear "when to use" guidelines
3. Specify appropriate tools and maintain focused responsibilities
4. Test thoroughly before submitting

## License

This project is open source and available under the MIT License.