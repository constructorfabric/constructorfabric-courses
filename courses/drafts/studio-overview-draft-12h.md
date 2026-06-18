# Constructor Studio Academy - Course Blueprint and Table of Contents

> NOTE: These course materials are a draft, generated from the following source repositories:
> - https://github.com/constructorfabric/studio
> - https://github.com/constructorfabric/studio-kit-sdlc

## 1. Target Audience, Problem, and Solution

### 1.1 Target Audience

This course addresses practitioners who work at the intersection of AI-assisted requirements and design generation, coding, and structured software delivery:

- **Product-minded engineers** who translate business requirements into structured design and want to preserve intent through implementation.
- **Technical leads and architects** responsible for delivery quality, traceability, and review readiness across teams.
- **Developers** who use AI coding tools daily and need a reliable way to keep requirements, design, and code aligned.
- **Quality Assurance (QA) engineers** who oversee requirements, design, implementation, and tests to ensure changes remain verifiable, consistent, and review-ready.
- **DevOps and platform engineers** who integrate validation and traceability checks into CI pipelines.
- **Kit and extension authors** who build reusable workflow packages, artifact kinds, and project rules for teams.

### 1.2 Nature of the Software Development Process

Software development is a chain of lossy transformations from human intent to executable code:

- **Requirements** are written by humans in natural language that is not mathematically strict and always assumes some level of uncertainty. Yet requirements contain clear intent, directions, and limitations that must be carried into design.
- **Design** is written in human language as a result of requirements interpretation and transformation, enriched with additional implicit and explicit context (architectural decisions, business constraints, security and privacy rules). Design contains a transformed intent, directions, and limitations for implementation — but the transformation is lossy and interpretive.
- **Implementation** is the most precise executable specification, written in machine language as a result of requirements and design interpretation, transformation, and application of additional technical context and constraints.

At every stage the process involves acceptance, transformation, validation, and feedback. Everything is non-deterministic and lossy.

### 1.3 How AI Changes the Development Flow

AI has changed development flow velocity drastically:

1. LLMs are superior in language **translation**, including human (requirements) to machine (code) language translation.
2. LLMs encode statistical representations of **best practices** to enrich unspecified context and think over design or code.
3. Agentic flows provide integrated **search** and needed context **retrieval** in runtime.

But AI does not automatically guarantee **fidelity** — requirements, design, and code **quality**, **clarity**, and **consistency** remains critical.

**Key question:** how to improve quality and speed of acceptance, transformation, validation, and feedback?

### 1.4 Typical Tooling Problem

The ideal system keeps intent, design, and code in one integrated ecosystem. Current tooling falls short:

- No tools are responsible for end-to-end Requirements ↔ Design ↔ Code ↔ Tests consistency.
- SDD frameworks (OpenSpec, BMAD) mostly focus on generation, but not on acceptance and traceability.
- SDD frameworks live separately and are not natively integrated into IDE UI or CI.
- Documents and code comments quickly become outdated and require manual housekeeping.
- Developers use their own prompts that are not necessarily complete and optimized for the projects.

### 1.5 What Constructor Studio Is and Who It Is For

Constructor Studio is a repo-attached workflow, context, and validation system for AI-native software delivery. It works with AI coding hosts and agentic IDEs such as Claude Code, OpenAI Codex, Cursor, Windsurf, and similar tools — instead of trying to replace them.

It helps development teams keep requirements, design, plans, code, and review evidence aligned through inspectable artifacts, structured workflows, deterministic checks, and traceability across the delivery lifecycle.

Constructor Studio is most useful for developers, architects, technical leads, QA, DevOps who need more than one-shot generation and need to control full project lifecycle - initial development, new feature implementation, later re-achitecture, etc.

---

## 2. Course Frame

Description: This course teaches Constructor Studio from first principles through advanced operation and extension authoring. It uses the established Constructor Studio terminology throughout the learner-facing material.

### 2.1 Learning Paths and Tracks

Description: The course has one shared foundation, then separates into an Operator track and a Kit and Extension Author track. Learners can complete the Operator track alone or continue into authoring and certification work.

#### Lessons and Checkpoints

- 2.1.1 Operator path: using Constructor Studio in real projects
- 2.1.2 Author path: building kits, workflows, skills, and extensions
- 2.1.3 Recommended paths by role
- 2.1.4 Checkpoint: choose your learner path

### 2.2 Command and Terminology Standard

Description: All lessons use the standard Constructor Studio terms and tools: Constructor Studio, `cfs`, `/cf`, `/cf-studio`, and `/cf-*`. Learners practice the command vocabulary they will use in real projects.

#### Lessons and Checkpoints

- 2.2.1 Product name: Constructor Studio
- 2.2.2 CLI tool name: `cfs`
- 2.2.3 Root skill and activation: `/cf`
- 2.2.4 Studio command surface: `/cf-studio`
- 2.2.5 Core skills: `/cf-plan`, `/cf-write-docs`, `/cf-coding`, `/cf-explore`
- 2.2.6 Kit workflow commands: `/cf-{kit}-{name}`
- 2.2.7 Naming practice: choosing the right command form

### 2.3 Course Project and Assessment Model

Description: The course uses one running repository project so each concept becomes a practical artifact, command, or workflow result. Assessments emphasize repeatable operation, traceability, validation, and review readiness.

#### Lessons and Checkpoints

- 2.3.1 The running course repository
- 2.3.2 Test application Git repository with full app source code and configured Constructor Studio (TODO: add exact repository link)
- 2.3.3 What learners will build
- 2.3.4 Labs, checkpoints, and capstone rules
- 2.3.5 Evidence required for completion
- 2.3.6 Certification rubric overview

## 3. Foundation - Mental Model and Operating Principles

Description: This part explains what Constructor Studio is, where it fits around AI coding tools, and why the system uses artifacts, workflows, validation, and traceability instead of one long prompt.

### 3.1 What Constructor Studio Is

Description: Learners build a simple mental model: Constructor Studio is the workflow, context, and validation layer around an AI coding tool. It helps teams keep requirements, design, plans, and code aligned. This module builds on the audience, problem, and solution framing established in Part 1.

#### Lessons and Checkpoints

- 3.1.1 The core problem: AI accelerates development but does not guarantee fidelity (see Part 1)
- 3.1.2 Why Claude Code or OpenAI Codex alone is not enough for controlled delivery
- 3.1.3 Why an agentic IDE alone is not enough for end-to-end traceability and validation
- 3.1.4 Constructor Studio as a repo-attached Spec Driven Development system
- 3.1.5 Constructor Studio works with Claude Code, Codex, Cursor, Windsurf, and other agentic tools
- 3.1.6 Inspectable artifacts versus chat memory
- 3.1.7 Deterministic checks versus model reasoning
- 3.1.8 Checkpoint: explain the system in one paragraph

### 3.2 Actors and Responsibilities

Description: This module separates the responsibilities of the human, AI coding tool, agent, Constructor Studio, CLI, and CI pipeline. The goal is to prevent learners from treating the system as either magic automation or just documentation.

#### Lessons and Checkpoints

- 3.2.1 Human owner and approval authority
- 3.2.2 AI coding tool as the host environment
- 3.2.3 Agent as the reasoning and writing executor
- 3.2.4 Constructor Studio as workflow and validation control
- 3.2.5 `cfs` as deterministic local and CI interface
- 3.2.6 Checkpoint: assign responsibilities for a change request

### 3.3 The Artifact-First Delivery Model

Description: Learners see how requirements, design, decomposition, features, plans, implementation, and review outputs form a delivery chain. This module introduces stable IDs and links without going deep into validation internals yet.

#### Lessons and Checkpoints

- 3.3.1 Why artifacts exist
- 3.3.2 Requirement to design to plan to code
- 3.3.3 Stable identifiers and references
- 3.3.4 Drift as a visible signal
- 3.3.5 Lab: read a simple evidence chain

### 3.4 Fit and Non-Fit

Description: This module teaches when Constructor Studio is worth the overhead and when a normal edit is better. Learners practice choosing based on risk, ambiguity, review pressure, and traceability needs.

#### Lessons and Checkpoints

- 3.4.1 Good fit: risky, multi-step, review-sensitive work
- 3.4.2 Good fit: brownfield understanding before editing
- 3.4.3 Non-fit: tiny edits and throwaway spikes
- 3.4.4 Tradeoff: more structure for more control
- 3.4.5 Checkpoint: classify ten work requests

### 3.5 Core Vocabulary

Description: This module establishes the language used across the rest of the course. Terms are defined as the normal Constructor Studio vocabulary learners will use in daily work.

#### Lessons and Checkpoints

- 3.5.1 Project, setup directory, and Studio installation
- 3.5.2 Artifacts, systems, codebases, and registries
- 3.5.3 Workflows, skills, commands, and generated integrations
- 3.5.4 Kits, templates, rules, checklists, and examples
- 3.5.5 Workspace sources and cross-repo resolution
- 3.5.6 Language complexity setting and output language control
- 3.5.7 Checkpoint: vocabulary matching exercise

### 3.6 Comparing SDD Approaches and Tools

Description: This module helps learners distinguish between prompt-first, template-first, and artifact-first Spec Driven Development approaches. It clarifies how Constructor Studio relates to tools such as OpenSpec and BMAD, and why different SDD tools optimize for different stages of the delivery process.

#### Lessons and Checkpoints

- 3.6.1 What Spec Driven Development means in practice
- 3.6.2 Prompt-first versus template-first versus artifact-first SDD
- 3.6.3 Generation-focused versus validation-focused SDD systems
- 3.6.4 OpenSpec, BMAD, and Constructor Studio: differences in scope and control surface
- 3.6.5 IDE-native versus repo-attached SDD workflows
- 3.6.6 Checkpoint: choose the right SDD approach for a project context

## 4. Getting Started - Installation, Setup, and First Use

Description: This part takes a new learner from no installed tool to a working repository with generated agent integrations and a first useful workflow run.

### 4.1 Local Prerequisites

Description: Learners prepare the development environment required for Constructor Studio. The module keeps the setup practical and focuses only on what is needed to run the system.

#### Lessons and Checkpoints

- 4.1.1 Required tools: Python, Git, `pipx`, and AI coding host
- 4.1.2 Optional tools: GitHub CLI for PR workflows
- 4.1.3 Supported hosts and practical differences
- 4.1.4 Environment checks before installation
- 4.1.5 Running `cfs doctor` to verify environment health
- 4.1.6 Lab: verify prerequisites

### 4.2 Installing the CLI

Description: This module introduces `cfs` as the Constructor Studio CLI. Learners verify installation before touching a project.

#### Lessons and Checkpoints

- 4.2.1 Installing Constructor Studio via `cfs`
- 4.2.2 Verifying the installed executable
- 4.2.3 Checking CLI version
- 4.2.4 Understanding global proxy behavior
- 4.2.5 Troubleshooting PATH issues
- 4.2.6 Lab: install and verify the CLI

### 4.3 Initializing a Repository

Description: Learners initialize Constructor Studio in a repository and inspect the generated surfaces. The focus is on what gets created, what is generated, and what the user owns.

#### Lessons and Checkpoints

- 4.3.1 Running `cfs init`
- 4.3.2 Configuring Constructor Studio for your current repository
- 4.3.3 Generated versus user-editable files
- 4.3.4 Project config and setup directory layout
- 4.3.5 Root AGENTS navigation block
- 4.3.6 Lab: initialize and configure the current repository

### 4.4 Generating Host Integrations

Description: This module explains how Constructor Studio projects workflows into AI coding tools. Learners regenerate integrations and learn when regeneration is required.

#### Lessons and Checkpoints

- 4.4.1 What `cfs generate-agents` creates
- 4.4.2 Host integration directories
- 4.4.3 Slash commands, skills, prompts, and subagents
- 4.4.4 Regenerating after setup changes
- 4.4.5 Lab: generate integrations for one host

### 4.5 Activating Constructor Studio in Chat

Description: Learners activate the system from their AI coding tool and understand the difference between terminal commands and chat commands. This module establishes the core operating rule for the rest of the course.

#### Lessons and Checkpoints

- 4.5.1 Terminal: use `cfs`
- 4.5.2 Chat: use `/cf` and workflow commands
- 4.5.3 Activating Constructor Studio with `/cf on`
- 4.5.4 Confirming activation
- 4.5.5 Common activation failures
- 4.5.6 Lab: activate and run a first analysis prompt

### 4.6 First Five-Minute Trial

Description: Learners perform a small but meaningful first run without overloading the system. The goal is to experience planning or analysis before attempting generation.

#### Lessons and Checkpoints

- 4.6.1 Why first use should often be `/cf-explore` or `/cf-plan`
- 4.6.2 First prompt patterns that work
- 4.6.3 Reading the response structure
- 4.6.4 Deciding the next action
- 4.6.5 Lab: run the first guided workflow

## 5. Operator Track - Daily Workflows

Description: This part teaches the core workflows an operator uses every day: plan, write documents, implement, explore, validate, review, and iterate.

### 5.1 Workflow Selection

Description: Learners learn to choose the right workflow before asking the agent to act. The module emphasizes task shape, risk, context size, and expected output.

#### Lessons and Checkpoints

- 5.1.1 `/cf-plan` for large or risky work
- 5.1.2 `/cf-write-docs` and `/cf-sdlc-doc-*` for creating or changing artifacts
- 5.1.3 `/cf-coding`, `/cf-sdlc-implement`, and review skills for code changes, validation, and inspection
- 5.1.4 `/cf-studio` as the broader command surface
- 5.1.5 Kit-specific commands with `/cf-{kit}-{name}`
- 5.1.6 Checkpoint: choose a workflow for each scenario

### 5.2 Planning Work with `/cf-plan`

Description: This module teaches how to decompose work into phase files and checkpoints. Learners understand that planning produces execution artifacts rather than doing the underlying implementation.

#### Lessons and Checkpoints

- 5.2.1 When planning is mandatory
- 5.2.2 Plan scope, target, and input signature
- 5.2.3 Phase files and compilation briefs
- 5.2.4 Plan lifecycle choices
- 5.2.5 Execution readiness and validation
- 5.2.6 Lab: create a plan for a medium-risk change

### 5.3 Writing Artifacts with `/cf-write-docs` and `/cf-sdlc-doc-*`

Description: Learners create and update structured artifacts using templates, examples, rules, and confirmation gates. The module focuses on bounded document authoring rather than free-form writing.

#### Lessons and Checkpoints

- 5.3.1 Generation inputs and required context
- 5.3.2 Template-driven artifact writing
- 5.3.3 Example-guided style and quality
- 5.3.4 Confirming proposed inputs before writing
- 5.3.5 Post-write validation and review
- 5.3.6 Lab: generate a small artifact

### 5.4 Implementing Code from Approved Artifacts

Description: This module teaches how code changes are constrained by approved requirements, designs, or feature specs. Learners preserve traceability while making practical implementation changes.

#### Lessons and Checkpoints

- 5.4.1 Source artifact selection
- 5.4.2 Extracting implementation requirements
- 5.4.3 Proposed approach review
- 5.4.4 Traceability markers in code
- 5.4.5 Validation after implementation
- 5.4.6 Lab: implement a bounded feature from a spec

### 5.5 Reviewing Artifacts with Dedicated Review Skills

Description: Learners validate artifacts through deterministic gates and semantic review. The module shows why a validator pass alone is not the same as a complete review, and routes review work to dedicated skills such as `/cf-write-docs`, `/cf-sdlc-pr-review`, and `/cf-sdlc-change-impact-analysis`.

#### Lessons and Checkpoints

- 5.5.1 Full analysis versus semantic-only analysis
- 5.5.2 File existence and registration checks
- 5.5.3 Deterministic validation gate
- 5.5.4 Semantic checklist review
- 5.5.5 Fix prompt and plan prompt outputs
- 5.5.6 Lab: analyze an artifact and triage findings

### 5.6 Reviewing Code and Implementation Behavior

Description: This module teaches code review through Constructor Studio's analysis model. Learners focus on defects, regressions, missing tests, and gaps against approved artifacts.

#### Lessons and Checkpoints

- 5.6.1 Code mode and design requirements
- 5.6.2 Bug-finding methodology
- 5.6.3 Missing or stale traceability markers
- 5.6.4 Review output severity and actionability
- 5.6.5 Lab: review a changed module against a feature

### 5.7 Validate-Review-Fix Loop

Description: Learners practice the standard loop: generate or implement, validate, review, fix, and validate again. This module makes iteration explicit instead of treating the first model output as done.

#### Lessons and Checkpoints

- 5.7.1 Why first-pass output is not final
- 5.7.2 Local validation before review
- 5.7.3 Separating generation and review contexts
- 5.7.4 Fixing deterministic failures
- 5.7.5 Fixing semantic findings
- 5.7.6 Lab: complete a full loop

### 5.8 Prompt Patterns for Operators

Description: This module gives learners practical prompt shapes for real work without turning the course into a prompt library. The focus is on bounded, reviewable requests.

#### Lessons and Checkpoints

- 5.8.1 Structured generation prompts
- 5.8.2 Structured analysis prompts
- 5.8.3 Planning prompts
- 5.8.4 Brownfield understanding prompts
- 5.8.5 Context-bounded execution prompts
- 5.8.6 Checkpoint: rewrite weak prompts

### 5.9 How Constructor Studio Routes Workflows

Description: This module explains the Protocol Guard and execution protocol that determines which files the agent loads, how variables are resolved, and why specific rules and specs are matched for each request. Understanding this mechanism helps operators debug routing issues and predict agent behavior.

#### Lessons and Checkpoints

- 5.9.1 Protocol Guard purpose and load sequence
- 5.9.2 Variable resolution with `cfs info`
- 5.9.3 Registry understanding and target determination
- 5.9.4 WHEN-clause spec matching
- 5.9.5 Navigation rules: ALWAYS open, OPEN and follow
- 5.9.6 Debugging routing problems
- 5.9.7 Lab: trace how a workflow request is routed

## 6. Artifacts, Traceability, and Validation

Description: This part goes deeper into the core evidence model: artifact registries, IDs, references, validation, and code traceability.

### 6.1 Artifact Registry Fundamentals

Description: Learners understand how Constructor Studio discovers and registers artifacts. This module explains systems, artifact kinds, paths, codebases, and ignore rules.

#### Lessons and Checkpoints

- 6.1.1 Purpose of the artifact registry
- 6.1.2 Systems and artifact kinds
- 6.1.3 Artifact paths and autodetect rules
- 6.1.4 Codebase entries and ignore patterns
- 6.1.5 Lab: inspect an artifact registry

### 6.2 Stable IDs

Description: This module teaches the role of stable identifiers in traceable delivery. Learners define, reference, query, and validate IDs.

#### Lessons and Checkpoints

- 6.2.1 ID purpose and lifecycle
- 6.2.2 ID kinds and naming conventions
- 6.2.3 Versioned IDs
- 6.2.4 Finding definitions with `cfs where-defined`
- 6.2.5 Finding usage with `cfs where-used`
- 6.2.6 Lab: trace an ID across documents

### 6.3 Cross-Artifact Links

Description: Learners connect requirements, design, decomposition, features, and implementation evidence. The module focuses on alignment and drift detection.

#### Lessons and Checkpoints

- 6.3.1 Outgoing references
- 6.3.2 Incoming references
- 6.3.3 Required links and coverage expectations
- 6.3.4 Broken links and orphaned IDs
- 6.3.5 Lab: repair a broken reference chain

### 6.4 Code Traceability

Description: This module connects artifacts to implementation through code markers and codebase scanning. Learners learn what traceability can show and what it cannot prove.

#### Lessons and Checkpoints

- 6.4.1 Code markers and implementation evidence
- 6.4.2 Marker naming policy
- 6.4.3 FULL versus DOCS-ONLY traceability
- 6.4.4 Marker recovery
- 6.4.5 Lab: add missing implementation markers

### 6.5 Deterministic Validation

Description: Learners run `cfs validate` and interpret results. The module explains exit codes, JSON output, and the difference between deterministic failure and semantic concern.

#### Lessons and Checkpoints

- 6.5.1 Validation scope
- 6.5.2 Exit codes and failure classes
- 6.5.3 JSON output and stderr messages
- 6.5.4 Local-only validation
- 6.5.5 CI validation basics
- 6.5.6 Lab: run and interpret validation

### 6.6 Validation Limits

Description: This module sets realistic expectations. Constructor Studio can expose missing, broken, or inconsistent evidence, but it does not prove business adequacy or implementation correctness.

#### Lessons and Checkpoints

- 6.6.1 What deterministic checks can prove
- 6.6.2 What semantic review must still cover
- 6.6.3 What human review must still decide
- 6.6.4 Avoiding false confidence
- 6.6.5 Checkpoint: classify validation claims

## 7. Advanced Operator Track - Brownfield, Workspaces, PRs, and Storytelling

Description: This part teaches advanced use in real teams: existing codebases, multi-repo workspaces, PR workflows, onboarding, and troubleshooting.

### 7.1 Brownfield Projects

Description: Learners use Constructor Studio in projects that already have code and inconsistent conventions. The module emphasizes understanding and auto-configuration before large edits.

#### Lessons and Checkpoints

- 7.1.1 Brownfield risks
- 7.1.2 Task-matched project rules
- 7.1.3 Auto-config purpose and outputs
- 7.1.4 When the agent offers auto-config: the brownfield detection gate
- 7.1.5 Reviewing and refining inferred rules
- 7.1.6 Re-running auto-config after project evolution
- 7.1.7 Lab: run auto-config and review inferred project rules

### 7.2 Large Task Handling

Description: This module teaches learners to avoid giant direct generation requests. They practice escalating to planning, chunking inputs, and keeping context boundaries healthy.

#### Lessons and Checkpoints

- 7.2.1 Context budget warnings
- 7.2.2 Raw input overflow
- 7.2.3 Phase boundaries and checkpoints
- 7.2.4 Resume after context loss
- 7.2.5 Lab: convert an oversized request into a plan

### 7.3 Multi-Repo Workspace Federation

Description: Learners connect multiple repositories into one reachable traceability surface. The module covers discovery, configuration, validation, and graceful degradation.

#### Lessons and Checkpoints

- 7.3.1 Workspace use cases
- 7.3.2 Source roles: artifacts, codebase, mixed, and support repos
- 7.3.3 Standalone versus inline workspace config
- 7.3.4 Cross-repo ID resolution
- 7.3.5 Missing source behavior
- 7.3.6 Lab: configure a two-repo workspace

### 7.4 Workspace Commands

Description: This module teaches the operational command set for workspaces. Learners inspect, add, sync, and validate workspace sources.

#### Lessons and Checkpoints

- 7.4.1 `cfs workspace-init`
- 7.4.2 `cfs workspace-add`
- 7.4.3 `cfs workspace-info`
- 7.4.4 `cfs workspace-sync`
- 7.4.5 Cross-repo `list-ids`, `where-defined`, and `where-used`
- 7.4.6 Lab: inspect cross-repo traceability

### 7.5 PR Review Workflows

Description: Learners run structured PR review and status workflows where supported by kits and GitHub tooling. The focus is review quality, checklists, unresolved comments, and status reporting.

#### Lessons and Checkpoints

- 7.5.1 PR review prerequisites
- 7.5.2 `/cf-sdlc-pr-review` as a kit workflow pattern
- 7.5.3 `/cf-sdlc-pr-status` as a kit workflow pattern
- 7.5.4 Review findings and severity
- 7.5.5 Resolved comment audit
- 7.5.6 Lab: produce a PR review report

### 7.6 Storytelling and Onboarding Workflows

Description: This module teaches the explain and onboarding modes for pedagogical walkthroughs. Learners use them to understand artifacts, PRs, and codebase conventions without turning analysis into a one-shot summary.

#### Lessons and Checkpoints

- 7.6.1 Storytelling intent and mode selection
- 7.6.2 Presentation mode
- 7.6.3 Review mode
- 7.6.4 Onboarding mode
- 7.6.5 Socratic and quiz mode
- 7.6.6 Explain package export
- 7.6.7 Lab: create an onboarding walkthrough

### 7.7 Host Tool Strategy

Description: Learners compare practical behavior across supported AI coding hosts. The module focuses on subagents, review isolation, model selection, and manual separation when host support is limited.

#### Lessons and Checkpoints

- 7.7.1 Claude Code strategy
- 7.7.2 Cursor strategy
- 7.7.3 GitHub Copilot strategy
- 7.7.4 OpenAI Codex strategy
- 7.7.5 Windsurf strategy
- 7.7.6 Checkpoint: choose a host strategy for a team

### 7.8 Troubleshooting and Recovery

Description: This module covers common setup, activation, validation, and workflow problems. Learners practice diagnosing issues without weakening the process.

#### Lessons and Checkpoints

- 7.8.1 CLI not found
- 7.8.2 Generated integrations not picked up
- 7.8.3 Wrong project root
- 7.8.4 Missing or stale AGENTS block
- 7.8.5 Validation failure triage
- 7.8.6 Plan recovery after interruption
- 7.8.7 Using `cfs doctor` for environment diagnosis
- 7.8.8 Lab: diagnose a broken setup

## 8. Kit and Extension Author Track - Building the System Surface

Description: This part teaches maintainers how to extend Constructor Studio with kits, artifacts, rules, workflows, skills, subagents, and host integrations.

### 8.1 Kit Architecture

Description: Learners understand kits as domain-specific packages that extend the core platform. The module separates core responsibilities from kit responsibilities.

#### Lessons and Checkpoints

- 8.1.1 Core platform versus kits
- 8.1.2 Kit lifecycle: install, update, move, validate
- 8.1.3 Kit files and ownership
- 8.1.4 User-editable kit content
- 8.1.5 SDLC kit architecture
- 8.1.6 Checkpoint: identify core versus kit concerns

### 8.2 Kit Manifest and Resources

Description: This module teaches manifest-driven kit installation and resource binding. Learners see how relocatable kit resources are declared, copied, updated, and resolved.

#### Lessons and Checkpoints

- 8.2.1 Manifest purpose
- 8.2.2 Resource identifiers and default paths
- 8.2.3 User-modifiable resources
- 8.2.4 Resource binding in config
- 8.2.5 Existing kit resource transition
- 8.2.6 Lab: inspect a kit manifest

### 8.3 Artifact Kind Design

Description: Learners design an artifact kind with a template, rules, examples, and checklist. The module teaches how to make generation and analysis reliable.

#### Lessons and Checkpoints

- 8.3.1 Artifact kind purpose
- 8.3.2 Template structure
- 8.3.3 Example quality
- 8.3.4 Checklist scope
- 8.3.5 Rules and dependencies
- 8.3.6 Lab: draft an artifact kind package

### 8.4 Rules and Checklists

Description: This module goes deeper into the authoring rules that drive generation, analysis, and planning. Learners write rules that are specific enough for agents to follow and validators to support.

#### Lessons and Checkpoints

- 8.4.1 Generation-phase dependencies
- 8.4.2 Validation-phase dependencies
- 8.4.3 Mandatory versus optional checks
- 8.4.4 Interaction points and confirmation gates
- 8.4.5 Avoiding vague author instructions
- 8.4.6 Lab: strengthen a weak checklist

### 8.5 Behavior Description Language (CDSL)

Description: This module teaches the Constructor DSL (CDSL) used for writing algorithms, actor flows, and state machines in DESIGN and FEATURE artifacts. CDSL is a plain-English behavior description language with structured control flow keywords, mandatory phase tokens, instruction IDs, and implementation checkboxes.

#### Lessons and Checkpoints

- 8.5.1 CDSL purpose and when to use it
- 8.5.2 Basic format: numbered lists, bold keywords, plain English
- 8.5.3 Control flow keywords: IF, FOR EACH, WHILE, TRY/CATCH, PARALLEL, MATCH
- 8.5.4 Phase tokens, instruction IDs, and implementation checkboxes
- 8.5.5 State machines in CDSL
- 8.5.6 Validation rules: required and prohibited patterns
- 8.5.7 Lab: write a behavior specification in CDSL

### 8.6 Workflow Authoring

Description: Learners create and maintain workflows that route user intent into reliable agent behavior. The module emphasizes navigation rules, fail-stop gates, and context hygiene.

#### Lessons and Checkpoints

- 8.6.1 Workflow purpose and frontmatter
- 8.6.2 ALWAYS open and follow rules
- 8.6.3 WHEN conditions
- 8.6.4 Phase structure and gates
- 8.6.5 Output contracts
- 8.6.6 Lab: design a small kit workflow

### 8.7 Skill Authoring

Description: This module teaches skills as host-visible entry points that route into workflows and methods. Learners write concise skill descriptions that trigger correctly.

#### Lessons and Checkpoints

- 8.7.1 Skill role in Constructor Studio
- 8.7.2 `SKILL.md` structure
- 8.7.3 Description quality and trigger behavior
- 8.7.4 Generated versus hand-maintained skills
- 8.7.5 Lab: write a skill entry point

### 8.8 Command Naming for Kits

Description: Learners apply the Constructor Studio command naming model to kit workflows. The module standardizes names such as `/cf-{kit}-{name}` and teaches how to keep command sets clear.

#### Lessons and Checkpoints

- 8.8.1 Core command namespace
- 8.8.2 Kit command namespace
- 8.8.3 Naming collisions and reserved names
- 8.8.4 Host-specific aliases
- 8.8.5 Lab: name a kit command set

### 8.9 Subagents and Delegation

Description: This module teaches when and how specialized agents support planning, phase compilation, phase execution, PR review, and large change orchestration. Learners understand host support differences and fallback behavior.

#### Lessons and Checkpoints

- 8.9.1 Subagent responsibilities
- 8.9.2 Phase compiler agent
- 8.9.3 Phase runner agent
- 8.9.4 PR review agent
- 8.9.5 Delegation and RalphEx-style orchestration
- 8.9.6 Lab: design a subagent role

### 8.10 Project-Level Extensibility

Description: Learners extend behavior inside a single project without changing the core platform. This module covers local rules, workflows, commands, and host-specific generated surfaces.

#### Lessons and Checkpoints

- 8.10.1 Project rules
- 8.10.2 Project specs
- 8.10.3 Local workflows and commands
- 8.10.4 Generated host integrations
- 8.10.5 Governance for local extensions
- 8.10.6 Lab: add a project-specific rule

### 8.11 Testing and Validating Extensions

Description: This module teaches authors to validate extension behavior before publishing or rolling it into team use. Learners combine deterministic checks, semantic reviews, and fixture projects.

#### Lessons and Checkpoints

- 8.11.1 Structural validation for kits
- 8.11.2 Using `cfs self-check` to validate kit examples against templates
- 8.11.3 Fixture projects
- 8.11.4 Prompt and workflow reviews
- 8.11.5 Regression tests for generated surfaces
- 8.11.6 Release checklist for kit changes
- 8.11.7 Lab: validate a custom kit slice

## 9. Governance, CI, and Team Adoption

Description: This part teaches teams how to adopt Constructor Studio without turning it into bureaucracy. The focus is practical governance, CI, review expectations, and maintainable operating habits.

### 9.1 Team Operating Model

Description: Learners define how Constructor Studio fits into team delivery. The module covers ownership, review gates, conventions, and what should be enforced versus documented.

#### Lessons and Checkpoints

- 9.1.1 Who owns artifacts
- 9.1.2 Who owns rules and kits
- 9.1.3 When plans are required
- 9.1.4 When validation is required
- 9.1.5 Human approval boundaries
- 9.1.6 Checkpoint: draft a team operating policy

### 9.2 CI Integration

Description: This module teaches how deterministic checks move from local development into CI. Learners understand which commands belong in CI and how to treat failures.

#### Lessons and Checkpoints

- 9.2.1 Local checks before PR
- 9.2.2 `cfs validate` in CI
- 9.2.3 Local-only versus workspace validation
- 9.2.4 Exit code handling
- 9.2.5 Reporting validation results
- 9.2.6 Lab: design a CI validation gate

### 9.3 Review Readiness

Description: Learners prepare changes so reviewers can see scope, intent, evidence, validation, and remaining risk. The module turns Constructor Studio outputs into a review package.

#### Lessons and Checkpoints

- 9.3.1 What reviewers need
- 9.3.2 Evidence chain summary
- 9.3.3 Validation result summary
- 9.3.4 Known risks and open questions
- 9.3.5 PR review handoff
- 9.3.6 Lab: assemble a review-ready change summary

### 9.4 Version and Update Management

Description: This module teaches how teams update the CLI, project-installed core, generated integrations, and kits. Learners handle version notices, diffs, and schema changes.

#### Lessons and Checkpoints

- 9.4.1 Global cache and project-installed core
- 9.4.2 Version notices
- 9.4.3 `cfs update`
- 9.4.4 Kit update diffs
- 9.4.5 Regenerating integrations after update
- 9.4.6 Lab: plan a safe update

### 9.5 Adoption Patterns and Anti-Patterns

Description: This module helps teams avoid both underuse and overuse. Learners identify where Constructor Studio adds value and where it becomes unnecessary overhead.

#### Lessons and Checkpoints

- 9.5.1 Good first team use cases
- 9.5.2 Bad first team use cases
- 9.5.3 Avoiding giant prompt culture
- 9.5.4 Avoiding false proof claims
- 9.5.5 Keeping artifacts alive
- 9.5.6 Checkpoint: adoption scenario review

## 10. Capstone and Certification

Description: This part turns the course into an end-to-end proof of skill. Learners complete a realistic delivery scenario and produce artifacts, plans, implementation evidence, validation output, review notes, and an extension slice.

### 10.1 Capstone Scenario

Description: Learners receive a realistic brownfield or multi-repo change request. The scenario requires both operator skills and, for advanced certification, a small extension or kit workflow.

#### Lessons and Checkpoints

- 10.1.1 Scenario brief
- 10.1.2 Repository setup
- 10.1.3 Success criteria
- 10.1.4 Constraints and allowed shortcuts
- 10.1.5 Checkpoint: capstone readiness review

### 10.2 Operator Capstone Path

Description: The operator path proves daily use competence. Learners initialize or inspect setup, choose workflows, produce or update artifacts, plan the change, implement, validate, analyze, and prepare review evidence.

#### Lessons and Checkpoints

- 10.2.1 Environment and setup evidence
- 10.2.2 Workflow selection rationale
- 10.2.3 Artifact generation or update
- 10.2.4 Execution plan
- 10.2.5 Implementation with traceability
- 10.2.6 Validation and review loop
- 10.2.7 Final review package

### 10.3 Author Capstone Path

Description: The author path adds an extension requirement on top of operator competence. Learners design a small kit artifact kind, workflow, skill, or project-level rule and validate that it works.

#### Lessons and Checkpoints

- 10.3.1 Extension concept
- 10.3.2 Artifact kind or workflow design
- 10.3.3 Skill or command entry point
- 10.3.4 Generated host integration expectation
- 10.3.5 Extension validation
- 10.3.6 Final authoring review

### 10.4 Certification Review

Description: This module defines the evaluation rubric and evidence package. Learners are assessed on correctness, traceability, workflow choice, validation discipline, and clarity of handoff.

#### Lessons and Checkpoints

- 10.4.1 Operator rubric
- 10.4.2 Author rubric
- 10.4.3 Required evidence files
- 10.4.4 Common failure modes
- 10.4.5 Remediation path
- 10.4.6 Final certification checklist

## Appendix A. Command and Terminology Reference

Description: This appendix collects the Constructor Studio names used throughout the course. It is a quick reference for product terms, terminal commands, chat commands, and kit command naming.

### A.1 Product and CLI Names

Description: This mapping covers product and terminal interface naming.

#### Reference

- Product name: Constructor Studio
- CLI: `cfs`
- Project setup directory: `.cf-studio/`
- Root chat command or skill: `/cf`
- Studio command surface: `/cf-studio`

### A.2 Chat and Workflow Names

Description: This mapping covers AI coding tool commands and skills.

#### Reference

- Root command or skill: `/cf`
- Studio surface: `/cf-studio`
- Plan workflow: `/cf-plan`
- Document-writing skills: `/cf-write-docs`, `/cf-sdlc-doc-prd`, `/cf-sdlc-doc-design`, `/cf-sdlc-doc-adr`
- Code implementation skills: `/cf-coding`, `/cf-sdlc-implement`
- Review and exploration skills: `/cf-explore`, `/cf-sdlc-pr-review`, `/cf-sdlc-change-impact-analysis`
- Kit workflow pattern: `/cf-{kit}-{name}`

### A.3 Course Writing Rules

Description: These rules keep lesson text consistent and prevent mixed terminology from confusing new learners.

#### Rules

- Use Constructor Studio as the primary product name.
- Use `cfs` for terminal examples.
- Use `/cf-*` for chat commands.
- Use `/cf-{kit}-{name}` for kit workflow examples.
- Keep internal implementation names out of learner-facing lesson titles.

## Appendix B. Learner Journey Map

Description: This appendix summarizes recommended completion paths for different learners.

### B.1 New Operator Path

Description: This path is for developers, technical leads, and product-minded engineers who want to use Constructor Studio in daily project work.

#### Recommended Sequence

- Complete Part 2: Course Frame
- Complete Part 3: Foundation
- Complete Part 4: Getting Started
- Complete Part 5: Operator Track
- Complete Part 6: Artifacts, Traceability, and Validation
- Complete Part 7 modules 7.1 through 7.8 as needed
- Complete Part 8 modules 8.1 through 8.6
- Complete Part 10.2 Operator Capstone Path

### B.2 Kit and Extension Author Path

Description: This path is for maintainers who design kits, workflows, skills, and project extensions. It assumes the learner has completed the operator foundations first.

#### Recommended Sequence

- Complete all New Operator Path modules
- Complete Part 8: Kit and Extension Author Track
- Complete Part 10.3 Author Capstone Path
- Complete Part 10.4 Certification Review

### B.3 Team Adoption Path

Description: This path is for technical leads planning rollout across a team or workspace. It prioritizes operating model, validation, review readiness, and adoption discipline.

#### Recommended Sequence

- Complete Part 2: Foundation
- Complete Part 3: Getting Started
- Complete Part 4 modules 4.1, 4.2, 4.5, and 4.7
- Complete Part 5 modules 5.1 through 5.6
- Complete Part 6 modules 6.3, 6.4, 6.5, and 6.8
- Complete Part 8: Governance, CI, and Team Adoption
- Review Part 9 certification rubric for internal enablement
