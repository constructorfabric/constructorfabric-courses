# Constructor Studio v1 Overview Scripts for Video Production

<!-- toc -->

- [Production Framing](#production-framing)
- [Overview 1. Constructor Studio](#overview-1-constructor-studio)
  - [Story Goal](#story-goal)
  - [Narrator Script and Visual Direction](#narrator-script-and-visual-direction)
- [Overview 2. Constructor Studio for CTO and R&D Leaders](#overview-2-constructor-studio-for-cto-and-rd-leaders)
  - [Story Goal](#story-goal-1)
  - [Narrator Script and Visual Direction](#narrator-script-and-visual-direction-1)
- [Overview 3. Constructor Studio for Product Managers](#overview-3-constructor-studio-for-product-managers)
  - [Story Goal](#story-goal-2)
  - [Narrator Script and Visual Direction](#narrator-script-and-visual-direction-2)
- [Overview 4. Constructor Studio for Architects](#overview-4-constructor-studio-for-architects)
  - [Story Goal](#story-goal-3)
  - [Narrator Script and Visual Direction](#narrator-script-and-visual-direction-3)
- [Overview 5. Constructor Studio for DevLeads and Developers](#overview-5-constructor-studio-for-devleads-and-developers)
  - [Story Goal](#story-goal-4)
  - [Narrator Script and Visual Direction](#narrator-script-and-visual-direction-4)
- [Overview 6. Constructor Studio for QA Engineers](#overview-6-constructor-studio-for-qa-engineers)
  - [Story Goal](#story-goal-5)
  - [Narrator Script and Visual Direction](#narrator-script-and-visual-direction-5)
- [Closing Note for Production Team](#closing-note-for-production-team)

<!-- /toc -->

## Production Framing

This document is a script pack for six 5-minute overview videos about Constructor Studio v1. Each video should feel like a simple story for a wide audience: first the problem, then the solution, then how the solution works.

Use clear on-screen text throughout, not minimal text only. Let the narrator explain, and let text, subtitles, diagrams, and animation reinforce the same point so learners can hear and see the structure at the same time.

Default story spine for every overview:

1. Problem: AI tools now help teams generate much more code, markdown, specs, tasks, tests, and documentation. In mid-size and large organizations, the number of files and handoffs grows quickly. Existing tools can help generate even more, but they do not automatically give the organization control.
2. Solution: Constructor Studio is a customizable team environment for organizing AI-assisted software delivery across Product Managers, Architects, DevLeads, Developers, and QA engineers.
3. How it works: Studio routes work through shared workflows, file-backed evidence, role-specific skills, repeatable validation, and traceability between documents, code, and tests.

Studio should be presented as covering the full software lifecycle: Plan, Build, and Operate.

- Plan: intent, vision, discovery, strategy, definition.
- Build: architecture, construction, validation, release.
- Operate: operations, support, intelligence, optimization.
- Required on-screen lifecycle line or diagram in every overview: Intent -> Vision -> Discover -> Define -> Design -> Build -> Validate -> Release -> Operate -> Support -> Learn -> Evolve.

Keep technical names late in the story. Start with the organizational pain, not with commands or internal mechanics.

Learner-facing terms that can appear when needed:

- `cfs` for terminal setup, validation, and project operations.
- `cf` for invoking Studio workflows in the AI coding tool.
- Concrete skills such as `cf-write-docs`, `cf-brainstorm`, `cf-explore`, `cf-explain`, `cf-sdlc-doc-prd`, `cf-sdlc-doc-design`, `cf-sdlc-doc-adr`, `cf-sdlc-implement`, `cf-sdlc-reverse-engineer`, `cf-sdlc-change-impact-analysis`, and `cf-coding`.

Do not mention router-level workflow names in learner-facing video scripts.

---

## Overview 1. Constructor Studio

### Story Goal

Explain why Constructor Studio was created, what goals it serves, and why teams and organizations need it beyond individual AI prompting.

### Narrator Script and Visual Direction

| Time | Narrator Script | Animation / Visual Direction | On-Screen Text |
|---|---|---|---|
| 0:00-0:35 | Modern AI tools give software teams a real productivity boost. They help write code, create markdown files, draft specs, generate tests, and explain unfamiliar systems much faster than before. | Show a team using AI tools. Code files, markdown docs, tasks, and tests appear rapidly around them. | AI makes more |
| 0:35-1:10 | But that boost creates a new problem. In a growing organization, the number of generated files and decisions can explode. Requirements drift. Design docs become stale. Tests stop matching intent. Code changes are hard to connect back to why they exist. | The generated files spread into disconnected clusters. Some links fade, some files conflict, some are marked incomplete. | More output, less control |
| 1:10-1:45 | Tools like OpenSpec and similar systems can help teams produce structured specs. That is useful. But generating more documents is not the same as keeping an organization aligned, consistent, and reviewable across teams. | Show a “generate specs” machine producing clean documents, then zoom out to messy handoffs between PM, architecture, development, and QA. | Generation is not governance |
| 1:45-2:20 | Constructor Studio was created for that organizational layer. Its goals are to keep AI-assisted delivery connected, reviewable, and adaptable across teams, so product work, architecture work, coding work, and QA work do not drift apart. | The scattered files move into one shared delivery map with role lanes and connecting lines. | Created for connected delivery |
| 2:20-3:05 | Studio is not only for one person writing better prompts. It is for collaboration between roles and between teams across the full software lifecycle. Product Managers shape requirements. Architects turn intent into decisions and design. Developers implement from approved context. QA checks behavior against traceable evidence. | PM, Architect, Developer, and QA lanes connect through shared files, then expand into lifecycle phases. | Teams across the lifecycle |
| 3:05-3:45 | The basic idea is simple: work is routed into the right workflow, with the right context, and with checks that make the result easier to inspect. Studio supports Plan, Build, and Operate as one delivery system: Intent -> Vision -> Discover -> Define -> Design -> Build -> Validate -> Release -> Operate -> Support -> Learn -> Evolve. | Scattered AI sessions across teams connect into a guided lifecycle path that spans planning, building, and operating. Keep the full lifecycle sequence visible on screen as a single line or clear diagram: Intent -> Vision -> Discover -> Define -> Design -> Build -> Validate -> Release -> Operate -> Support -> Learn -> Evolve. | Plan -> Build -> Operate; full lifecycle: Intent -> Vision -> Discover -> Define -> Design -> Build -> Validate -> Release -> Operate -> Support -> Learn -> Evolve |
| 3:45-4:25 | Studio works on top of the tools teams already like: Claude Code, GitHub Copilot, Cursor, and similar AI coding environments. It does not ask the organization to replace its technology stack just to get control over AI-assisted delivery. | Existing AI tools stay in place while Studio adds a workflow and evidence layer above them. | Keep your tools |
| 4:25-4:45 | Studio is also customizable. An organization can adapt templates, rules, workflows, validation, and codebase conventions instead of throwing away its existing process. The default SDLC kit gives teams a starting point they can adapt. | A default workflow adapts into several company-specific variants. | Fit your process |
| 4:45-5:00 | The outcome is control. AI can still help teams move faster, but the work becomes easier to connect, review, validate, and maintain. Constructor Studio turns AI-assisted output into a team delivery system. | End on a clean map where docs, code, tests, and review are connected. | Speed with control |

---

## Overview 2. Constructor Studio for CTO and R&D Leaders

### Story Goal

Help technical leaders decide whether Constructor Studio is a useful organizational control layer for AI-assisted delivery.

### Narrator Script and Visual Direction

| Time | Narrator Script | Animation / Visual Direction | On-Screen Text |
|---|---|---|---|
| 0:00-0:35 | For CTOs and R&D leaders, the main AI question is no longer “can developers generate code faster?” They can. The harder question is what happens when many teams generate code, documents, tests, and decisions faster at the same time. | Multiple teams generate artifacts in parallel. The volume rises quickly. | Scale changes the problem |
| 0:35-1:10 | Without a shared operating model, speed can turn into fragmentation. Teams may use different templates, lose decision history, skip review evidence, or produce documents that no longer match the codebase. | Show separate team islands with inconsistent docs and unclear handoffs. | Fragmentation risk |
| 1:10-1:45 | Constructor Studio is a proposed solution for that layer. It is an open-source, customizable environment that helps organize collaboration across Product Managers, Architects, Developers, DevLeads, and QA engineers. | The islands connect into one shared operating layer. | Shared operating layer |
| 1:45-2:25 | Studio differs from individual or project-centered specification tools because it is focused on organizational delivery control. The goal is not just to create one more spec. The goal is to keep intent, decisions, implementation, tests, and review evidence connected. | Compare “project spec” with “organization workflow”: the second shows cross-role links. | Beyond project specs |
| 2:25-3:05 | The mechanism is straightforward. Studio uses workflows and concrete skills for different kinds of work: brainstorming, exploration, Product Requirements Documents, design documents, Architecture Decision Records, implementation, reverse engineering, and change impact analysis. | Show each role lane using the workflow that fits its job: product requirements, design, code, tests, and review. | Workflows by role |
| 3:05-3:40 | Traceability is the control point. CPT IDs can connect documents and code so teams can reason about consistency. Validation can check structure, references, and configured rules. Human review remains the final authority. | A chain connects Product Requirements Document, DESIGN, FEATURE, code, tests, and approval. | Traceable evidence |
| 3:40-4:20 | Adoption does not require a process, tech stack, or favorite tools reset. Teams can start with the default SDLC kit and then customize document templates, checklists, workflows, and codebase rules to match existing governance. | Default kit expands into organization-specific process gates and existing tool icons stay in place. | Start standard, adapt |
| 4:20-5:00 | The leadership case is simple: Constructor Studio helps preserve the AI productivity boost while reducing the risk that generated code and documents become inconsistent, incomplete, or impossible to govern at scale. | End with a leader dashboard-style view of connected teams and artifacts. | AI speed, governed delivery |

---

## Overview 3. Constructor Studio for Product Managers

### Story Goal

Show Product Managers how Studio helps keep product intent clear, reviewable, and reusable downstream.

### Narrator Script and Visual Direction

| Time | Narrator Script | Animation / Visual Direction | On-Screen Text |
|---|---|---|---|
| 0:00-0:35 | Product work often starts as a conversation: a customer need, a stakeholder request, a feature idea, or a rough market assumption. AI can turn that into text very quickly. | A rough idea becomes a long generated document. | Ideas become text |
| 0:35-1:10 | The problem is that fast text can still be unclear. It may miss actors, constraints, edge cases, success criteria, or tradeoffs. When that unclear intent moves downstream, architects and developers fill gaps with assumptions. | Missing requirement fields create warning marks in later role lanes. | Fast text can drift |
| 1:10-1:45 | Constructor Studio helps Product Managers turn early intent into product requirements that are easier for the whole team to review and reuse. | Rough notes become a structured Product Requirements Document connected to architecture and QA. | Intent becomes reviewable |
| 1:45-2:25 | A PM can use `cf-brainstorm` to explore options before committing to scope. The point is not to get a pretty answer. The point is to surface alternatives, risks, missing questions, and decision criteria early. | Branching options appear, then collapse into a chosen direction with open questions. | Explore before scope |
| 2:25-3:05 | When the direction is ready, the Product Requirements Document workflow helps create or review requirements using structured expectations. `cf-write-docs` supports broader product writing when the document is less formal. | Two paths: formal Product Requirements Document and flexible product document. | Requirements and docs |
| 3:05-3:40 | Studio also helps with review and traceability. Requirements, and even specific paragraphs inside them, can use stable IDs that link to requirements defined elsewhere. That creates a graph of connected requirements that shapes the final product scope. | Requirement paragraphs receive stable IDs, then connect into a visible requirement graph. | Linked requirements |
| 3:40-4:25 | This improves collaboration because downstream teams receive something more stable than a chat transcript or an unstructured requirements document. Architects can see which requirements are covered by design, developers can see how they can be implemented, and QA can design tests against visible intent. | One Product Requirements Document feeds architecture, implementation, and QA lanes with trace links. | Stable handoff |
| 4:25-5:00 | Product Managers can also use phase tags to group requirement stories by delivery phase. Architects can see both the current scope and upcoming functionality, while development teams stay focused on the current delivery scope. When requirements move, Studio helps identify design or code that may need updates and gaps that need review. | End with requirement IDs grouped by phase, with changed items highlighting affected design and code nodes. | Intent that survives |

---

## Overview 4. Constructor Studio for Architects

### Story Goal

Show Architects how Studio helps turn requirements and existing codebase context into controlled design decisions.

### Narrator Script and Visual Direction

| Time | Narrator Script | Animation / Visual Direction | On-Screen Text |
|---|---|---|---|
| 0:00-0:35 | Architects often sit in the middle of the AI acceleration problem. Product intent is changing faster. Code is changing faster. Documentation is being generated faster. But architecture still needs coherence. | Product docs, code changes, and design notes move quickly around an architect. | Speed needs coherence |
| 0:35-1:10 | The risk is hidden drift. A Product Requirements Document may imply one architecture. Existing code may support another. A design document may become stale as implementation moves ahead. | Show Product Requirements Document, design, and code slowly separating from each other. | Hidden drift |
| 1:10-1:45 | Architecture is usually a tradeoff between business requirements, technical constraints, future extensibility, operational costs, security, and performance. Architects need many inputs in view before they can make the right decision. | Inputs from requirements, code, operations, security, and performance converge into one decision view. | Many inputs, one decision |
| 1:45-2:25 | Constructor Studio helps keep those inputs accessible. `cf-explore` can gather relevant requirements, existing design material, codebase context, and previous decisions before the architect writes or changes a design. | Repository and document sources are scanned, then summarized into an architecture context map. | Explore first |
| 2:25-3:05 | When the decision is still open, `cf-brainstorm` helps compare options and tradeoffs. Studio then supports consistent, well-informed decisions with architecture document templates, validation rules, reviewable structure, and links back to the source requirements. | Options are compared against requirement, cost, security, and performance criteria. | Tradeoffs made visible |
| 3:05-3:45 | Studio follows modern architecture documentation practice by separating design documents from Architecture Decision Records. Design documents define how the system should work. Architecture Decision Records capture why specific decisions were made and what consequences they create. | DESIGN and Architecture Decision Record streams split, then link back to the same requirement. | Design and rationale |
| 3:45-4:25 | That separation also helps AI work with a cleaner context. Code generation can focus on the pure design content needed for implementation, while architectural history and rationale remain linked as evidence without always entering the generation context. | The code-generation context receives DESIGN; linked Architecture Decision Records stay available as rationale. | Smaller AI context |
| 4:25-5:00 | In existing systems, Architects can use `cf-sdlc-reverse-engineer` to reconstruct design understanding from code and `cf-sdlc-change-impact-analysis` to estimate what a proposed change may touch across documents, components, and repositories. The result is faster collaboration with fewer invisible architecture gaps. | Brownfield code turns into a design map with cross-repository impact links. | Fewer invisible gaps |

---

## Overview 5. Constructor Studio for DevLeads and Developers

### Story Goal

Show DevLeads and Developers how Studio keeps implementation work bounded, traceable, and easier to review.

### Narrator Script and Visual Direction

| Time | Narrator Script | Animation / Visual Direction | On-Screen Text |
|---|---|---|---|
| 0:00-0:35 | Developers feel the AI boost directly. Code can be generated faster. Tests can be drafted faster. Bug explanations can arrive faster. But faster editing can also create faster confusion. | Code, tests, and fixes appear quickly in an editor. Some lose links to requirements. | Faster code, faster confusion |
| 0:35-1:10 | The problem is not that AI writes code. The problem is code without enough context: unclear requirement links, missing design decisions, weak tests, or changes that reviewers cannot trace back to intent. | A pull request appears with unanswered questions around it. | Context is the bottleneck |
| 1:10-1:45 | Constructor Studio helps developers start from approved inputs instead of an isolated AI answer or a loose ticket note. Work can begin from Product Requirements Document, design, Architecture Decision Record, or feature artifacts that explain why the change exists. | Editor opens next to linked FEATURE and DESIGN files. | Code from intent |
| 1:45-2:25 | For planned feature work, `cf-sdlc-implement` helps implement from approved FEATURE context. For smaller focused changes, `cf-coding` supports code and unit test work without pretending every edit needs a large process. | A large feature uses full workflow; a small fix uses a lighter path. | Right size workflow |
| 2:25-3:05 | For unfamiliar code or bugs, `cf-explore` helps developers understand the area before changing it. That matters because random edits in unknown code create review risk and regression risk. | A bug report links to targeted code exploration before the fix. | Explore before fixing |
| 3:05-3:45 | Tests become part of the same story. Instead of writing tests only against implementation details, developers can connect tests back to feature intent and expected behavior. | FEATURE intent generates code and tests side by side. | Tests follow intent |
| 3:45-4:25 | Before review, `cfs` can run repeatable checks for the configured project surface. These checks do not replace human judgment, but they give reviewers a cleaner evidence packet. | Terminal checks pass, then a reviewer inspects the linked evidence. | Checks before review |
| 4:25-5:00 | For DevLeads, the value is consistency across a team and across repositories. Workspaces can bring related specifications, libraries, API contracts, backend services, frontends, and mobile apps into one traceability view, so teams can spot gaps between requirements and real implementation. | Multiple repositories converge into one reviewable map with requirement, code, and test links. | Reviewable team work |

---

## Overview 6. Constructor Studio for QA Engineers

### Story Goal

Show QA engineers how Studio makes expected behavior, evidence, and traceability easier to inspect before test work begins.

### Narrator Script and Visual Direction

| Time | Narrator Script | Animation / Visual Direction | On-Screen Text |
|---|---|---|---|
| 0:00-0:35 | QA teams are also affected by AI acceleration. More code changes arrive. More generated tests appear. More documents claim to describe behavior. But QA still needs to know what is actually expected. | A QA board receives many code, doc, and test artifacts at once. | More artifacts to verify |
| 0:35-1:10 | The problem is weak evidence. If requirements, design, implementation, and tests are disconnected, QA has to reconstruct intent from tickets, chats, diffs, and meetings. | A QA engineer follows broken links between ticket, doc, code, and test. | Intent gets scattered |
| 1:10-1:45 | Constructor Studio helps QA work from a clearer chain. A change can carry product intent, design context, feature behavior, implementation evidence, and validation results together. | The scattered artifacts connect into one evidence chain. | Clearer evidence chain |
| 1:45-2:25 | `cf-explore` and `cf-explain` help QA engineers understand the codebase and related documents before writing or extending tests. This is especially useful in brownfield systems where behavior is spread across older modules. | QA starts from a context map before writing tests. | Understand before testing |
| 2:25-3:05 | `cf-coding` can support automated test authoring when the expected behavior is clear. The goal is not to generate tests blindly, but to write tests against visible intent and requirement links. | Test cases connect back to feature behavior and requirements. | Test against intent |
| 3:05-3:45 | Repeatable checks add another signal. If references, structure, or configured traceability fail, QA can see that early. Passing checks do not prove quality, but failing checks expose review risk. | Validator catches a broken reference before QA approval. | Checks expose risk |
| 3:45-4:25 | This changes collaboration. QA is no longer only at the end of a code diff. QA can inspect the same delivery chain that Product, Architecture, and Development used to create the change. | QA joins the shared PM, Architect, Developer workflow map. | QA inside the flow |
| 4:25-5:00 | For QA engineers, Constructor Studio provides better context before testing, stronger evidence during review, and a clearer path from requirements to behavior and automated tests. QA can review where a requirement is tested: unit tests, integration tests, end-to-end tests, security tests, performance tests, and gaps that still need coverage. | End on requirement, feature, code, test layers, and approval connected across a workspace. | Better context, better tests |

---

## Closing Note for Production Team

Each overview must lead with the organizational problem before naming Studio mechanics. The audience should first feel the pain: AI creates more code and markdown faster, and that creates control, consistency, completeness, and review problems.

Only after that should the narrator introduce Constructor Studio as the solution: a customizable collaboration environment for teams, roles, workflows, evidence, validation, and traceability.

Production should use narration, on-screen text, subtitles, and simple diagrams together. Do not rely on voice alone when a phase model, evidence chain, or role handoff can be shown visually.

Recurring visual pattern:

- First show artifact explosion.
- Then show drift and inconsistency.
- Then show Studio connecting roles and artifacts.
- Then show a simple evidence chain from intent to code to tests to review.
