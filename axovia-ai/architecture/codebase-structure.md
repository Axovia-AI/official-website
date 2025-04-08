# codebase-structure.md — Axovia AI Website Project Structure

## Purpose
This document provides an **extensive definition** of every major directory and file within the Axovia AI Website project, ensuring consistency, maintainability, and clarity. It also describes how the `axovia-ai/` framework structure operates as a foundation for planning, memory, and AI assistant interactions.

---

## High-Level Overview
```
/
├── axovia-ai/            # Documentation, Agent Framework, and Project Planning
│   ├── checklists/         # Mandatory pre-task & post-task verification
│   │   ├── pre-task.md       # Verification steps to complete before starting a task
│   │   ├── post-task.md      # Verification steps to complete after finishing a task        
|   |   └── capabilities/`**: Documents the agent's perceived capabilities and limitations. 
│   │`      └── task-confidence.md  # Displays the agent's tasks with a confidence level
│   ├── memory/             # Memory context, current task, and management rules
│   │   ├── memory-context.md # Summaries of architectural state and decisions
│   │   ├── current-task.md   # Tracks the single active task in progress
│   │   └── memory-mgmt.md    # Guidelines for continuity and pruning stale data
│   ├── communication/      # Requests-to-human, answers-to-agent logs
│   │   ├── requests-to-human.md  # Agent queries requiring human feedback
│   │   └── answers-to-agent.md   # Human-provided solutions or decisions
│   ├── config/             # Environment templates, secrets management docs
│   │   ├── env-template.md      # Template specifying required environment variables
│   │   └── secrets-mgmt.md      # Best practices for API keys and sensitive data
│   ├── credentials/        # Securely stored API or platform credentials references
│   ├── rules/              # Custom rule sets (setup, resume, etc.)
│   │   ├── setup.rules        # Initial environment configuration rules
│   │   └── resume.rules       # Rules for resuming work on tasks
│   ├── notes/              # Development notes, meeting notes, technical debt
│   │   ├── development-notes.md  # Running log of day-to-day dev decisions
│   │   ├── meeting-notes.md      # Summaries of stakeholder discussions
│   │   └── technical-debt.md     # Lists known issues for future resolution
│   ├── architecture/       # System diagrams, code structure, design guidelines
│   │   ├── codebase-structure.md   # This document - codebase organization
│   │   ├── component-registry.md   # Registry of reusable components
│   │   ├── design-system.md        # Design principles and guidelines
│   │   ├── api-guide.md            # API documentation and usage
│   │   └── workflow-diagrams.md    # Visual representations of key workflows
│   ├── monitoring/         # Errors, metrics, evaluation, logs
│   │   ├── errors.md         # Catalog of known error states and solutions
│   │   └── metrics.md        # Performance or usage statistics tracking
│   ├── plugins/            # Any plugin architecture docs
│   ├── research/           # Research findings on tools, APIs, or approaches
│   ├── testing/            # Testing plan, coverage tracking, e2e test docs
│   │   ├── test-coverage.md   # Documentation of test coverage requirements
│   │   └── testing-plan.md    # Strategic approach to testing the system
│   ├── versioning/         # Version-control guidelines, version history
│   │   ├── version-control.md   # Guidelines for version control procedures
│   │   └── version-history.md   # Record of version changes and updates
│   ├── planning/           # Master implementation plan, major scheduling
│   │   └── implementation-plan.md  # Comprehensive list of tasks with statuses
│   ├── integrations/       # External service integration docs
│   │   ├── zapier.md            # Documentation for Zapier integration
│   │   └── langchain_integration.md  # Documentation for LangChain integration
│   └── ci/                 # CI/CD scripts, pipeline feedback logic
│       └── pipeline-feedback-check.sh  # Script to block progress if tests fail
├── testing/                # Project-wide testing resources
│   ├── testing-plan.md       # Overall testing strategy for the project
│   └── testing-coverage.md   # Documentation of test coverage across the project
└── ...
```

---
## File Descriptions

### Root Level Files

#### CHANGELOG.md
- **Purpose**: Documents version history and changes to the project
- **Content**: Follows the Keep a Changelog format with sections for Added, Changed, Fixed, and Removed
- **Usage**: Updated with each release to track project evolution

#### CONTRIBUTING.md
- **Purpose**: Guidelines for contributing to the project
- **Content**: Development setup, workflow processes, coding standards, and PR guidelines
- **Usage**: Reference for new contributors and team members

### Architecture Directory

#### api-guide.md
- **Purpose**: Documents APIs and integration points
- **Content**: API endpoints, parameters, authentication, response formats, and example usage
- **Usage**: Reference for developers implementing integrations

#### codebase-structure.md
- **Purpose**: Explains the project's file organization
- **Content**: Directory structure, file purposes, and organization principles
- **Usage**: Orientation for new developers and maintaining consistent organization

#### component-registry.md
- **Purpose**: Catalogs all system components
- **Content**: Component names, responsibilities, dependencies, and usage examples
- **Usage**: Reference to understand component relationships and responsibilities

#### design-system.md
- **Purpose**: Defines UI/UX standards
- **Content**: Color schemes, typography, spacing, components, and accessibility guidelines
- **Usage**: Ensures consistent design implementation across the application

#### user-flows.md
- **Purpose**: Documents user journeys
- **Content**: Step-by-step user paths through key features with annotations
- **Usage**: Understanding user experience and feature relationships

#### workflow-diagrams.md
- **Purpose**: Visualizes system processes
- **Content**: Flowcharts, sequence diagrams, and data flow diagrams
- **Usage**: Understanding complex interactions between system components

### Checklist Directory

#### post-task.md
- **Purpose**: Verification steps after task completion
- **Content**: Checklist for documentation, testing, and code quality
- **Usage**: Ensure consistent task closure and quality control

#### pre-task.md
- **Purpose**: Preparation steps before starting a task
- **Content**: Checklist for understanding requirements, checking dependencies, and planning
- **Usage**: Ensure proper preparation and prevent rework

### Cursor Rules Directory

#### resume.md
- **Purpose**: Guidelines for resuming work after breaks
- **Content**: Steps to reload context and re-establish understanding of state
- **Usage**: Maintain continuity between work sessions

#### resume.mdc
- **Purpose**: Template for context resumption
- **Content**: Markdown template for documenting session state
- **Usage**: Standardize context documentation

#### settings.cursorrules
- **Purpose**: Agent behavior configuration
- **Content**: Rules, preferences, and constraints for agent operation
- **Usage**: Standardize agent behavior across sessions

#### setup.md
- **Purpose**: Project setup instructions
- **Content**: Environment setup, tool installation, and configuration steps
- **Usage**: Onboarding new developers

#### start-task.md
- **Purpose**: Task initialization guidelines
- **Content**: Steps for properly beginning new tasks
- **Usage**: Establish consistent task handling

### Memory Directory

#### context-memory.md
- **Purpose**: Stores current project state
- **Content**: Implementation details, decisions, and current progress
- **Usage**: Maintain continuity across development sessions

#### current-task.md
- **Purpose**: Tracks active tasks
- **Content**: Task details, status, progress, and blockers
- **Usage**: Focus point for current development efforts

#### memory-mgmt.md
- **Purpose**: Memory management guidelines
- **Content**: Principles for managing agent memory
- **Usage**: Optimize agent performance and context management

### Planning Directory

#### implementation-plan.md
- **Purpose**: Project roadmap and task tracking
- **Content**: Tasks, statuses, dependencies, and implementation details
- **Usage**: Guide development sequence and monitor progress

## Other Key Directories

### feature-prompts/
- **Purpose**: Feature specifications
- **Content**: Detailed requirements, user stories, and acceptance criteria
- **Usage**: Define expected functionality for implementation

### research/
- **Purpose**: Research findings
- **Content**: Analysis of technologies, approaches, and alternatives
- **Usage**: Document research to inform development decisions

### integrations/
- **Purpose**: External service integration documentation
- **Content**: Integration details, authentication methods, and usage examples
- **Usage**: Guide for implementing external service connections

### logic/
- **Purpose**: Agent logic patterns
- **Content**: Algorithms, decision trees, and pattern implementations
- **Usage**: Reference for implementing consistent agent behaviors

## Development Workflow

The development workflow follows these steps:

1. Review the implementation plan to identify the next task
2. Complete the pre-task checklist to ensure proper preparation
3. Implement the task following the project's coding standards
4. Update the context memory with new implementation details
5. Complete the post-task checklist to verify proper completion
6. Update the implementation plan with the task status
7. Commit changes following the project's versioning guidelines

## Implementation Patterns

The Axovia Flow project implements several agent patterns:

1. **Evaluator-Optimizer Pattern**: Used for content refinement where content is iteratively evaluated and optimized.
2. **Orchestrator-Worker Pattern**: Used for parallel task processing where an orchestrator delegates subtasks to workers.
3. **Expert Panel Pattern**: Used for complex decisions requiring input from multiple specialized agents.
4. **Memory-Augmented Pattern**: Used for learning from historical data and improving over time.
5. **Tool-Agent Pattern**: Used for agents that can utilize external tools and APIs.
6. **Swarm Intelligence Pattern**: Used for collaborative problem-solving across multiple agents.

## Conclusion

This document provides a comprehensive reference for the Axovia Flow project structure. Maintaining this organization is crucial for scalability, maintainability, and collaboration. All team members should follow these guidelines when adding new files or modifying existing ones. 

## Social Media Manager Directory Structure

```
social_media_manager/                  # Flutter web application
├── android/                           # Android platform configuration
├── ios/                               # iOS platform configuration
├── web/                               # Web platform configuration
├── macos/                             # macOS platform configuration
├── linux/                             # Linux platform configuration
├── windows/                           # Windows platform configuration
├── lib/                               # Dart source code
│   ├── config/                        # Application configuration
│   │   ├── firebase_options.dart      # Firebase project configuration
│   │   ├── routes.dart                # Application routing definitions
│   │   └── theme.dart                 # Theme and styling configuration
│   ├── main.dart                      # Application entry point
│   ├── models/                        # Data models
│   ├── providers/                     # State management providers
│   ├── screens/                       # UI screens by feature
│   │   ├── auth/                      # Authentication screens
│   │   ├── dashboard/                 # Dashboard screens
│   │   ├── content/                   # Content management screens
│   │   ├── platforms/                 # Platform-specific screens
│   │   ├── analytics/                 # Analytics and reporting screens
│   │   ├── schedule/                  # Scheduling screens
│   │   └── settings/                  # Settings and configuration screens
│   ├── services/                      # Service layer for API interactions
│   ├── src/                           # Core implementation
│   │   ├── core/                      # Core functionality
│   │   │   ├── repositories/          # Data repositories
│   │   │   └── services/              # Core services
│   │   ├── features/                  # Feature modules
│   │   │   ├── instagram/             # Instagram-specific features
│   │   │   │   ├── agents/            # Instagram AI agents
│   │   │   │   ├── models/            # Instagram data models
│   │   │   │   ├── screens/           # Instagram UI screens
│   │   │   │   ├── services/          # Instagram services
│   │   │   │   └── widgets/           # Instagram-specific widgets
│   │   │   └── [other platforms]      # Other platform-specific features
│   │   └── shared/                    # Shared components
│   │       ├── theme/                 # Theme constants
│   │       └── widgets/               # Shared widgets
│   ├── utils/                         # Utility functions
│   └── widgets/                       # Reusable UI components
│       ├── analytics_widgets/         # Analytics-specific widgets
│       ├── common/                    # Common widgets
│       ├── dashboard/                 # Dashboard widgets
│       ├── navigation/                # Navigation components
│       └── platform_widgets/          # Platform-specific widgets
├── test/                              # Test directory
│   ├── unit/                          # Unit tests
│   ├── widget/                        # Widget tests
│   └── integration/                   # Integration tests
├── firebase.json                      # Firebase configuration
├── .firebaserc                        # Firebase project configuration
├── pubspec.yaml                       # Flutter dependencies
└── pubspec.lock                       # Flutter dependency lock file
```

## Functions Directory Structure

```
functions/                             # Firebase Cloud Functions
├── python/                            # Python cloud functions
│   ├── main.py                        # Cloud Functions entry point
│   ├── agents/                        # AI agent implementation
│   │   ├── base/                      # Base agent classes
│   │   │   ├── agent.py               # Abstract agent base class
│   │   │   ├── patterns/              # Implementation patterns
│   │   │   │   ├── evaluator_optimizer.py   # Content refinement pattern
│   │   │   │   ├── orchestrator_worker.py   # Parallel processing pattern
│   │   │   │   ├── expert_panel.py          # Multi-agent consensus pattern
│   │   │   │   └── memory_augmented.py      # Learning from history pattern
│   │   │   └── state.py               # Agent state management
│   │   ├── content/                   # Content management agents
│   │   ├── platforms/                 # Platform-specific agents
│   │   │   ├── instagram/             # Instagram-specific agents
│   │   │   ├── tiktok/                # TikTok-specific agents
│   │   │   ├── x/                     # X-specific agents
│   │   │   └── reddit/                # Reddit-specific agents
│   │   └── analytics/                 # Analytics and insights agents
│   ├── services/                      # External API integrations
│   ├── utils/                         # Utility functions
│   │   ├── firebase.py                # Firebase interactions
│   │   ├── logging.py                 # Logging utilities
│   │   └── validation.py              # Input validation
│   └── requirements.txt               # Python dependencies
├── package.json                       # Node.js configuration
└── tsconfig.json                      # TypeScript configuration
```

## Key Files Explained

### Root Level Files

- **CHANGELOG.md**: Documents all notable changes to the project, including new features, bug fixes, and breaking changes.
- **CONTRIBUTING.md**: Guidelines for contributing to the project, including coding standards, pull request process, and development setup.

### Architecture Files

- **architecture/codebase-structure.md**: This file - provides a comprehensive view of the project's file organization.
- **architecture/component-registry.md**: Catalogs all system components with their responsibilities and relationships.
- **architecture/design-system.md**: Defines UI/UX patterns, color schemes, typography, and layout guidelines.
- **architecture/user-flows.md**: Describes user journeys through the application for key scenarios.
- **architecture/workflow-diagrams.md**: Visual representations of system processes and data flows.
- **architecture/api-guide.md**: Documentation for API interfaces, endpoints, and usage examples.

### Planning Files

- **planning/implementation-plan.md**: Detailed roadmap of tasks, their status, dependencies, and implementation details.

### Memory Management Files

- **memory/context-memory.md**: Keeps track of the current project state, decisions, and implementation details for continuity.
- **memory/current-task.md**: Tracks the active task being worked on, including its status, progress, and blockers.
- **memory/memory-mgmt.md**: Guidelines for managing and organizing agent memory for optimal performance.

### Cursor IDE Configuration

- **cursorrules/settings.cursorrules**: Configuration for agent behavior, preferences, and constraints.
- **cursorrules/setup.md**: Comprehensive setup instructions for developers starting with the project.
- **cursorrules/start-task.md**: Guidelines for properly initializing and beginning new tasks.
- **cursorrules/resume.mdc**: Markdown templates for resuming project context.

## Implementation Patterns

The Axovia Flow project implements several agent patterns:

1. **Evaluator-Optimizer Pattern**: Used for content refinement where content is iteratively evaluated and optimized.
2. **Orchestrator-Worker Pattern**: Used for parallel task processing where an orchestrator delegates subtasks to workers.
3. **Expert Panel Pattern**: Used for complex decisions requiring input from multiple specialized agents.
4. **Memory-Augmented Pattern**: Used for learning from historical data and improving over time.
5. **Tool-Agent Pattern**: Used for agents that can utilize external tools and APIs.
6. **Swarm Intelligence Pattern**: Used for collaborative problem-solving across multiple agents.

## Development Workflow

The development workflow follows these steps:

1. Review the implementation plan to identify the next task
2. Complete the pre-task checklist to ensure proper preparation
3. Implement the task following the project's coding standards
4. Update the context memory with new implementation details
5. Complete the post-task checklist to verify proper completion
6. Update the implementation plan with the task status
7. Commit changes following the project's versioning guidelines

## File Naming Conventions

- **Dart Files**: Snake case (e.g., `user_profile.dart`, `auth_service.dart`)
- **Python Files**: Snake case (e.g., `content_analyzer.py`, `instagram_service.py`)
- **Markdown Documentation**: Kebab case (e.g., `user-flows.md`, `api-guide.md`)
- **Configuration Files**: Standard conventions for each tool (e.g., `firebase.json`, `pubspec.yaml`)

## Dependencies and Tools

- **Flutter/Dart**: Frontend application framework
- **Firebase**: Backend services (Auth, Firestore, Storage, Functions, Hosting)
- **LangGraph**: Agent orchestration framework for LLM agents
- **Python**: Used for Cloud Functions and agent implementation

## Conclusion

This document provides a comprehensive reference for the Axovia Flow project structure. Maintaining this organization is crucial for scalability, maintainability, and collaboration. All team members should follow these guidelines when adding new files or modifying existing ones.
