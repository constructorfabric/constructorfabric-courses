# Constructor Studio Academy: Build a Todo App With AI Agents

> Version boundary: Constructor Studio v1.0.0 only.
>
> This course content is validated against Constructor Studio v1.0.0 source documentation only. Any other product version, fork, or host-integration revision requires a fresh source review before reuse.

## What You Will Build

In this course you will use Constructor Studio to build and review a small Todo app. The core path uses one canonical architecture: a TypeScript HTTP API backend plus a React client. By the end, you will have a review-ready project package with:

- the SDLC (Software Development Lifecycle) kit installed and validated;
- a short Todo intent refined through `cf-brainstorm` into an input brief;
- SDLC artifacts (`PRD`, `ADR`, `DESIGN`, `DECOMPOSITION`, and `FEATURE`);
- checkpoint evidence in `docs/course-notes.md`;
- a TypeScript HTTP API backend slice;
- a React UI slice connected to that backend;
- code traceability markers linking implementation to FEATURE IDs when the kit enables traceability;
- validation output;
- behavior proof for list, create, toggle, and delete;
- review findings and fixes;
- a final handoff package explaining what changed, what evidence exists, and what still needs human approval.

This course is operator-first. You are learning the day-one workflow for using Constructor Studio on a Todo project safely and repeatably. It assumes basic repo, Git, and terminal familiarity. Custom authoring, extension work, and deeper host tailoring come later, after you can operate the standard workflows with confidence.

The app stays intentionally small. The point is not to teach React or backend design from scratch. The point is to teach you how to use Constructor Studio so AI-assisted work remains bounded, traceable, reviewable, and safe.

Optional variant:

- an in-process service or adapter layer may exist behind the HTTP API if the repo already uses that pattern;
- do not make that the primary course architecture;
- do not switch from HTTP API to in-process-only behavior on the core path without an explicit repo-specific reason.

The course works with Claude Code, Codex, or both. The core artifact-authoring path requires whichever host you use to preserve Constructor Studio routing, read-only analysis, and write gates. Use the host you prefer after it passes the Module 3 host gate; if a host surface is stale or misconfigured, regenerate its integration, reopen or reload it, and rerun the gate before continuing.

## How To Take This Course

Use one repo throughout the course. The repo may be empty at first, or it may already contain a small Todo app. Your evidence file for this course is `docs/course-notes.md`. If `docs/` does not exist yet, create it first. Put every checkpoint, command log, validation note, and review evidence in that file.

When you see a terminal command, run it in your shell from the repo root. When you see a chat prompt, paste it into Claude Code or Codex after Constructor Studio is active.

Canonical forms:

- Terminal commands use `cfs`.
- Prompt cards are copy-paste ready. When a course step has a chat prompt, it should show a Claude Code block and a Codex block.
- The workflow intent is usually identical in both hosts, but the copy-paste command prefix is not.
- Claude Code prompt cards start with `/cf` (activation) or a specific skill name, for example `/cf-coding`, `/cf-write-docs`, `/cf-sdlc-doc-prd`, or `/cf-sdlc-implement`.
- Codex prompt cards use the same names with the dollar prefix: `$cf`, `$cf-coding`, `$cf-write-docs`, `$cf-sdlc-doc-prd`, `$cf-sdlc-implement`.
- Pick the specialized command for the job. The SDLC kit skills (`cf-sdlc-doc-prd`, `cf-sdlc-doc-adr`, `cf-sdlc-doc-design`, `cf-sdlc-decompose`, `cf-sdlc-doc-feature`, `cf-sdlc-implement`) author and review their own artifact, and core skills like `cf-coding` and `cf-write-docs` both write and review through a built-in review-fix loop.
- For activation, Claude Code uses `/cf`; Codex uses `$cf`. The task text follows the command name (no colon needed), for example `/cf-auto-config` in Claude Code or `$cf-auto-config` in Codex.
- Codex defaults to an autonomous mode that runs ahead and skips the interactive gates Constructor Studio relies on. Start every Codex session with `disable autonomous mode` (best practice; or set it as a system prompt) so sub-agent approval, git-commit mode, brainstorm offers, and per-write confirmations actually appear. See Lesson 2.3. Claude Code respects the gates by default.
- SDLC and Cypilot migration skills appear in the skill list but are reference-only in this course.

Starter `docs/course-notes.md` template:

```markdown
# Course Notes

## Setup Evidence
| Item | Value |
|---|---|
| Course repo root | |
| Setup state | |
| Current next step | |

## Command Log
| Command | Purpose | Result | Log excerpt or path |
|---|---|---|---|
|  |  |  |  |

## Validation Log
| Command | Scope | Pass/Fail/N/A | Output excerpt or log path |
|---|---|---|---|
|  |  |  |  |

## Review Cycle Log
| Cycle | Prompt or review source | Findings in scope | Decision | Follow-up |
|---|---|---|---|---|
|  |  |  |  |  |

## Plan-State Snapshots
| Moment | Plan path | plan.execution_status | plan.lifecycle_status | phases[].status |
|---|---|---|---|---|
|  |  |  |  |  |

## SDLC Artifact Chain
| Layer | Artifact path | Key IDs | Validation result |
|---|---|---|---|
| PRD |  |  |  |
| ADR |  |  |  |
| DESIGN |  |  |  |
| DECOMPOSITION |  |  |  |
| FEATURE |  |  |  |
| CODEBASE implementation + traceability |  |  |  |

## Conflict Table
| Course guidance | Observed/source truth | Impact | Decision |
|---|---|---|---|
|  |  |  |  |

## Brownfield/Workspace Evidence
| Topic | Evidence | Impact on this repo |
|---|---|---|
|  |  |  |
```

## Module 1. Orientation: What Constructor Studio Adds

### Lesson 1.1. The Four Actors

Constructor Studio is a repo-attached workflow, context, and validation layer around an AI coding tool. It does not replace judgment.

There are four actors:

- Human: approves scope and accepts the final result.
- Host: Claude Code or Codex, the environment where the agent runs.
- Agent: the reasoning and writing executor inside the host.
- Constructor Studio: the workflow, context, routing, and validation layer.

Your operating rule for the rest of the course:

```text
approved SDLC artifact chain -> bounded plan -> implementation with traceability -> deterministic checks -> semantic review -> human approval
```

If a step skips that chain, stop and recover before continuing.

Do this as a thinking check, not a file-writing exercise yet:

1. Name the four actors in your own words.
2. Say what each actor is allowed to decide.
3. Say this sentence out loud or write it in temporary notes: `A passing validator is not human approval.`

Checkpoint:

- You can distinguish the human, host, agent, and Constructor Studio roles.
- You understand that validation evidence supports review; it does not replace approval.

### Lesson 1.2. The Running Todo Project

You will build a Todo app through small, reviewable steps. The app will eventually support four core behaviors:

- list todos;
- create a todo with a title;
- mark a todo complete or incomplete;
- delete a todo.

Do not write the Todo intent or input brief yet. First you need a real course folder, a working `cfs` install, Constructor Studio initialized in that folder, the SDLC kit installed, and host integrations generated. Prompts start only after setup is complete.

Checkpoint:

- You understand the target app shape.
- You did not invent a learner repo URL or rely on a hidden sample repo.

## Module 2. Setup For Claude Code And Codex

### Lesson 2.1. Create The Course Folder And Install `cfs`

Start from a clean course folder. The course assumes you initialize Constructor Studio yourself; it does not assume a preconfigured repo.

Terminal preflight:

```bash
mkdir -p todo-course
cd todo-course
pwd
git status --short
python3 --version
pipx --version
```

If `git status --short` fails because this is not a Git repo yet, initialize one before continuing:

```bash
git init
```

If `python3` is older than 3.11, fix Python first. If `pipx` is missing, install or repair it before continuing.

Checkpoint:

- You are in the course repo root.
- `git status --short` works.
- You have not opened Claude Code or Codex for course prompts yet.

Verify your prerequisites before continuing:

```bash
python3 --version
pipx --version
```

If `pipx` is missing, use the smallest platform-appropriate recovery:

macOS:

```bash
brew install pipx
pipx ensurepath
```

Linux:

```bash
python3 -m pip install --user pipx
python3 -m pipx ensurepath
```

Windows PowerShell:

```powershell
py -m pip install --user pipx
py -m pipx ensurepath
```

The core course command path assumes a POSIX-compatible shell: macOS Terminal, Linux, WSL, or Git Bash on Windows. If you choose native PowerShell after installation, translate POSIX commands explicitly and record the PowerShell equivalent in `docs/course-notes.md` before continuing.

Then open a new terminal. On macOS `zsh`, or if you intentionally want to reload the current shell:

```bash
source ~/.zshrc
```

Install the Constructor Studio CLI at the course version boundary, then verify it:

```bash
pipx install "git+https://github.com/constructorfabric/studio.git@v1.0.0"
cfs --version
```

Expected `cfs --version` semantics:

- the output must report version `1.0.0` for this course line;
- patch or host packaging details may vary, but the reported Studio version must still resolve to `1.0.0`;
- if `cfs --version` reports another major or minor version, stop and reconcile before continuing.

If `cfs` is still missing after install, recover in this order:

1. Open a new terminal.
2. On macOS `zsh`, run `source ~/.zshrc`.
3. Re-check `pipx --version`.
4. Re-check `cfs --version`.

Once `cfs --version` works, initialize the repo:

```bash
cfs init
```

During `cfs init`, use the defaults unless you intentionally need a custom project root or Constructor Studio directory. When the SDLC kit prompt appears, choose `a` to install it. When kit resource paths are shown, press Enter for each default path.

You do not need to read every generated resource path. The important choices are:

```text
Project root directory? [current repo]                  -> press Enter
Constructor Studio directory? [.cf-studio]              -> press Enter
Install SDLC kit (constructorfabric/studio-kit-sdlc)?    -> type a
Kit root directory [...]                                -> press Enter
Resource '...' path [...]                               -> press Enter for each resource
```

A successful init ends with a summary like this:

```text
Constructor Studio Init
  Project: TodoCourse
  Constructor dir: .cf-studio/

Core files copied to .core/
Config created in config/
Kits installed:
  sdlc: files generated
AGENTS.md navigation block injected into project root

Constructor Studio initialized!

Next steps:
  1. Set up your IDE:  cfs generate-agents
  2. Review config:    open .cf-studio/config/core.toml
  3. Start using:      type '/cf' in your IDE chat
```

If your `cfs init` flow does not offer the kit, or if you accidentally decline it, install the kit explicitly before continuing:

```bash
cfs kit install constructorfabric/studio-kit-sdlc
cfs info
cfs validate-kits --kit sdlc
```

`cfs validate-kits .` is a useful general kit-template validation command, but for this course the SDLC proof must include `cfs info` plus `cfs validate-kits --kit sdlc`, so you know the installed `sdlc` kit is the one being checked.

After init, `cfs info` should show the project, the `.cf-studio` adapter directory, and the SDLC kit registration. A shortened healthy shape looks like this:

```text
Constructor Studio Project Info
  Project root: .../todo-course
  Adapter dir: .cf-studio
  Config version: 1.0

Kits (1)
  sdlc  v1.0.0
    Content: artifacts, codebase, scripts, workflows
    Artifact kinds: ADR, DECOMPOSITION, DESIGN, FEATURE, PRD, ...
    Workflows: migrate-openspec, pr-review, pr-status

Systems (1)
  TodoCourse (...)  kit=sdlc
```

The full output may list many resources and variables. You do not need to copy them all into `docs/course-notes.md`; record the evidence that `sdlc v1.0.0` is present, the system is `TodoCourse`, and the kit content includes artifacts and workflows.

Do not continue to Module 3 without the SDLC kit. Without it, the course cannot teach the required PRD -> ADR + DESIGN -> DECOMPOSITION -> FEATURE -> CODE flow.

Generate host integrations for the host you will use.

Claude Code:

```bash
cfs generate-agents --agent claude
```

Expected Claude preview shape:

```text
Generate Agent Integration — claude

  claude:
    + .claude/skills/cf/SKILL.md (created)
    + .claude/skills/cf-generate/SKILL.md (created)
    + .claude/skills/cf-analyze/SKILL.md (created)
    + .claude/skills/cf-plan/SKILL.md (created)
    + .claude/agents/cf-phase-runner.md (created)
    + .claude/agents/cf-semantic-reviewer-artifact.md (created)
    + ... many more generated skills and agents ...

Reply with `y` to write these generated files or `n` to abort.
Proceed? [Y/n]
```

The long list is normal. It is a preview of generated Claude skills and agents. If the target is your course repo and the create/update set matches `claude`, answer `y`.

After you confirm, a successful run ends with a summary like this:

```text
27 skill file(s), 42 subagent file(s)

Agent integration complete!

Your IDE will now:
  - Route /cf-generate, /cf-analyze, /cf-plan, and /cf-workspace to Constructor Studio workflows
  - Recognize the Constructor Studio skill in chat
```

The exact counts may change with the installed Studio version, but for this v1.0.0 course the important signal is `Agent integration complete!`.

Codex:

```bash
cfs generate-agents --agent openai
```

Expected OpenAI/Codex preview shape:

```text
Generate Agent Integration — openai

  openai:
    + .agents/skills/cf/SKILL.md (created)
    + .agents/skills/cf-generate/SKILL.md (created)
    + .agents/skills/cf-analyze/SKILL.md (created)
    + .agents/skills/cf-plan/SKILL.md (created)
    + .codex/agents/cf-phase-runner.toml (created)
    + .codex/agents/cf-semantic-reviewer-artifact.toml (created)
    + ... many more generated skills and agents ...

Reply with `y` to write these generated files or `n` to abort.
Proceed? [Y/n]
```

The long list is normal here too. For Codex, skills are generated under `.agents/skills/`, and subagents are generated as `.codex/agents/*.toml`. If the target is your course repo and the create/update set matches `openai`, answer `y`.

After you confirm, a successful OpenAI/Codex run also ends with a summary like this:

```text
27 skill file(s), 42 subagent file(s)

Agent integration complete!

Your IDE will now:
  - Route /cf-generate, /cf-analyze, /cf-plan, and /cf-workspace to Constructor Studio workflows
  - Recognize the Constructor Studio skill in chat
```

The exact counts may change with the installed Studio version, but the important signal is still `Agent integration complete!`.

`cfs generate-agents` may preview files or pause for confirmation before writing. Answer the prompt, let generation finish, then reopen or reload the host so it picks up the generated files. Rerunning `cfs generate-agents` fully regenerates generated host entry points; do not hand-edit generated host files. Keep project-specific changes in the actual source-of-truth files instead.

Both hosts:

```bash
cfs generate-agents --agent claude
cfs generate-agents --agent openai
```

After generating agents, rerun:

```bash
cfs info
```

The `Agent integrations` section should include the host or hosts you generated:

```text
Agent integrations
  claude
  openai
```

If you generated only one host, seeing only that host is fine. If you generated both Claude and OpenAI/Codex, both should appear.

Expected result:

- `.cf-studio/` exists.
- The SDLC kit is installed or explicitly installed immediately after init.
- `cfs info` shows the `sdlc` kit is registered, and `cfs validate-kits --kit sdlc` passes. Any kit installation problem is recorded as a blocker.
- Claude Code setups typically include generated `.claude/skills/` and `.claude/agents/`.
- Codex setups typically include shared `.agents/skills/`, a `.codex/` installation marker, and `.codex/agents/` with a TOML agent file.
- Generated host files are integration surfaces, not source-of-truth files. Keep requests explicit and bounded in both hosts.
- No setup command was run from the wrong repo.

Troubleshooting:

- If `pipx` is not found, install `pipx`, update `PATH`, open a new terminal, and rerun `pipx --version`.
- If `cfs` is not found after install, open a new terminal, run `source ~/.zshrc` on macOS `zsh`, then rerun `pipx --version` and `cfs --version`.
- If `cfs generate-agents` looks stalled, it may be waiting for confirmation before writing files.
- If generated files are not picked up, reopen or reload the host after generation completes.
- If you think setup ran in the wrong place, re-check in order: `pwd`, `git status --short`, `pipx --version`, `cfs --version`.

Now create the course evidence file:

```bash
mkdir -p docs
touch docs/course-notes.md
```

Add these headings to `docs/course-notes.md`:

```markdown
# Course Notes

## Setup Evidence

## Activation Evidence

## Brainstorm And Intent

## SDLC Artifact Chain

## Validation Log

## Review Cycle Log
```

Add the sentence `A passing validator is not human approval.` under `Setup Evidence`.

Checkpoint:

- `docs/course-notes.md` records the exact setup commands you ran.
- `docs/course-notes.md` records that you accepted or installed the SDLC kit and includes the `cfs info` registration evidence plus the `cfs validate-kits --kit sdlc` result.
- `docs/course-notes.md` names the generated host surfaces that match your chosen host.

### Lesson 2.2. Make The Initial Commit

Create the initial Git commit before any brainstorm or sub-agent workflow. This module is design-first, so there is nothing to build by hand. The application itself is created later, when the agent implements the FEATURE in Module 4.

Native sub-agent dispatch needs a valid Git `HEAD`: a freshly initialized repo with no commits can pass `git status`, but still fail sub-agent dispatch because `git rev-parse HEAD` has nothing to resolve. This commit captures the initialized Studio workspace only.

Check for `HEAD`:

```bash
git rev-parse --verify HEAD
```

If that command fails, create the initial course setup commit:

```bash
git status --short
git add .
git commit -m "chore: initialize Constructor Studio todo course"
git rev-parse --short HEAD
```

Expected result:

- The first commit may be large. Seeing many files is normal because `.cf-studio/`, SDLC kit resources, and the generated Claude/Codex host integrations are all part of the initialized course workspace.
- The important success signal is that `git rev-parse --short HEAD` prints a short commit hash such as `b4a1e9e`.
- Record that hash in `docs/course-notes.md` under setup evidence.

If `git commit` fails because Git identity is not configured, configure your Git identity using your normal project policy, then rerun the commit. Do not continue to Module 3 until `git rev-parse --verify HEAD` succeeds.

### Lesson 2.3. Activate Constructor Studio In Chat

1. Open Claude Code or Codex in the repo root.

2. Before activating Constructor Studio, set the working model profile.

Claude Code:

```text
/model Sonnet
/effort medium
```

Prefer regular Sonnet without a `[1m]` suffix for this course. In Claude Code, type `/model Sonnet` directly; opening `/model` without an argument may show a picker that keeps or selects `Sonnet (1M context)`. If you accidentally land on 1M context, type `/model Sonnet` again, then verify the status line says `Sonnet with medium effort` rather than `Sonnet (1M context)`. If Claude Code still will not let you remove 1M context, do not block the course. Keep Sonnet with medium effort. Record `Claude context: 1M could not be disabled` in `docs/course-notes.md`, then continue.

Codex:

```text
Model: gpt-5.4
Reasoning: medium
```

Use the Codex model picker, session settings, or config surface available in your install before running `$cf`. The goal is GPT-5.4 with medium reasoning for the course path.

Codex also defaults to an autonomous mode that can run ahead and skip the interactive gates Constructor Studio relies on — sub-agent approval, git-commit mode, brainstorm offers, and per-write confirmations. Turn it off once at the start of every Codex session, before `$cf`:

```text
disable autonomous mode
```

Keep this as your first Codex message each session, or set it as a system or config instruction so it always applies — disabling autonomy at session start is the best practice. With autonomy off, the gates appear exactly as this course describes and you approve every write.

If you cannot disable autonomous mode, use the two-prompt fallback for each skill: send the bare load command first (for example `$cf-sdlc-doc-prd`), let the skill load and present its gates, then send the intent as a separate follow-up message. Claude Code does not need this; it respects the gates by default.

3. Activate Constructor Studio.

Claude Code:

```text
/cf
```

Codex:

```text
$cf
```

Expected result after activation:

- You get a clear activation confirmation or workflow-aware acknowledgement.
- The host behaves like Constructor Studio is active for this repo, not like a generic assistant with no repo-aware workflow layer.

Claude Code activation commonly looks like this when you type only `/cf` without naming a workflow. Constructor Studio first loads its core rules and reports them, then asks you to pick a workflow skill:

```text
Constructor Studio loaded (cf). Rule sources loaded: .cf-studio/.gen/AGENTS.md,
.cf-studio/.gen/SKILL.md, .cf-studio/config/ (when present), the core PDSL
execution card, and the cf SKILL units. cf is ready.

No task intent in the prompt. Showing all available cf-* skills.

Pick a cf-* skill by number to run it.

Core workflows:
1. cf-analyze — analyze artifacts, code, or the codebase
2. cf-auto-config — auto-configure the studio
3. cf-brainstorm — run a brainstorm panel
4. cf-coding — write, implement, or fix code
5. cf-debug-prompts — debug prompt / skill issues
6. cf-explain — explain, walk through, or narrate a topic or artifact
7. cf-explore — explore, discover, or survey the project
8. cf-generate — create, update, or regenerate artifacts
9. cf-help — get help with Constructor Studio
10. cf-map — build an interactive dependency map
11. cf-plan — plan work before executing it
12. cf-studio — session management (alias of cf)
13. cf-workspace — set up or manage a multi-repo workspace
14. cf-write-docs — write or revise documentation
15. cf-write-skills — write or revise skills

Kit: sdlc workflows:
16. cf-sdlc-change-impact-analysis — analyze change impact across artifacts
17. cf-sdlc-decompose — decompose a PRD/DESIGN into a DECOMPOSITION artifact
18. cf-sdlc-doc-adr — author or revise an ADR
19. cf-sdlc-doc-design — author or revise a DESIGN artifact
20. cf-sdlc-doc-feature — author or revise a FEATURE artifact
21. cf-sdlc-doc-prd — author or revise a PRD
22. cf-sdlc-implement — implement a FEATURE as code
23. cf-sdlc-migrate-openspec — migrate OpenSpec artifacts into the SDLC pipeline
24. cf-sdlc-pr-review — review a pull request
25. cf-sdlc-pr-status — get the status of a PR
26. cf-sdlc-reverse-engineer — reverse-engineer existing code into SDLC artifacts

27. none — stop
```

This is a valid activation signal. It means Constructor Studio loaded its core rules and is offering the available `cf-*` workflow skills. The agent shows the same load report and skill menu in both hosts; only the prefix you typed differs (`/cf` in Claude Code, `$cf` in Codex). Because you typed `/cf` with no task intent, the menu lists every available skill and pre-selects none; when your prompt does carry an intent, the matching skill is tagged `(suggested)`. After activation a write gate is held: the agent can inspect and route, but it cannot write files until a workflow releases the gate and you confirm each write. SDLC and Cypilot migration skills appear in the list but are reference-only in this course. For this lesson, do not pick a write-capable skill yet; continue with the read-only `cf-explore` check in Lesson 2.4.

Codex activation commonly looks like this (same load report and skill menu; you type `$cf` instead of `/cf`):

```text
Constructor Studio loaded (cf). Rule sources loaded: .cf-studio/.gen/AGENTS.md,
.cf-studio/.gen/SKILL.md, .cf-studio/config/ (when present), the core PDSL
execution card, and the cf SKILL units. cf is ready.

No task intent in the prompt. Showing all available cf-* skills.

Pick a cf-* skill by number to run it.

Core workflows:
1. cf-analyze — analyze artifacts, code, or the codebase
2. cf-auto-config — auto-configure the studio
3. cf-brainstorm — run a brainstorm panel
4. cf-coding — write, implement, or fix code
5. cf-debug-prompts — debug prompt / skill issues
6. cf-explain — explain, walk through, or narrate a topic or artifact
7. cf-explore — explore, discover, or survey the project
8. cf-generate — create, update, or regenerate artifacts
9. cf-help — get help with Constructor Studio
10. cf-map — build an interactive dependency map
11. cf-plan — plan work before executing it
12. cf-studio — session management (alias of cf)
13. cf-workspace — set up or manage a multi-repo workspace
14. cf-write-docs — write or revise documentation
15. cf-write-skills — write or revise skills

Kit: sdlc workflows:
16. cf-sdlc-change-impact-analysis — analyze change impact across artifacts
17. cf-sdlc-decompose — decompose a PRD/DESIGN into a DECOMPOSITION artifact
18. cf-sdlc-doc-adr — author or revise an ADR
19. cf-sdlc-doc-design — author or revise a DESIGN artifact
20. cf-sdlc-doc-feature — author or revise a FEATURE artifact
21. cf-sdlc-doc-prd — author or revise a PRD
22. cf-sdlc-implement — implement a FEATURE as code
23. cf-sdlc-migrate-openspec — migrate OpenSpec artifacts into the SDLC pipeline
24. cf-sdlc-pr-review — review a pull request
25. cf-sdlc-pr-status — get the status of a PR
26. cf-sdlc-reverse-engineer — reverse-engineer existing code into SDLC artifacts

27. none — stop
```

4. Confirm read-only routing before any setup prompt that can write.

Claude Code prompt:

```text
/cf-explore summarize the current repo structure and identify the safest next setup step. Do not modify files.
```

Codex prompt:

```text
$cf-explore summarize the current repo structure and identify the safest next setup step. Do not modify files.
```

Expected survey result:

- It may report that `.cf-studio/` and the SDLC kit are ready.
- It may report that there is no application code yet; that is normal for a fresh course repo.
- It may report that the artifact registry is empty and no PRD, ADR, DESIGN, DECOMPOSITION, or FEATURE exists yet.
- It may report whether the repo has an initial commit.
- It may recommend one of several next steps: make the initial commit, brainstorm intent, or write PRD/FEATURE.

Use this course policy to interpret the survey:

- If the survey reports missing Git `HEAD`, create the initial setup commit before continuing.
- If the survey recommends `cf-brainstorm` as the safest next step, accept that recommendation and continue to Module 3.
- If the survey recommends creating PRD or FEATURE immediately, treat that as a useful reminder that the artifact registry is empty, but do not skip the course path. Continue to Module 3 and run the brainstorm first so the first artifact is grounded in a human-approved Todo intent.

Do not create technical plumbing just because it is absent; the agent creates it when implementation begins. Do not register codebase scan paths in Module 2: there are no course artifacts yet, so marker scanning is not actionable. The course handles traceability configuration later, after the Todo FEATURE exists and implementation is about to begin.

5. Run a read-only readiness check for the next course stage.

Claude Code prompt:

```text
/cf-explore verify that this repo is ready to continue to the Todo brainstorm and SDLC artifact chain.
Check only setup readiness: .cf-studio initialization, sdlc kit installation, generated host integration, valid git HEAD, and docs/course-notes.md.
Do not modify files.
Return:
- PASS if the repo is ready for brainstorm/artifact authoring
- SETUP BLOCKER only for issues that prevent Module 3 from running
- DEFERRED if the issue matters later but does not block brainstorm or SDLC artifacts
```

Codex prompt:

```text
$cf-explore verify that this repo is ready to continue to the Todo brainstorm and SDLC artifact chain.
Check only setup readiness: .cf-studio initialization, sdlc kit installation, generated host integration, valid git HEAD, and docs/course-notes.md.
Do not modify files.
Return:
- PASS if the repo is ready for brainstorm/artifact authoring
- SETUP BLOCKER only for issues that prevent Module 3 from running
- DEFERRED if the issue matters later but does not block brainstorm or SDLC artifacts
```

Expected readiness interpretation:

- Missing initial Git commit is a `SETUP BLOCKER`; native sub-agent dispatch can fail when `git rev-parse HEAD` has no valid commit.
- Missing `.cf-studio/`, missing SDLC kit, or missing generated host integration is a `SETUP BLOCKER`.

Healthy readiness output should look like this in substance:

```text
Setup Readiness Report — Module 3

Check                       Result  Evidence
--------------------------  ------  -------------------------------------------------
.cf-studio initialization   PASS    .cf-studio/ + core.toml [[kits]] sdlc + artifacts.toml
SDLC kit installation       PASS    kits/sdlc/ subdirs; all artifact kinds + workflows
Generated host integration  PASS    .cf-studio/.gen/ with AGENTS.md + SKILL.md
Git HEAD                    PASS    valid commit on current branch; no detached HEAD
docs/course-notes.md        PASS    exists, writable; section headers present (body empty)

Overall: PASS — ready for the Todo brainstorm and SDLC artifact chain (Module 3).
No SETUP BLOCKER. No DEFERRED items.
```

If the host offers next options after the PASS, choose the brainstorm route. Do not choose direct PRD/FEATURE generation yet; the next course step is the human-guided Todo brainstorm.

6. Do not implement backend or UI product code in Module 2 yet. Greenfield SDLC work is design-first: implementation with `cf-sdlc-implement` starts only after PRD, ADR, DESIGN, DECOMPOSITION, and FEATURE exist, and that implementation also creates the project shell (`package.json`, `ui/`, `src/server/`, `.gitignore`, and the package scripts).

7. After setup, the repo holds just Constructor Studio and your notes:

```text
.cf-studio/
docs/
  course-notes.md
```

Generated host-integration directories (such as `.claude/`, `.agents/`, `.codex/`) are also present. The agent creates `package.json`, `src/server/`, `tests/`, `ui/`, and the package scripts (`dev:api`, `dev:ui`, `test`, `typecheck`, `build`) when FEATURE-driven implementation begins in Module 4.

8. There is no command contract to record yet. The package scripts are created by the agent during implementation in Module 4. Before Module 3, the important point is that setup, activation, and readiness checks passed; the app and its commands come later, from the FEATURE.

### Lesson 2.4. Activation Rubric

Use this rubric to grade the activation and read-only responses you already saw in Lesson 2.3 — the `/cf` load report and the `cf-explore` survey and readiness output. If you opened a fresh chat, re-run `/cf` and one read-only `cf-explore` prompt first, then apply the rubric.

A healthy activation:

- gives a clear activation confirmation or workflow-aware acknowledgement, not a generic-assistant reply;
- stays read-only on the survey and readiness prompts and writes no files;
- references at least one real repo artifact or note (`docs/course-notes.md`, `.cf-studio/`, or `src/`);
- names one bounded next step, or one tight clarification question.

It may name different "safest" next steps in different hosts. That is acceptable here: you are testing read-only routing and repo awareness, not delegating the course sequence.

Interpretation rule:

- If the response suggests writing PRD or FEATURE directly, record the suggestion, then still continue to the Module 3 brainstorm. The course's canonical sequence is: setup, read-only survey, brainstorm, then SDLC artifacts.
- If the response suggests backend code first, defer it until after the brainstorm and artifact chain.

Short activation rubric:

- Good: read-only behavior, explicit mention of a real repo artifact, no file writes, and one bounded next step or one tight clarification question.
- Bad: writes files, ignores the read-only instruction, or replies like a generic assistant with no `cf` workflow behavior.

Checkpoint:

- `docs/course-notes.md` contains one activation note and one read-only analysis result.
- `docs/course-notes.md` lists one good activation signal and one bad activation signal taken from the actual response you saw.

### Lesson 2.5. Routing And Control Plane: Operator Summary

You do not need the full internals on day one. You do need the operator rules that prevent bad turns.

- The `cf` skill loads its core rules at session start (the load report) before any workflow work and gates what can run safely in this repo.
- Intent routing offers the matching `cf-*` skill, so ask for one thing at a time and phrase the request clearly.
- A request such as `find the bug and fix it` goes to `cf-coding`, which reviews first and then applies bounded fixes through its review-fix loop.
- If your input is very large, ask `cf-explore` to summarize or split it into smaller review units before you continue, and use `cf-plan` only when the work itself truly needs phased execution.
- Write permissions, git behavior, and sub-agent behavior are controlled separately; do not assume that because one gate is open, all gates are open.
- The `cf-coding`, `cf-write-docs`, and `cf-write-skills` workflows open with optional explore and brainstorm gates before authoring or reviewing; skip them (the default) when the task is already clear, or use them for unfamiliar or ambiguous work.
- Keep context lean: when the next step does not need the current chat context, run `/clear` or open a new chat. Everything the course relies on lives on disk — the SDLC artifacts, `plan.toml` and phase files, the saved brainstorm, and `docs/course-notes.md` — so a fresh session loses nothing. After any reset, re-activate with `/cf` (and on Codex, re-send `disable autonomous mode`) before continuing, because activation is per session.

Under-the-hood glossary:

- The deeper gate and state glossary lives in Appendix D. Read it when you need to reconcile routing, size gates, or control-plane variables against source truth.

Mini-lab:

1. In `docs/course-notes.md`, add a short table with three rows: `cf-explore`, `cf-plan`, `cf-coding`.
2. For each row, write one sentence for when it is the right route.
3. Add one sentence explaining how `cf-coding` both finds and fixes through its review-fix loop.

### Lesson 2.6. Optional Source-Truth Sanity Check

Use this only as a lightweight safety check during the core path when command wording or routing behavior looks inconsistent in your current host. Do not turn it into a full audit unless something is actually off.

Do this when:

- command spelling looks inconsistent;
- routing or gate behavior in the host does not match the course;
- you need to clarify one live workflow choice before continuing.

Suggested prompt.

Claude Code prompt:

```text
/cf-explore compare the specific Constructor Studio command or routing wording I am about to use with the current repo-visible source truth for version 1.0.0. Return only the learner-safe phrasing I should use next and any explicit exclusions. Do not modify files.
```

Codex prompt:

```text
$cf-explore compare the specific Constructor Studio command or routing wording I am about to use with the current repo-visible source truth for version 1.0.0. Return only the learner-safe phrasing I should use next and any explicit exclusions. Do not modify files.
```

Formal source-truth reconciliation for teaching, reuse, or governance happens later in Module 10.3. During the core Todo path, record only the corrections that materially affect the current repo.

## Module 3. Create The SDLC Artifact Chain And Plan The Todo Work

### Module 3 Host Gate

Before you start artifact authoring, prove that your host preserves Constructor Studio routing:

1. Activate Constructor Studio: `/cf` in Claude Code, or `$cf` in Codex.
2. Run one read-only `cf-explore` prompt and confirm it does not write files.
3. Run the `cf-brainstorm` prompt in Lesson 3.1 and confirm it behaves as brainstorming, not generic implementation.
4. Ask for a write-capable artifact prompt only after the host shows or respects an explicit write-confirmation boundary.

If the host you chose does not preserve activation, read-only analysis, brainstorming, and write-confirmation boundaries, regenerate that host integration, reopen or reload the host, and rerun the gate. If it still fails, use another generated host that passes the gate before continuing.

### Lesson 3.1. Pick The Right Workflow

Use this decision table.

| Situation | Use |
|---|---|
| The idea is fuzzy | `cf-brainstorm` |
| You need the SDLC artifact chain | `cf-sdlc-doc-prd`, `cf-sdlc-doc-adr`, `cf-sdlc-doc-design`, `cf-sdlc-decompose`, `cf-sdlc-doc-feature` |
| The task is multi-step, risky, or multi-file | `cf-plan` |
| The scope is approved and you are writing or changing code | `cf-coding` (or `cf-sdlc-implement` for FEATURE → code with `@cpt-*` traceability) |
| You need review, validation, or explanation | the same specialized skill (each reviews through its review-fix loop); `cf-explain` for walkthroughs, `cf-write-skills` for prompt/workflow/agent files |

Do this exercise in chat.

Claude Code prompt:

```text
/cf-brainstorm I want to learn Constructor Studio by building a very small Todo app.
The app should have a TypeScript HTTP API and a React UI.
As a user, I should be able to list todos, create one with a title, toggle completion, and delete it.
Keep the project local, simple, reviewable, and suitable for SDLC artifacts, validation, and traceability practice.
Help me brainstorm the PRD-level product requirements first: actors, goals, functional requirements, non-goals, constraints, acceptance criteria, and product scope boundaries. Do not plan implementation yet.
End this brainstorm session by saving or summarizing the decisions only. Do not continue into PRD generation, artifact writing, planning, or implementation in this turn.
```

Codex prompt:

```text
$cf-brainstorm I want to learn Constructor Studio by building a very small Todo app.
The app should have a TypeScript HTTP API and a React UI.
As a user, I should be able to list todos, create one with a title, toggle completion, and delete it.
Keep the project local, simple, reviewable, and suitable for SDLC artifacts, validation, and traceability practice.
Help me brainstorm the PRD-level product requirements first: actors, goals, functional requirements, non-goals, constraints, acceptance criteria, and product scope boundaries. Do not plan implementation yet.
End this brainstorm session by saving or summarizing the decisions only. Do not continue into PRD generation, artifact writing, planning, or implementation in this turn.
```

Expected result:

- A PRD-focused brainstorm, not an implementation plan.
- A brainstorm panel offer.
- A proposed expert panel and seed topic.
- A wrap-up menu that lets you approve, iterate, discard, or continue into the next workflow with resolved inputs.
- The session stops after saved or summarized brainstorm decisions.
- No implementation yet.

The interaction runs in this order: (1) the brainstorm panel offer, (2) a one-time sub-agent approval, (3) the proposed expert panel.

1. Brainstorm panel offer. It reads roughly "Want a brainstorm panel? I'll assemble a 3-6 expert panel for cross-discipline pushback…", with reply grammar `yes` / `no` / `save` (plus optional modifiers such as `:N` for a round cap, `mode=fan-out`, or `mode=single-agent`). Reply `save` for this course so the transcript, `state.json`, and final `design.md` persist under `.cf-studio/.cache/brainstorm/...`:

```text
save
```

If `save` is not offered because the host is chat-only, reply `yes` and rely on the wrap-up approval handoff. If the session has already moved past the offer with no save path, finish the brainstorm and copy the approved wrap-up summary into `docs/course-notes.md` as fallback evidence.

2. Sub-agent approval (asked once per session). Approve so the facilitator and panel sub-agents run natively:

```text
1
```

3. Proposed expert panel and seed topic. The menu offers `start`, `seed:<topic>`, `drop E{N}`, `swap E{N}:<persona>`, `add:<persona>`, or `wrap`. Use the simplest path unless you see a real gap — reply `start` to begin round 1:

```text
start
```

The git-commit-mode question does not appear during brainstorm — its sub-agents are read-only. You are asked to choose `commit` / `stage` / `none` later, at the first write-capable workflow (for example PRD authoring); choose `commit` for this course so write-capable sub-agents have an explicit git boundary. That choice never overrides write gates: every file write still needs the workflow's write release and your explicit confirmation.

During the brainstorm rounds, keep these course constraints non-negotiable:

- the PRD scope must still cover list, create, toggle, and delete as product capabilities;
- the artifact chain is still PRD -> ADR + DESIGN -> DECOMPOSITION -> FEATURE before implementation;
- storage is local and simple, preferably in-memory for the first backend slice unless you intentionally approve persistence;
- no auth, multi-user behavior, routing, tags, due dates, priority, editing titles after creation, deployment, or database work.

If a panel tries to plan the implementation slice, drop delete, skip ADR/DESIGN, or delay the SDLC chain until after code, do not accept that default. Redirect the round back to PRD-level product requirements and scope boundaries.

Common Round 1 answer when the defaults preserve all four Todo operations:

```text
accept all
then: W
```

Common Round 1 answer when the panel tries to defer delete or skip SDLC layers:

```text
E1Q1: keep this brainstorm at PRD level; implementation planning comes later through DESIGN, DECOMPOSITION, and FEATURE
E2Q1: include list, create, toggle, and delete in PRD scope; do not defer delete
E3Q1: accept
E4Q1: accept
then: W
```

Use `then: W` when the first round has already captured product scope, boundaries, actors, and acceptance direction. Pick another numbered topic only if a PRD requirement or boundary is still unresolved.

At the brainstorm wrap-up, approve the resolved inputs if they match the Todo course scope, but do not continue into PRD generation in the same turn. If the workflow offers a handoff into the next generate step, stop after saving or summarizing the brainstorm decisions. Record the saved brainstorm cache path if save mode was used, or record the approved wrap-up summary in `docs/course-notes.md` if the session was chat-only. The brainstorm output becomes the original input evidence for PRD generation; it is not the governing implementation artifact.

If the host asks whether to continue into PRD generation immediately, answer:

```text
stop after saving the brainstorm decisions; do not generate PRD yet
```

Context reset (optional): the brainstorm decisions are saved on disk, and PRD authoring reads them from there. You can `/clear` or open a new chat before the artifact chain to keep context lean — then re-activate (`/cf`; on Codex also re-send `disable autonomous mode`).

### Lesson 3.2. Create The SDLC Artifact Chain

The SDLC kit is the governing process for this course. Its pipeline is:

```text
PRD -> ADR + DESIGN -> DECOMPOSITION -> FEATURE -> CODEBASE -> TESTING / REVIEW
```

Each layer transforms the previous layer:

- PRD captures WHAT: actors, capabilities, requirements, use cases, constraints, non-goals.
- ADR captures key architecture decisions and rationale.
- DESIGN captures HOW: components, interfaces, data model, API shape, sequences, constraints.
- DECOMPOSITION breaks DESIGN into ordered feature scope with dependencies.
- FEATURE captures implementable behavior as CDSL (Constructor DSL) flows, algorithms, states, definitions of done, and acceptance criteria.
- CODEBASE implements FEATURE, runs tests/build/review, and keeps traceability through scope markers plus per-instruction block markers when FULL traceability mode is active.
- TESTING / REVIEW validates behavior, markers, references, and semantic correctness.

Create the artifacts from the brainstorm-derived Todo input brief. Use `cf` if that is your host alias; the SDLC kit docs also show `cf-studio` for some kit-specific surfaces.

Artifact write pattern: send the authoring prompt for the next artifact directly (for example `cf-sdlc-doc-prd` for the PRD). The skill runs its own preflight, reports the exact target path and write scope, and waits for your approval before writing — there is no separate `cf-explore` step. Include `Approved write scope:` in the prompt, or approve the host's write-confirmation turn for those exact paths.

What the authoring skill reports for an empty registry:

- It may report `Semantic: FAIL` because `artifacts = []` and no PRD exists yet. That is expected at this exact point in the course; it means the SDLC chain has not started, not that setup failed.
- Treat the reported PRD path as the source of truth. In a fresh `TodoCourse` run this may be `docs/todocourse/PRD.md`; in another repo it may differ.
- If the host offers a menu such as "continue in this session", "fix prompt", or "plan prompt", do not let it auto-create the artifact from a vague menu choice. Continue with the explicit PRD generation prompt below, using the exact path the skill reported.
- Record the reported path and the empty-registry status in `docs/course-notes.md`.

### Lesson 3.2a. PRD, ADR, And DESIGN

During artifact generation, Constructor Studio may ask where to keep the mandatory author plan:

```text
Reply enter or memory for in-memory plan (default), or disk to also save a Markdown plan pack under .cf-studio/.cache/generate-plans/.
```

For this course, reply:

```text
memory
```

Use `disk` only if you intentionally want to inspect or preserve the generated author plan files across a long session. The normal course path keeps the plan in memory and writes only the approved SDLC artifacts.

PRD authoring is the first write-capable workflow, so this is where the git-commit-mode question appears: Constructor Studio asks how sub-agents should handle git for the files they write this session — `commit` / `stage` / `none`. Choose `commit` for this course:

```text
1
```

This is asked once per session. If you ran the Module 3 brainstorm, sub-agent dispatch was already approved there; if you skipped it, you are asked to approve sub-agents here instead (reply `1`).

Before it writes, the authoring skill (the SDLC doc skills run through `cf-write-docs`) opens two optional gates, each a numbered menu — first an explore gate, then a brainstorm gate:

```text
Before writing or reviewing docs, brainstorm ambiguous decisions or framing options with cf-brainstorm — or skip? Skip is the default when the approach is already clear. Reply with a number.
1 brainstorm
2 skip
```

Skip is the default. For this course you already ran a dedicated brainstorm in Module 3, so reply `2` (skip) at both gates here:

```text
2
```

Reply `1` (brainstorm) only to refine a genuinely ambiguous artifact — that launches `cf-brainstorm` with the offer from Lesson 3.1 (`yes` / `no` / `save`); prefer `save` so the decisions persist. Brainstorm separately per layer only when it helps: ADR + DESIGN when the architecture/design choices are still fuzzy, DECOMPOSITION or FEATURE when implementation order or acceptance boundaries are unclear.

After writing, the skill runs its own review-fix loop — it does not ask how many iterations to run. It runs the deterministic gate (tests, lint, typecheck, build where applicable), then a semantic review, and asks you to approve fixes one finding at a time. Each approved fix is applied, the deterministic gate re-runs, and the review repeats; the loop stops and reports any remaining findings when no fix is applied (nothing approved or nothing applicable). You stay in control through the per-finding approval gate, not an iteration count.

PRD.

Let the agent find the saved brainstorm evidence inside the PRD generation turn. This keeps the copy-paste prompt self-contained.

Claude Code prompt:

```text
/cf-sdlc-doc-prd make PRD for the Todo app from the approved brainstorm wrap-up.
Approved write scope:
- the exact PRD path reported by the skill, for example docs/todocourse/PRD.md
Before writing, find the newest saved brainstorm session under .cf-studio/.cache/brainstorm that matches the Todo PRD/product-requirements brainstorm.
Use its design.md as the original input evidence and its state.json as supporting context.
Report the exact design.md and state.json paths you selected.
If no saved brainstorm session exists, stop and ask me to either run the brainstorm with save mode or provide the approved brainstorm wrap-up from chat.
Keep PRD at the WHAT layer: actors, capabilities, requirements, use cases, constraints, non-goals, risks, and success criteria.
Do not include API schema, React component design, implementation tasks, or code details in the PRD.
```

Codex prompt:

```text
$cf-sdlc-doc-prd make PRD for the Todo app from the approved brainstorm wrap-up.
Approved write scope:
- the exact PRD path reported by the skill, for example docs/todocourse/PRD.md
Before writing, find the newest saved brainstorm session under .cf-studio/.cache/brainstorm that matches the Todo PRD/product-requirements brainstorm.
Use its design.md as the original input evidence and its state.json as supporting context.
Report the exact design.md and state.json paths you selected.
If no saved brainstorm session exists, stop and ask me to either run the brainstorm with save mode or provide the approved brainstorm wrap-up from chat.
Keep PRD at the WHAT layer: actors, capabilities, requirements, use cases, constraints, non-goals, risks, and success criteria.
Do not include API schema, React component design, implementation tasks, or code details in the PRD.
```

Validate PRD.

Claude Code prompt:

```text
/cf-sdlc-doc-prd validate PRD for the Todo app. Check structural, semantic, and reference quality. Do not modify code.
```

Codex prompt:

```text
$cf-sdlc-doc-prd validate PRD for the Todo app. Check structural, semantic, and reference quality. Do not modify code.
```

Read the validation result before moving on:

- classify one finding as blocker or non-blocker;
- cite the evidence that caused that classification;
- decide whether to revise the artifact or proceed;
- record the decision in `docs/course-notes.md`.

ADR, then DESIGN. Author them in order with the two specialized SDLC skills: `cf-sdlc-doc-adr` first, then `cf-sdlc-doc-design`.

ADR — Claude Code prompt:

```text
/cf-sdlc-doc-adr make the ADR for the Todo app from the PRD.
Approved write scope:
- the exact ADR path reported by the skill, for example docs/todocourse/ADR/cpt-todocourse-adr-todo-architecture.md
ADR decision: TypeScript HTTP API backend plus Vite React client for this course.
Do not implement code.
```

ADR — Codex prompt:

```text
$cf-sdlc-doc-adr make the ADR for the Todo app from the PRD.
Approved write scope:
- the exact ADR path reported by the skill, for example docs/todocourse/ADR/cpt-todocourse-adr-todo-architecture.md
ADR decision: TypeScript HTTP API backend plus Vite React client for this course.
Do not implement code.
```

DESIGN — Claude Code prompt:

```text
/cf-sdlc-doc-design make the DESIGN for the Todo app from the PRD and ADR.
Approved write scope:
- the exact DESIGN path reported by the skill, for example docs/todocourse/DESIGN.md
DESIGN must define the API boundary, Todo data model, UI/API interaction, local dev ports, validation approach, and traceability expectations.
Do not implement code.
```

DESIGN — Codex prompt:

```text
$cf-sdlc-doc-design make the DESIGN for the Todo app from the PRD and ADR.
Approved write scope:
- the exact DESIGN path reported by the skill, for example docs/todocourse/DESIGN.md
DESIGN must define the API boundary, Todo data model, UI/API interaction, local dev ports, validation approach, and traceability expectations.
Do not implement code.
```

Validate ADR and DESIGN.

Claude Code prompt:

```text
/cf-sdlc-doc-design validate ADR and DESIGN against the PRD and SDLC kit rules. Do not modify code.
```

Codex prompt:

```text
$cf-sdlc-doc-design validate ADR and DESIGN against the PRD and SDLC kit rules. Do not modify code.
```

Checkpoint:

- `docs/course-notes.md` records PRD, ADR, and DESIGN paths.
- `docs/course-notes.md` explains one thing that belongs in PRD and one implementation detail that must stay out.
- `docs/course-notes.md` explains one ADR decision and one DESIGN detail that must not be placed in PRD.
- You revised blocker findings before continuing, or explicitly recorded why findings are non-blocking.

### Lesson 3.2b. DECOMPOSITION And FEATURE

DECOMPOSITION.

Claude Code prompt:

```text
/cf-sdlc-decompose decompose the Todo DESIGN into ordered feature scope.
Approved write scope:
- the exact DECOMPOSITION path reported by the skill, for example docs/todocourse/DECOMPOSITION.md
Include at least one feature for Todo CRUD behavior that covers list, create, toggle, and delete.
Keep dependencies explicit and implementation units small.
Do not implement code.
```

Codex prompt:

```text
$cf-sdlc-decompose decompose the Todo DESIGN into ordered feature scope.
Approved write scope:
- the exact DECOMPOSITION path reported by the skill, for example docs/todocourse/DECOMPOSITION.md
Include at least one feature for Todo CRUD behavior that covers list, create, toggle, and delete.
Keep dependencies explicit and implementation units small.
Do not implement code.
```

Validate DECOMPOSITION.

Claude Code prompt:

```text
/cf-sdlc-decompose validate DECOMPOSITION against DESIGN and PRD. Check coverage, dependencies, IDs, and references. Do not modify code.
```

Codex prompt:

```text
$cf-sdlc-decompose validate DECOMPOSITION against DESIGN and PRD. Check coverage, dependencies, IDs, and references. Do not modify code.
```

FEATURE.

Recommended course convention: put FEATURE artifacts under `docs/todocourse/features/`. This keeps implementable feature specs separate from system-level PRD, ADR, DESIGN, and DECOMPOSITION artifacts.

Claude Code prompt:

```text
/cf-sdlc-doc-feature make FEATURE for todo-crud from DECOMPOSITION and DESIGN.
Approved write scope:
- the exact FEATURE path reported by the skill, for example docs/todocourse/features/todo-crud.md
The FEATURE must include CDSL actor flows for list, create, toggle, and delete; processing algorithms; Todo state behavior where relevant; definitions of done; acceptance criteria; and upstream references.
Preserve the SDLC FEATURE template structure, including the top-level `featstatus` ID and the parent DECOMPOSITION feature reference.
Do not implement code.
```

Codex prompt:

```text
$cf-sdlc-doc-feature make FEATURE for todo-crud from DECOMPOSITION and DESIGN.
Approved write scope:
- the exact FEATURE path reported by the skill, for example docs/todocourse/features/todo-crud.md
The FEATURE must include CDSL actor flows for list, create, toggle, and delete; processing algorithms; Todo state behavior where relevant; definitions of done; acceptance criteria; and upstream references.
Preserve the SDLC FEATURE template structure, including the top-level `featstatus` ID and the parent DECOMPOSITION feature reference.
Do not implement code.
```

Validate FEATURE.

Claude Code prompt:

```text
/cf-sdlc-doc-feature validate FEATURE todo-crud for CDSL structure, semantic completeness, upstream references, definitions of done, and implementation readiness. Do not modify code.
```

Codex prompt:

```text
$cf-sdlc-doc-feature validate FEATURE todo-crud for CDSL structure, semantic completeness, upstream references, definitions of done, and implementation readiness. Do not modify code.
```

Checkpoint:

- `docs/course-notes.md` records DECOMPOSITION and FEATURE paths.
- `docs/course-notes.md` explains why ordered implementation units belong in DECOMPOSITION.
- `docs/course-notes.md` explains why CDSL flows, algorithms, states, and definitions of done belong in FEATURE.
- `docs/course-notes.md` lists one thing that must stay out of FEATURE because it belongs in DESIGN, ADR, PRD, or CODEBASE.

### Lesson 3.2c. Validate The Artifact Chain

Expected artifact locations are the paths the skill reports and registers in `.cf-studio/config/artifacts.toml`. In a fresh `TodoCourse` run, they may look like:

- `docs/todocourse/PRD.md`
- `docs/todocourse/ADR/cpt-todocourse-adr-*.md`
- `docs/todocourse/DESIGN.md`
- `docs/todocourse/DECOMPOSITION.md`
- `docs/todocourse/features/*.md`

Deterministic validation examples, using the fresh `TodoCourse` shape:

```bash
cfs validate --artifact docs/todocourse/PRD.md
cfs validate --artifact docs/todocourse/ADR/cpt-todocourse-adr-todo-architecture.md
cfs validate --artifact docs/todocourse/DESIGN.md
cfs validate --artifact docs/todocourse/DECOMPOSITION.md
cfs validate --artifact docs/todocourse/features/todo-crud.md
cfs validate --local-only
```

Always replace the sample paths with the exact paths registered in your repo before running the commands. Validate every ADR file separately; the sample ADR and FEATURE paths are examples only. When `cfs toc` / `cfs validate-toc` is available in your installed version and required by the artifact rules, update the table of contents before marking an artifact ready.

Checkpoint:

- `docs/course-notes.md` records the paths of PRD, ADR, DESIGN, DECOMPOSITION, and FEATURE.
- `docs/course-notes.md` records validation results for each artifact layer.
- `docs/course-notes.md` records one blocker/non-blocker classification from artifact validation and the decision it caused.
- The FEATURE artifact, not the brainstorm cache or wrap-up summary, is now the governing artifact for implementation.
- If the kit generated different artifact paths, record those paths and use them consistently from here onward.

Context reset (optional): the artifact chain is on disk and the plan reads the FEATURE from `.cf-studio/config/artifacts.toml`. You can `/clear` or start a new chat before planning — then re-activate (`/cf`; on Codex also re-send `disable autonomous mode`).

### Lesson 3.3. Create A Plan

Now create a plan for the Todo app work.

Pre-plan checkpoint:

- Confirm the SDLC artifact chain exists and the Todo FEATURE is validated or has only explicitly accepted non-blocking issues.
- Confirm the Todo FEATURE is the governing artifact for implementation; the brainstorm cache or wrap-up summary is only the original input evidence.
- Confirm the bounded change target for the first phase: one backend/API slice first, then one React UI slice, then validation and review.
- Treat scope/content approval and later file-write approval as separate decisions.

Claude Code prompt:

```text
/cf-plan create a small implementation plan for the Todo FEATURE artifact.
Treat the registered Todo FEATURE path from `.cf-studio/config/artifacts.toml` as the governing artifact.
Assume the first phase is a bounded backend/API slice, the second phase is a bounded React UI slice, and the final phase is validation plus review.
The first phase must also create the project shell (package.json, dependencies, the dev:api/dev:ui/test/typecheck/build scripts, .gitignore, root tsconfig, and the Vite ui/) before or with the backend code, since the app is built here from the FEATURE.
Preserve SDLC kit traceability at the artifact level. Defer code marker and codebase scan-root decisions until implementation begins.
The plan must build one TypeScript backend/API slice and one React UI slice.
Use the actual course repo shape:
- backend/API files belong under src/server/ and tests/
- React UI files belong under ui/src/
- do not invent backend/src/ or frontend/src/ directories
Keep phases small. Include validation and review evidence.
Do not implement yet.
```

Codex prompt:

```text
$cf-plan create a small implementation plan for the Todo FEATURE artifact.
Treat the registered Todo FEATURE path from `.cf-studio/config/artifacts.toml` as the governing artifact.
Assume the first phase is a bounded backend/API slice, the second phase is a bounded React UI slice, and the final phase is validation plus review.
The first phase must also create the project shell (package.json, dependencies, the dev:api/dev:ui/test/typecheck/build scripts, .gitignore, root tsconfig, and the Vite ui/) before or with the backend code, since the app is built here from the FEATURE.
Preserve SDLC kit traceability at the artifact level. Defer code marker and codebase scan-root decisions until implementation begins.
The plan must build one TypeScript backend/API slice and one React UI slice.
Use the actual course repo shape:
- backend/API files belong under src/server/ and tests/
- React UI files belong under ui/src/
- do not invent backend/src/ or frontend/src/ directories
Keep phases small. Include validation and review evidence.
Do not implement yet.
```

When `cf-plan` starts it first opens an explore/brainstorm gate (`Before assessing scope, explore project resources or brainstorm decisions — or skip straight to assessment? Reply with a number.`, options `1 explore` / `2 brainstorm` / `3 skip`). The FEATURE already defines the work, so reply `3` (skip).

Expected result:

- A plan directory under `.cf-studio/.plans/` when plan writes are available.
- `plan.toml` as the canonical manifest.
- Supporting `brief-*.md` and `phase-*.md` files.
- A next-phase execution prompt or equivalent "run this phase next" instruction.
- The response explicitly reports the created plan path.

If the plan workflow asks how completed plans should be handled (lifecycle: `gitignore` / `cleanup` / `archive` / `manual`), choose:

```text
gitignore
```

This keeps the generated plan files available locally while `.cf-studio/.plans/` remains out of version control. This is the recommended course path: the student can inspect `plan.toml`, briefs, and phase files throughout the course without committing temporary planning artifacts.

Before confirming plan file writes, read the decomposition preview. If it proposes output paths like `backend/src/...` or `frontend/src/...`, do not answer `y` yet. Correct the plan in chat and require the repo shape from this lesson: `src/server/`, `tests/`, and `ui/src/`.

After the manifest and briefs are written, the plan workflow asks how to produce the compiled phase files:

```text
Brief package prepared (plan.toml + N briefs, 0/N phase files) — choose how to produce phase files: 1 inline (uses this chat's budget); 2 prompts (skips validation); 3 subagents (needs sub-agent approval); 4 stop (keep briefs). Reply with a number.
```

For this course, choose:

```text
3
```

This runs `cf-phase-compiler` subagents for each brief. It keeps the main chat focused and lets each phase file be compiled from its own brief. After the subagents finish, confirm that `phase-01-*.md`, `phase-02-*.md`, and `phase-03-*.md` exist under the plan directory before moving to execution.

When the plan passes self-validation and the workflow asks for the next action, choose:

```text
1
```

This runs a dedicated `/cf-analyze` review of the plan before execution. Treat this as the plan gate: execute phase 1 only after the review has no blockers or after you explicitly accept any non-blocking findings.

If the host returns a chat-only plan instead of plan files, treat that as a fallback, not equal plan truth. Ask for a file-backed plan when possible.

Claude Code prompt:

```text
/cf-plan restate this Todo plan as a canonical plan with plan.toml, brief files, and phase files if the host can write them. Do not implement yet.
```

Codex prompt:

```text
$cf-plan restate this Todo plan as a canonical plan with plan.toml, brief files, and phase files if the host can write them. Do not implement yet.
```

If plan files still cannot be produced, copy the next-phase prompt into `docs/course-notes.md` and record that no canonical plan artifacts were created yet.

If the path gets lost, recover the newest manifest from the repo root:

```bash
find .cf-studio/.plans -name plan.toml -exec ls -t {} + | head -n 1
```

Open the plan manifest and inspect:

- manifest path;
- phase order;
- brief files;
- phase files;
- next phase prompt;
- inputs;
- outputs;
- status;
- acceptance criteria.

Checkpoint:

- Paste the plan path into `docs/course-notes.md`.
- Write the next phase you would execute and why.

### Lesson 3.4. Plan Lifecycle States

A plan can be valid even when not every generated file is present forever.

Know these `plan.execution_status` values:

- `not_started`: plan exists but execution has not begun.
- `briefs_only`: planning emitted briefs but not compiled phase files yet.
- `prompts_emitted`: prompts exist for downstream execution; compiled phase files may not be present.
- `in_progress`: execution has started.
- `failed`: execution or validation failed and needs triage.
- `done`: the planned work reached its terminal state.

Also know these `plan.lifecycle_status` values:

- `pending`: lifecycle handling has not started.
- `ready`: lifecycle action is ready to run.
- `in_progress`: lifecycle action is currently running or was interrupted mid-action.
- `done`: lifecycle action completed successfully.
- `failed`: lifecycle action failed and needs triage.
- `partial`: cleanup completed only partly; keep the receipt and inspect what remains.
- `manual_action_required`: manual lifecycle work is required before the plan can be treated as closed.

Lifecycle cleanup can intentionally remove `brief-*`, `phase-*`, or `out/` files after the plan is finished. Lifecycle archive can move the plan under `.cf-studio/.plans/.archive/...`.

Evidence rule:

- Active plan with compiled phases: cite `plan.toml`, relevant `brief-*`, and relevant `phase-*`.
- `briefs_only` or `prompts_emitted`: cite `plan.toml`, emitted prompts/briefs, and explain that phase files were not generated yet.
- Cleanup: cite the terminal `plan.toml` receipt and note that compiled files were intentionally removed.
- Archive: cite the archived plan path or `active_plan_dir` / archive reference that points to it.

Do not treat every missing `phase-*.md` as failure. Treat it as failure only when the manifest says compiled phases should exist and there is no lifecycle explanation.

### Lesson 3.5. Execute One Compiled Phase As The Canonical Work Unit

In Constructor Studio, the compiled `phase-*.md` file is the canonical work unit. Do not execute from chat memory when a compiled phase exists.

Do this:

1. Open `plan.toml`.
2. Confirm `plan.execution_status`, `plan.lifecycle_status`, and each `phases[].status`.
3. Select the next ready phase from the manifest state, not from memory.
4. Open only that `phase-*.md` file and treat it as the authoritative instructions for the phase.
5. If your host offers guarded same-chat native execution for compiled phases, use that for the selected phase.
6. If same-chat native execution is unavailable, generate or use the new-chat startup prompt contract: the new chat must read `plan.toml`, resolve the next phase from manifest state, verify dependencies and outputs, update status through the phase-runner contract, then execute the selected phase file.
7. Treat `cfs delegate` as an optional advanced branch only when you explicitly choose RalphEx-style delegated execution:

```bash
cfs delegate ".cf-studio/.plans/todo-implementation-20260527"
```

Do not make `cfs delegate` the default Todo course execution path.
8. After execution, reopen `plan.toml` and record the status progression from disk.
9. Save the emitted next-phase prompt into `docs/course-notes.md`.

Use only the execution surface your installed Studio version and host actually expose. Record which one you used: guarded same-chat native execution, new-chat startup prompt execution, or optional `cfs delegate` handoff.

New-chat startup prompt when same-chat native execution is unavailable.

Claude Code prompt:

```text
I have a Constructor Studio execution plan ready at:
  .cf-studio/.plans/todo-implementation-20260527/plan.toml

Please read the plan manifest, then execute the next ready phase.
Treat plan.toml on disk as the source of truth for phase status.
Resolve the target phase from the manifest state unless I explicitly name a phase.
Verify dependencies, output paths, and lifecycle-state exceptions before executing.
Read only the selected phase file after manifest resolution.
Follow the phase file exactly; it is self-contained and authoritative.
Update plan.toml with the resulting phase status and aggregate execution state.
After completion, report results and generate the prompt for the next phase.
```

Codex prompt:

```text
I have a Constructor Studio execution plan ready at:
  .cf-studio/.plans/todo-implementation-20260527/plan.toml

Please read the plan manifest, then execute the next ready phase.
Treat plan.toml on disk as the source of truth for phase status.
Resolve the target phase from the manifest state unless I explicitly name a phase.
Verify dependencies, output paths, and lifecycle-state exceptions before executing.
Read only the selected phase file after manifest resolution.
Follow the phase file exactly; it is self-contained and authoritative.
Update plan.toml with the resulting phase status and aggregate execution state.
After completion, report results and generate the prompt for the next phase.
```

Status rule:

- Use the manifest statuses exactly as written on disk: `pending`, `in_progress`, `done`, or `failed`.
- Do not invent alternate phase labels in your notes.
- Read the status changes from `plan.toml` after execution. Do not infer them from chat memory.

Checkpoint:

- `docs/course-notes.md` records the selected `phase-*.md` path, the exact `phases[].status` evidence copied from `plan.toml` before and after execution, and the next-phase prompt.
- `docs/course-notes.md` also explains why that phase was the correct next phase based on the manifest state, not memory or guesswork.

### Lesson 3.6. Recovery From A Bad Plan

A bad plan is usually too broad, not evidence-based, or missing validation.

If the plan tries to build everything in one step, recover with a read-only review first.

Claude Code prompt:

```text
/cf-plan review this plan for unsafe scope, missing validation, missing review evidence, and unclear Todo acceptance criteria. Do not modify files.
```

Codex prompt:

```text
$cf-plan review this plan for unsafe scope, missing validation, missing review evidence, and unclear Todo acceptance criteria. Do not modify files.
```

Then ask for a narrower plan.

Claude Code prompt:

```text
/cf-plan revise the Todo implementation plan so the first phase only creates the backend/API model and operations, the second phase connects the React UI, and the final phase validates and prepares the handoff.
Keep the Todo FEATURE artifact as the governing artifact and preserve SDLC traceability markers.
```

Codex prompt:

```text
$cf-plan revise the Todo implementation plan so the first phase only creates the backend/API model and operations, the second phase connects the React UI, and the final phase validates and prepares the handoff.
Keep the Todo FEATURE artifact as the governing artifact and preserve SDLC traceability markers.
```

Checkpoint:

- Your plan has separate implementation, validation, and review points.

## Module 4. Implement The TypeScript HTTP API Slice

### Lesson 4.0. Pre-Implementation Command Gate

You are now about to write product code. The backend implementation step creates the project shell (`package.json`, dependencies, the package scripts, `src/server/`, and the Vite `ui/`) along with the backend code, so confirm the plan for that first.

The core path uses this command contract:

```bash
npm run dev:api
npm run dev:ui
npm test
npm run typecheck
npm run build
```

`dev:api`, `typecheck`, and `build` must become real implementation/validation commands. The backend implementation step creates `package.json`, the dependencies, and these scripts. Do not start the backend slice without a plan to make them pass in or before the backend implementation write.

If the planned TypeScript HTTP API and React client cannot be supported by the repo, do not invent a different core architecture mid-course. Stop, record the gap in `docs/course-notes.md`, and get approval for an alternate setup.

Choose the implementation traceability mode now:

- `FULL`: code will include Constructor Studio markers for implemented FEATURE flows, algorithms, states, and definitions of done; register codebase scan roots before writing product code.
- `DOCS-ONLY`: code stays free of Constructor Studio markers; keep traceability through artifacts, validation notes, and review evidence.

For this course, prefer `FULL` if you want to practice marker scanning end to end. Choose `DOCS-ONLY` only if the goal of the run is artifact practice rather than code-marker practice. Record the choice in `docs/course-notes.md`.

If you choose `FULL` and the implementation roots are not registered yet, do one configuration-only pass now. This is the first point where codebase scan roots are actionable: the FEATURE exists, the implementation plan exists, and product code is about to be written.

Claude Code prompt:

```text
/cf-coding update only .cf-studio/config/artifacts.toml so Constructor Studio can scan the Todo course implementation roots for the already-created Todo FEATURE.
Approved write scope:
- .cf-studio/config/artifacts.toml
Required outcomes:
- backend codebase scan root covers src/server TypeScript files
- frontend codebase scan root covers ui/src TypeScript and TSX files
- existing PRD, ADR, DESIGN, DECOMPOSITION, and FEATURE registrations remain unchanged
Do not create product code.
Do not implement Todo behavior.
After writing, report the exact codebase entries and the FEATURE path they support.
```

Codex prompt:

```text
$cf-coding update only .cf-studio/config/artifacts.toml so Constructor Studio can scan the Todo course implementation roots for the already-created Todo FEATURE.
Approved write scope:
- .cf-studio/config/artifacts.toml
Required outcomes:
- backend codebase scan root covers src/server TypeScript files
- frontend codebase scan root covers ui/src TypeScript and TSX files
- existing PRD, ADR, DESIGN, DECOMPOSITION, and FEATURE registrations remain unchanged
Do not create product code.
Do not implement Todo behavior.
After writing, report the exact codebase entries and the FEATURE path they support.
```

### Lesson 4.1. Define The Backend/API Contract

Before asking the agent to write code, confirm that the backend/API contract exists in the SDLC artifacts.

The PRD should contain the user-visible requirements. DESIGN should contain the API and data model. FEATURE should contain CDSL flows, algorithms, states, definitions of done, and acceptance criteria. If these details are only in the brainstorm cache or wrap-up summary, stop and update the SDLC artifacts first.

The Todo FEATURE should express this behavior, either directly or by reference to DESIGN:

```markdown
## Backend/API Contract

Todo:
- id: string
- title: string
- completed: boolean
- createdAt: string

Operations:
- listTodos(): Todo[]
- createTodo(title: string): Todo
- toggleTodo(id: string): Todo
- deleteTodo(id: string): void

HTTP API:
- GET /api/todos -> Todo[]
- POST /api/todos -> Todo
- PATCH /api/todos/:id/toggle -> Todo
- DELETE /api/todos/:id -> 204

Rules:
- title must not be blank.
- createTodo trims title.
- toggleTodo fails clearly when the id is unknown.
- deleteTodo is idempotent only if the existing project already uses that convention; otherwise unknown id should fail clearly.
```

Checkpoint:

- The Todo FEATURE is the authoritative behavior boundary for implementation, tests, and semantic review.
- `docs/course-notes.md` records the FEATURE path and the IDs for list, create, toggle, delete, and related definitions of done.

### Lesson 4.2. Execute The Backend/API Plan Phase

Do not start a fresh implementation prompt here. Module 3 already created and reviewed the implementation plan; the compiled phase file is now the governing work unit. If you discover that the backend/API scope needs a new endpoint, rule, file area, or behavior that is not already covered by PRD, DESIGN, DECOMPOSITION, FEATURE, and the plan, stop and update the artifacts or plan first.

Run the next ready compiled phase from the plan manifest. In the normal course path, this is phase 1: the TypeScript backend/API slice.

Phase 1 also creates the project shell — `package.json`, dependencies, the `dev:api`/`dev:ui`/`test`/`typecheck`/`build` scripts, `.gitignore`, the root `tsconfig`, and the Vite `ui/` — before or alongside the backend code, exactly as the plan and FEATURE require. If your compiled phase 1 does not include this shell, update the plan before executing.

Claude Code prompt:

```text
I have a Constructor Studio execution plan ready at:
  .cf-studio/.plans/implement-todo-crud/plan.toml

Please read the plan manifest, then execute only phase 1: TypeScript Backend / API Slice.
Treat plan.toml on disk as the source of truth for phase status.
Verify dependencies, output paths, and lifecycle-state exceptions before executing.
Read only the selected phase file after manifest resolution.
Follow the phase file exactly; it is self-contained and authoritative.
Use the actual course repo shape: backend/API files under src/server/ and tests/, not backend/src/.
If the phase requires scope that is not documented in the SDLC artifacts or compiled phase file, stop and ask for an artifact/plan update instead of inventing behavior.
Update plan.toml with the resulting phase status and aggregate execution state.
After completion, report changed files, validation output, and the prompt for the next phase.
```

Codex prompt:

```text
I have a Constructor Studio execution plan ready at:
  .cf-studio/.plans/implement-todo-crud/plan.toml

Please read the plan manifest, then execute only phase 1: TypeScript Backend / API Slice.
Treat plan.toml on disk as the source of truth for phase status.
Verify dependencies, output paths, and lifecycle-state exceptions before executing.
Read only the selected phase file after manifest resolution.
Follow the phase file exactly; it is self-contained and authoritative.
Use the actual course repo shape: backend/API files under src/server/ and tests/, not backend/src/.
If the phase requires scope that is not documented in the SDLC artifacts or compiled phase file, stop and ask for an artifact/plan update instead of inventing behavior.
Update plan.toml with the resulting phase status and aggregate execution state.
After completion, report changed files, validation output, and the prompt for the next phase.
```

If your plan path differs, replace `.cf-studio/.plans/implement-todo-crud/plan.toml` with the exact manifest path produced in Module 3.

Expected result:

- Phase 1 status in `plan.toml` is updated from disk evidence.
- The project shell (`package.json`, dependencies, scripts, `.gitignore`, `ui/`) is created as part of phase 1.
- Backend/API files are created only in the repo shape approved by the plan and artifacts.
- Tests, build, or documented behavior proof are run according to the phase file.
- The agent reports the next-phase prompt without executing phase 2 yet.

If the agent tries to bypass the compiled phase and starts proposing a separate implementation pass, stop and redirect it to the plan manifest and phase file.

Checkpoint:

- `docs/course-notes.md` maps each changed backend/API file to at least one FEATURE flow, algorithm, state, or definition-of-done ID.

### Lesson 4.3. Validate The Backend/API Slice

Use the repo's normal validation command if it exists. Common examples:

```bash
npm test
npm run test
npm run typecheck
npm run lint
```

Constructor Studio validation:

```bash
cfs validate --local-only
```

If the repo is workspace-aware and all sources are reachable:

```bash
cfs validate
```

Expected result:

- You have validation output.
- Passing validation is not final approval.
- Validation evidence records the exact command, pass/fail result, and either a key output excerpt or a raw log path/reference.

If the repo has no test suite or no standard validation command, do not invent a broad setup just to satisfy the course. Record a TDD exception, run the narrowest available checks, such as one targeted test file, a typecheck, a lint command, or a local `cfs validate` pass, require concrete behavior proof, then record the missing-test or missing-command gap as a follow-up risk.

If validation fails, do not ask for a broad fix. Ask for a narrow triage.

Claude Code prompt:

```text
/cf-coding triage these Todo backend/API validation failures against the Todo FEATURE and DESIGN.
Return the smallest safe fix plan. Do not modify files.
```

Codex prompt:

```text
$cf-coding triage these Todo backend/API validation failures against the Todo FEATURE and DESIGN.
Return the smallest safe fix plan. Do not modify files.
```

Checkpoint:

- Paste the exact command, pass/fail result, and a short output excerpt or raw log reference into `docs/course-notes.md`.

## Module 5. Implement The React UI Slice

Context reset (optional): the backend slice is committed and the UI slice reads the FEATURE and plan from disk. A `/clear` or new chat here keeps context lean — re-activate (`/cf`; on Codex also re-send `disable autonomous mode`) first.

### Lesson 5.1. Define The UI Behavior

Confirm that this UI behavior exists in the Todo FEATURE and references the relevant DESIGN/API elements. If it does not, update FEATURE before generating UI code:

```markdown
## UI Contract

The React UI should let a user:
- see all todos;
- type a title;
- add a todo;
- toggle completed state;
- delete a todo.

The UI should show a simple empty state when there are no todos.
The UI does not need authentication, routing, or persistence beyond the course scope unless the existing app already has those conventions.

## Local Integration Contract

- Local API base in development: `http://localhost:3001`
- Vite UI in development: `http://localhost:5173`
- Preferred UI request shape: relative `/api/...` calls from the browser, forwarded by Vite proxy to `http://localhost:3001`
- If the repo already uses a different documented integration convention, record that convention in `docs/course-notes.md` before generating UI code
```

Checkpoint:

- The UI scope is bounded before generation begins.

### Lesson 5.2. Generate The UI Slice

Write boundary before generation:

- Approve the UI contract and bounded product scope first.
- Then approve the exact file-write scope for the UI slice. `cf-sdlc-implement` reports the target files, validation commands, write scope, and required traceability coverage before it writes, so you approve those exact paths.

Run generation.

Claude Code prompt:

```text
/cf-sdlc-implement implement the React UI slice for the Todo app from the Todo FEATURE artifact.
Approved write scope:
- ui/src/App.tsx
- ui/src/components/TodoList.tsx
- ui/src/api.ts
- docs/todocourse/features/todo-crud.md, or the actual registered Todo FEATURE path, only for checkbox/status updates after tests pass
- docs/todocourse/DECOMPOSITION.md, or the actual registered DECOMPOSITION path, only for parent feature status update after every task-tracked FEATURE item is complete
Approved validation commands:
- if a UI test harness exists: npm test -- TodoList
- if no UI test harness exists: npm run typecheck, npm run build, and the smoke checklist in Lesson 5.3
- npm run build
Scope:
- use the existing frontend conventions;
- connect to the Todo HTTP API shape already created;
- use the local integration contract: UI at http://localhost:5173 and API at http://localhost:3001 through Vite proxy or the repo's documented equivalent;
- implement only the FEATURE flows/definitions of done assigned to the UI slice;
- in FULL traceability mode, add or preserve scope markers and per-instruction `@cpt-begin` / `@cpt-end` block markers for implemented FEATURE IDs;
- if the repo has a runnable UI test harness, write a failing targeted UI test first, implement the minimal change to pass, then refactor;
- if the repo does not have a UI test harness, do not approve `npm test -- TodoList`; record a TDD exception, run `npm run typecheck`, `npm run build`, and the smoke checklist in Lesson 5.3, then report the testing gap as follow-up;
- update only the relevant FEATURE checkboxes/status after implementation and validation prove completion; otherwise leave them unchecked and record the gap;
- include only list, create, toggle, delete, and empty-state behavior;
- do not add authentication, routing, or deployment.
After writing, report changed files and validation steps.
```

Codex prompt:

```text
$cf-sdlc-implement implement the React UI slice for the Todo app from the Todo FEATURE artifact.
Approved write scope:
- ui/src/App.tsx
- ui/src/components/TodoList.tsx
- ui/src/api.ts
- docs/todocourse/features/todo-crud.md, or the actual registered Todo FEATURE path, only for checkbox/status updates after tests pass
- docs/todocourse/DECOMPOSITION.md, or the actual registered DECOMPOSITION path, only for parent feature status update after every task-tracked FEATURE item is complete
Approved validation commands:
- if a UI test harness exists: npm test -- TodoList
- if no UI test harness exists: npm run typecheck, npm run build, and the smoke checklist in Lesson 5.3
- npm run build
Scope:
- use the existing frontend conventions;
- connect to the Todo HTTP API shape already created;
- use the local integration contract: UI at http://localhost:5173 and API at http://localhost:3001 through Vite proxy or the repo's documented equivalent;
- implement only the FEATURE flows/definitions of done assigned to the UI slice;
- in FULL traceability mode, add or preserve scope markers and per-instruction `@cpt-begin` / `@cpt-end` block markers for implemented FEATURE IDs;
- if the repo has a runnable UI test harness, write a failing targeted UI test first, implement the minimal change to pass, then refactor;
- if the repo does not have a UI test harness, do not approve `npm test -- TodoList`; record a TDD exception, run `npm run typecheck`, `npm run build`, and the smoke checklist in Lesson 5.3, then report the testing gap as follow-up;
- update only the relevant FEATURE checkboxes/status after implementation and validation prove completion; otherwise leave them unchecked and record the gap;
- include only list, create, toggle, delete, and empty-state behavior;
- do not add authentication, routing, or deployment.
After writing, report changed files and validation steps.
```

If the skill named different files or commands, replace every sample path and command above before sending the prompt.

Expected result:

- A React component or UI route.
- Connection to the Todo backend/API or a clearly bounded adapter.
- No unrelated UI redesign.

If the project has no React setup, ask for a plan before adding one.

Claude Code prompt:

```text
/cf-plan the repo does not appear to have a React setup. Plan the smallest course-appropriate React UI setup for the Todo app, including validation and handoff evidence. Do not implement yet.
```

Codex prompt:

```text
$cf-plan the repo does not appear to have a React setup. Plan the smallest course-appropriate React UI setup for the Todo app, including validation and handoff evidence. Do not implement yet.
```

Checkpoint:

- `docs/course-notes.md` names the UI entry file or route and the backend/API contract or adapter it uses.

### Lesson 5.3. Validate The Full Project Slice

Run applicable commands:

```bash
npm test
npm run typecheck
npm run lint
npm run build
cfs validate --local-only
```

Capture the exact command, pass/fail result, and either a key output excerpt or raw log reference in `docs/course-notes.md`.

If some commands do not exist, do not add a new build or test stack just for the course. Record a TDD exception when a runnable test harness is missing, run the narrowest available checks, and record the missing validation surface as a follow-up gap.

Run one concrete smoke procedure and record it in `docs/course-notes.md` or `docs/review-handoff.md`:

1. Start the backend with `npm run dev:api`.
2. Start the UI with `npm run dev:ui`.
3. Open `http://localhost:5173`.
4. Confirm the UI can load the todo list through `/api/todos`.
5. Create one todo such as `Study Constructor Studio` and confirm it appears.
6. Toggle that todo and confirm the completed state changes without a page reload.
7. Delete that todo and confirm it disappears from the list.
8. Record `Step`, `Expected result`, `Observed result`, and the evidence location.

Then run semantic review.

Claude Code prompt:

```text
/cf-coding review the Todo backend/API and React UI changes against the Todo FEATURE, DESIGN, DECOMPOSITION, and PRD.
Focus on correctness, missing tests, scope creep, validation gaps, and review readiness.
Do not modify files.
```

Codex prompt:

```text
$cf-coding review the Todo backend/API and React UI changes against the Todo FEATURE, DESIGN, DECOMPOSITION, and PRD.
Focus on correctness, missing tests, scope creep, validation gaps, and review readiness.
Do not modify files.
```

Expected result:

- Findings are separated from fixes.
- You know which findings are blockers.
- You know whether another bounded `cf-coding` pass is needed.

Use this blocker rule:

- Blocker: violates the Todo FEATURE or upstream SDLC artifacts, fails validation, breaks a core user flow, loses required traceability, or widens scope unsafely.
- Defer: non-blocking polish, optional cleanup, or follow-up work that does not break the agreed slice.

Checkpoint:

- You have validation output, review findings, and a decision: accept, fix, or defer.

## Module 6. Fix Loop And Review Discipline

### Lesson 6.1. Fix One Finding At A Time

Do not ask the agent to "fix everything" unless the findings are clearly small and mechanical. For normal course work, fix one class of issue at a time.

Write boundary before remediation:

- First approve which findings are in scope for this fix pass.
- Then approve the exact file-write scope for the remediation.

Claude Code prompt:

```text
/cf-coding fix only the blocker findings from the Todo review.
Use the Todo FEATURE artifact as the governing implementation artifact, and check upstream DESIGN/DECOMPOSITION/PRD when a fix changes behavior or architecture.
Finding IDs/text:
- BLOCKER-1: createTodo accepts blank titles and violates the service contract rule that titles must not be blank after trimming.
- BLOCKER-2: toggleTodo does not fail clearly for an unknown id.
Target files:
- src/server/todoApi.ts
- src/server/todoStore.ts
- tests/todoApi.test.ts
Acceptance rules:
- title must not be blank.
- createTodo trims title.
- toggleTodo fails clearly when the id is unknown.
- preserve required `@cpt-*` markers for the affected FEATURE IDs.
Do not add new features.
After writing, report changed files, validation commands, and remaining risks.
```

Codex prompt:

```text
$cf-coding fix only the blocker findings from the Todo review.
Use the Todo FEATURE artifact as the governing implementation artifact, and check upstream DESIGN/DECOMPOSITION/PRD when a fix changes behavior or architecture.
Finding IDs/text:
- BLOCKER-1: createTodo accepts blank titles and violates the service contract rule that titles must not be blank after trimming.
- BLOCKER-2: toggleTodo does not fail clearly for an unknown id.
Target files:
- src/server/todoApi.ts
- src/server/todoStore.ts
- tests/todoApi.test.ts
Acceptance rules:
- title must not be blank.
- createTodo trims title.
- toggleTodo fails clearly when the id is unknown.
- preserve required `@cpt-*` markers for the affected FEATURE IDs.
Do not add new features.
After writing, report changed files, validation commands, and remaining risks.
```

Replace the example blocker text and file paths with your real findings, but keep the same tight structure. Do not fall back to vague placeholders such as "fix the blockers" or "update the needed files."

Then validate again:

```bash
npm test
npm run typecheck
cfs validate --local-only
```

Record the same evidence standard again: exact command, pass/fail, and key output excerpt or raw log reference.

Then run a post-fix semantic review against the current code before handoff.

Claude Code prompt:

```text
/cf-coding review the current Todo code after the blocker fixes against the Todo FEATURE, DESIGN, DECOMPOSITION, and PRD.
Focus on whether the blockers are actually resolved, whether validation gaps remain, and whether any new scope creep was introduced.
Do not modify files.
```

Codex prompt:

```text
$cf-coding review the current Todo code after the blocker fixes against the Todo FEATURE, DESIGN, DECOMPOSITION, and PRD.
Focus on whether the blockers are actually resolved, whether validation gaps remain, and whether any new scope creep was introduced.
Do not modify files.
```

Checkpoint:

- The fix loop contains generation, validation, review, and human decision.

### Lesson 6.2. Package The Review Evidence

Create `docs/review-handoff.md`:

```markdown
# Todo Review Handoff

## Scope
State the bounded slice that was approved and what is intentionally out of scope.

## Governing Artifact
Name the Todo FEATURE artifact as canonical for implementation. Also list upstream PRD, ADR, DESIGN, and DECOMPOSITION artifacts that govern this slice. Treat the brainstorm cache or wrap-up summary as original input evidence only.

## Plan Lifecycle Artifacts
Link the `plan.toml`, relevant `brief-*` and `phase-*` files when they still exist, archived plan path when archived, or terminal cleanup receipt when lifecycle cleanup intentionally removed compiled files.

## SDLC Traceability
| Layer | Artifact path | Key IDs or decisions | Validation evidence |
|---|---|---|---|
| PRD |  |  |  |
| ADR |  |  |  |
| DESIGN |  |  |  |
| DECOMPOSITION |  |  |  |
| FEATURE |  |  |  |
| CODEBASE implementation + traceability |  |  |  |

## Changed Files
List the actual edited files only.

## Validation
| Command | Scope | Pass/Fail/N/A | Output excerpt or raw log reference | Rerun after last blocker fix? |
|---|---|---|---|---|
| npm test | Todo API behavior |  |  |  |
| npm run build | React UI build |  |  |  |
| cfs validate --local-only | Studio local validation |  |  |  |
| cfs validate | Workspace/cross-artifact validation status |  |  |  |

Add one row for every supported validation command you ran. If a command is unsupported, mark it `N/A` here and explain it again in `Unsupported Commands / N/A Rationale`.

## Behavior Proof
| Flow | Steps or test | Expected result | Observed result | Evidence |
|---|---|---|---|---|
| List |  |  |  |  |
| Create |  |  |  |  |
| Toggle |  |  |  |  |
| Delete |  |  |  |  |

## Unsupported Commands / N/A Rationale
| Command | Why unsupported or not applicable | Replacement evidence |
|---|---|---|
|  |  |  |

## Review Findings
- Blockers fixed:
- Non-blocking findings deferred:
- Findings still open:

## Fixed
Map each fixed finding to the files or behavior it changed.

## Deferred
Explain why each deferred item is safe to defer.

## Remaining Risks
- Risk:
- Evidence:
- Why it is still open:

## Gate And Approval Decisions
- Content approval:
- File-write approval:
- Accept/Fix/Defer decision:
- Reviewer gate decision:

## Human Approval Needed
- Reviewer name or role:
- Exact approval requested:
- Risks this approval must cover:

## Submission Status
Choose one: `passing` | `incomplete` | `not passing`
Reason:
```

Fill it from actual evidence. Do not invent green checks.

Claude Code prompt:

```text
/cf-write-docs review docs/review-handoff.md for missing evidence, hidden risk, and unclear human approval boundary. Do not modify files.
```

Codex prompt:

```text
$cf-write-docs review docs/review-handoff.md for missing evidence, hidden risk, and unclear human approval boundary. Do not modify files.
```

Checkpoint:

- A reviewer can read the handoff and decide what to do next.

### Lesson 6.3. Core Path Complete Gate

After Module 6, the core operator path is complete.

Do not jump straight to the Capstone. The next modules turn the completed Todo slice into operational evidence: brownfield re-entry, workspace boundary awareness, teammate explanation, authoring extension, and governance. They are part of the required course path.

## Module 7. Brownfield And Workspace Evidence

### Lesson 7.1. Brownfield Retrofit

Treat the completed Todo app as if another teammate handed it to you tomorrow. The goal is not to rebuild it; the goal is to prove you can re-enter an existing Constructor Studio project safely, detect conventions, and avoid blind reinitialization.

Start with the brownfield gate, not with blind reinitialization.

- Verify `.cf-studio/` exists and the host integrations you need are current.
- Do not rerun `cfs init` on a healthy initialized repo.
- Do not regenerate agents unless the relevant host files are missing or stale.
- Use `cf-auto-config` to inspect and refresh inferred repo-local rules only when the current session has not already verified them.

In chat, activate Constructor Studio first:

```text
Claude Code activation command: /cf
Codex activation command: $cf
```

For the course drill, treat the current Todo repo as brownfield even though you created it earlier in the course. That forces you to practice re-entry discipline.

Before any product edit, inspect what was inferred and turn it into a safe brownfield plan:

If the inferred rules are wrong, run one bounded generate pass to fix only the repo-local rule source before any future product edits.

Claude Code prompt:

```text
/cf-auto-config

/cf-write-skills review the inferred project rules and call out anything that does not match how this Todo repo actually works. Do not modify files.

/cf-explore summarize current Todo app conventions, architecture boundaries, test conventions, and risky areas. Do not modify files.

/cf-plan create a safe brownfield re-entry plan for this already-initialized Todo repo before any future feature edits.
Constraints:
- phase 1 is inspection and convention alignment only;
- validate after each phase;
- surface human approval boundaries.
```

Codex prompt:

```text
$cf-auto-config

$cf-write-skills review the inferred project rules and call out anything that does not match how this Todo repo actually works. Do not modify files.

$cf-explore summarize current Todo app conventions, architecture boundaries, test conventions, and risky areas. Do not modify files.

$cf-plan create a safe brownfield re-entry plan for this already-initialized Todo repo before any future feature edits.
Constraints:
- phase 1 is inspection and convention alignment only;
- validate after each phase;
- surface human approval boundaries.
```

Expected result:

- A convention summary.
- A short list of inferred-rule fixes or confirmations.
- A risk list.
- A brownfield re-entry plan before future edits.

Checkpoint:

- `docs/course-notes.md` records the current conventions, the brownfield re-entry plan path or fallback note, and the first safe brownfield phase.

### Lesson 7.2. Multi-Repo Workspace

Run a workspace boundary check even when the course repo is currently single-repo. The goal is to prove whether your evidence is local-only or workspace-aware, not to pretend you have multiple repos.

Workspace model:

- In the normal course repo, docs and code live together. Record that validation is local-repo evidence unless you configure an explicit workspace.
- In a split repo, use a parent directory such as `~/todo-workspace/` that contains the orchestration repo plus sibling repos like `todo-docs/` and `todo-app/`.
- Run workspace commands from the orchestration repo root that owns the workspace config.
- If you need to scan a broader parent directory while keeping the workspace config in the orchestration repo, stay in that orchestration repo root and pass both `--root` and `--output .cf-workspace.toml`.
- Current CLI/code uses `.cf-workspace.toml` as the canonical standalone filename. Some older Studio workflow docs still mention `.studio-workspace.toml`; treat that as a legacy alias only, and do not keep both files in the same repo.

Workspace terminal flow when you intentionally configure split-repo evidence:

```bash
cfs workspace-init --root ~/todo-workspace/ --output .cf-workspace.toml
cfs workspace-add --name docs --path ../todo-docs --role artifacts
cfs workspace-add --name app --path ../todo-app --role codebase
cfs workspace-info
# only when you added one or more Git URL sources with --url
cfs workspace-sync
cfs validate
```

Required inspection commands for the course:

```bash
cfs where-defined --id cpt-todo-feature-todo-crud
cfs list-ids --source docs
cfs validate --local-only
cfs validate
cfs validate --source docs
cfs validate --source docs --local-only
cfs map --local-only
cfs map
```

Use `--source` when a workspace source named `docs` exists. If it does not exist, record that source-targeted validation is not available in this run and keep the `validate --local-only` versus `validate` comparison as your required evidence. `--local-only` controls whether validation stays local; `--source` controls which source is targeted. They are independent and can be combined.

Claude Code prompt:

```text
/cf-map show the local and workspace traceability edges that affect the Todo feature, and call out anything degraded or unresolved. Do not modify files.
```

Codex prompt:

```text
$cf-map show the local and workspace traceability edges that affect the Todo feature, and call out anything degraded or unresolved. Do not modify files.
```

Expected result:

- You know which repos are reachable and which are degraded.
- You know whether a source is a local path source or a Git URL source.
- You know that `workspace-sync` explicitly fetches or updates Git URL sources only; it does not update local path sources.
- You know whether validation and mapping are workspace-aware, local-only, source-targeted, or both source-targeted and local-only.
- You do not confuse workspace federation with project extensibility.

Recovery:

- If a source is unreachable, keep the evidence: `workspace-info` warnings, `workspace-sync` output, or the exact Git URL reachability failure.
- If `workspace-info` says a source is not cloned, do not guess; record the degraded state and run `workspace-sync` only for Git URL sources.
- Compare `cfs validate --local-only` with `cfs validate`, and compare `cfs map --local-only` with `cfs map`.
- Do not claim cross-repo health from local-only output.

Checkpoint:

- You have `workspace-info` output, one cross-repo evidence lookup, and one clear statement of what is local-only versus workspace-aware.

### Lesson 7.3. Failure And Large Input Recovery

When a request is too large, do not keep adding text to the same chat. Use a smaller unit of work.

Useful chat recovery.

Claude Code prompt:

```text
/cf-explore summarize this oversized Todo review input into the smallest safe review units, preserving exact filenames, findings, and follow-up questions. Do not modify files.
```

Codex prompt:

```text
$cf-explore summarize this oversized Todo review input into the smallest safe review units, preserving exact filenames, findings, and follow-up questions. Do not modify files.
```

Recovery drill:

| Problem | Recovery |
|---|---|
| Validation fails and the cause is unclear | Ask `cf-coding` to triage the failure and fix only the bounded blocker set. |
| `cfs validate --local-only` passes but workspace validation or CI fails | Compare `cfs validate --local-only` with `cfs validate`, compare `cfs map --local-only` with `cfs map`, and use `cf-map` if you need a read-only explanation of the degraded edges. |
| Review or validation mentions language/script issues | Use human review of the learner-facing copy plus the normal repo validation flow; if wording risk still matters, ask `cf-write-docs` to point out unclear passages without treating language review as a public `cfs` command. |
| Traceability shape is unclear | Optionally run `cfs map`, `cfs map --local-only`, or `cf-map` to see whether the missing edge is local or workspace-wide. |
| The host blocks writes because confirmation or safety gates were not satisfied | Give an explicit bounded write instruction, or restate `read-only` if this should be analysis only. If the host integration is stale, regenerate it and retry from repo root. |
| The host wrote during a review request | Stop, inspect the diff, revert only with human intent, then restart in a fresh read-only session. |

Explain the recovery state when needed.

Claude Code prompt:

```text
/cf-explain explain why the Todo validation or review state failed, which evidence is local-only versus workspace-wide, and the safest next recovery step. Do not modify files.
```

Codex prompt:

```text
$cf-explain explain why the Todo validation or review state failed, which evidence is local-only versus workspace-wide, and the safest next recovery step. Do not modify files.
```

Codex-safe checklist:

- Restate `read-only` when you want analysis.
- Start a fresh session when switching from generation to review.
- Inspect diffs after every implementation pass before asking for the next change.
- If source-of-truth files changed, regenerate host integrations before trusting host surfaces again.
- Use `/clear` only when that host surface exposes it.

Checkpoint:

- You can recover from an oversized or polluted session without weakening the evidence chain.

## Module 8. Explain, Onboard, And Teach The Project

### Lesson 8.1. Interactive Explanation

After the Todo project has code and evidence, ask Constructor Studio to explain it.

Claude Code prompt:

```text
/cf-explain explain the current Todo app architecture, evidence chain, and review status for a new teammate. Do not modify files.
```

Codex prompt:

```text
$cf-explain explain the current Todo app architecture, evidence chain, and review status for a new teammate. Do not modify files.
```

Expected result:

- A bounded explanation.
- No new product claims.
- Clear distinction between implemented behavior and pending review.

Checkpoint:

- Paste the explanation or a summary into `docs/course-notes.md`.

### Lesson 8.2. Review-Ready Explain Package

Keep Module 8 interactive by default. Use `cf-explain` when a teammate needs a live walkthrough or onboarding conversation.

Use `cf-explain` (package mode) here only when the Todo project is already review-ready and you want to package existing evidence into durable docs. If you want to change how explain packaging works, or use explain-package authoring as an extension exercise, treat that as Module 9 bridge work instead of normal onboarding.

Claude Code prompt:

```text
/cf-explain build the explain handoff package for the Todo app.
Audience: teammate joining the project.
Scope: Todo SDLC artifact chain, implemented Todo backend/API slice, React UI slice, validation output, traceability evidence, and review handoff.
Do not invent behavior that is not in the repo.
```

Codex prompt:

```text
$cf-explain build the explain handoff package for the Todo app.
Audience: teammate joining the project.
Scope: Todo SDLC artifact chain, implemented Todo backend/API slice, React UI slice, validation output, traceability evidence, and review handoff.
Do not invent behavior that is not in the repo.
```

Expected result:

- A package under a generated path such as `.cf-studio/.cache/explain/packages/todo-handoff-2026-05-27T120000Z/`.
- An `index.md` entry point plus portion files that explain the project.
- Source-grounded claims only.

Checkpoint:

- Open `index.md` first, inspect one portion file for source links and invented claims, then decide whether the package is ready to share.

## Module 9. Author And Extension Bridge

This module is not required to finish the Todo app. Enter it only after three gates are true:

- Your operator baseline is complete and you can run the normal plan/generate/analyze loop.
- You know which file is the editable source of truth for the behavior you want to change.
- The host integrations you plan to use have already been generated at least once.

### Lesson 9.1. Editable Truth Versus Generated Surfaces

Rule:

- Edit repo-local configuration and source-of-truth files.
- Regenerate host integrations.
- Do not edit generated host surfaces as if they were product truth.
- After any repo-local rule, prompt, agent, manifest, or kit-source change, regenerate host integrations before using those host surfaces again.

Concrete map:

| If you want to change... | Edit this source of truth | Do not treat this as truth |
|---|---|---|
| Project settings or workspace registration | `.cf-studio/config/core.toml` or standalone `.cf-workspace.toml` / inline `[workspace]` | Generated host files that merely consume those settings |
| System and artifact registry | `.cf-studio/config/artifacts.toml` | `.cf-studio/.gen/*` or host-generated summaries |
| Repo-local prompts, workflows, rules, or agents | Repo `manifest.toml`, included manifests, and the source files they point to | Generated host surfaces such as `.codex/agents/*.toml`, repo host integration files, or other generated agent wrappers |
| Manifest-driven kit resources | The resource file itself plus its binding in `core.toml` when applicable | Copied/generated outputs that were assembled from those bindings |

Host surfaces differ in file layout:

- Claude Code integrations are generated under `.claude/skills/` and `.claude/agents/`.
- Codex/OpenAI integrations use shared `.agents/skills/` plus `.codex/agents/*.toml`.
- In both cases, regenerate the host integration after source-of-truth changes, then reopen or reload the host before trusting the generated surface.

Checkpoint:

- You can name the editable source and the generated surface for one project rule, and you know when regeneration is required.

### Lesson 9.2. Choose The Extension Path First

Before you change any Module 9 rule, choose how that rule is meant to run:

| Path | Best for | Tradeoff |
|---|---|---|
| Native subagent path | Hosts with strong built-in subagent or skill execution | More host-specific behavior; less portable |
| Chat-only path | Portable repo-local prompts and bounded manual operator flow | More discipline required from the operator each time |
| Delegated `ralphex`-style path | Exported plans or isolated execution in another runner | Adds another execution boundary and another recovery surface |

Checkpoint:

- `docs/course-notes.md` names the chosen extension path and one reason it fits this Todo project.

### Lesson 9.3. Review Prompt, Workflow, Or Agent Instructions

Use the right review lens before rewriting behavior:

- Use `cf-write-skills` when the target behaves like an instruction contract, state machine, menu, or workflow router (it runs the PDSL-aware prompt/workflow/skill review); use `cfs pdsl validate` for deterministic PDSL block validation.
- Use `cf-write-skills` semantic review when the main risk is ambiguity, weak UX, unsafe write behavior, or missing approval boundaries.
- Use a prompt bug-finding review when you suspect hidden failure modes, contradictory routing, unsafe recovery, or regressions outside the happy path.

Use `cf-write-skills` when the target behaves like an instruction contract.

Claude Code prompt:

```text
/cf-write-skills review the project instruction or workflow file for state-machine correctness, unsafe defaults, missing stop points, and unclear user prompts.
```

Codex prompt:

```text
$cf-write-skills review the project instruction or workflow file for state-machine correctness, unsafe defaults, missing stop points, and unclear user prompts.
```

For a normal semantic review.

Claude Code prompt:

```text
/cf-write-skills review this project instruction for ambiguity, missing contracts, interaction UX issues, and unsafe write behavior. Do not modify files.
```

Codex prompt:

```text
$cf-write-skills review this project instruction for ambiguity, missing contracts, interaction UX issues, and unsafe write behavior. Do not modify files.
```

For a prompt bug-finding lens.

Claude Code prompt:

```text
/cf-write-skills review this project instruction for prompt bugs, hidden failure modes, contradictory routing, and unsafe recovery behavior. Do not modify files.
```

Codex prompt:

```text
$cf-write-skills review this project instruction for prompt bugs, hidden failure modes, contradictory routing, and unsafe recovery behavior. Do not modify files.
```

Expected result:

- A review memo, not an immediate rewrite.
- Clear distinction between prompt review and implementation.

Checkpoint:

- You can identify one ambiguity, one missing contract, and one human approval boundary.

### Lesson 9.4. Turn Review Findings Into A Bounded Fix Prompt

Do not jump from an instruction review straight into an open-ended rewrite. First convert the review into a bounded remediation handoff.

Use this exercise after any prompt, workflow, or agent review.

Claude Code prompt:

```text
/cf-write-skills convert these approved prompt/workflow/agent review findings into a bounded remediation handoff.
Return:
- the exact finding IDs or quoted findings in scope;
- the exact source-of-truth files to edit;
- the approvals that must exist before writing;
- the validation or read-back steps required after the fix;
- a final `cf-coding` fix prompt that does not widen scope.
Do not modify files.
```

Codex prompt:

```text
$cf-write-skills convert these approved prompt/workflow/agent review findings into a bounded remediation handoff.
Return:
- the exact finding IDs or quoted findings in scope;
- the exact source-of-truth files to edit;
- the approvals that must exist before writing;
- the validation or read-back steps required after the fix;
- a final `cf-coding` fix prompt that does not widen scope.
Do not modify files.
```

Checkpoint:

- You can turn review findings into a fix prompt that names exact files, exact findings, and exact post-fix checks.

### Lesson 9.5. Add One Bounded Project Rule

Example rule:

```markdown
# Todo Project Rule

Every public Todo operation must have at least one validation or test note in the review handoff.
```

Claude Code prompt:

```text
/cf-write-skills add a small project-local rule for Todo review evidence.
Scope:
- rule only;
- no product behavior change;
- after writing, explain which source files changed and which host integrations must be regenerated.
```

Codex prompt:

```text
$cf-write-skills add a small project-local rule for Todo review evidence.
Scope:
- rule only;
- no product behavior change;
- after writing, explain which source files changed and which host integrations must be regenerated.
```

Then regenerate the host you use:

```bash
cfs generate-agents --agent claude
# or
cfs generate-agents --agent openai
```

Checkpoint:

- You made one M9 extension that governs the project without changing Todo behavior.

## Module 10. Governance And Team Adoption

### Lesson 10.1. The Team Operating Rule

Team rule:

```text
No Todo feature is accepted until the governing artifact, changed files, validation output, semantic review, and human approval boundary are visible.
```

Host rule:

```text
Use the host-specific prompt card for the host you are running. Do not mix `/cf` and `$cf` in the same copied prompt. If a host surface looks stale, regenerate that host integration and rerun the relevant gate.
```

Plain meaning of human approval:

- A named reviewer or reviewer role makes a decision such as "approve for merge," "approve with listed deferrals," or "request changes."
- Record that decision in `docs/review-handoff.md`.
- Also record the open risks that reviewer is accepting, rejecting, or sending back.

Checkpoint:

- Your team rule names the evidence and the host difference.

### Lesson 10.2. CI And Validation

If your project has CI, map local commands to CI checks.

Example:

```markdown
| Evidence | Local command | CI check |
|---|---|---|
| TypeScript | npm run typecheck | typecheck |
| Tests | npm test | test |
| Studio validation | cfs validate --local-only | constructor-studio-validate |
```

Pinned-install discipline:

- This course is pinned to Constructor Studio `1.0.0`.
- If your local install or generated host files drift from the `1.0.0` course source, stop the run and reconcile before continuing.
- Reinstall the pinned `1.0.0` CLI from the same approved source you used in setup, regenerate the host integrations you actually use, and rerun validation.
- Do not treat Claude/Codex host surfaces as self-updating. Generated agent or prompt files stay stale until you regenerate and reload them.

Local-only versus workspace-aware validation:

| Command | Use it when | What it proves | What it does not prove | Example |
|---|---|---|---|---|
| `cfs validate --local-only` | You need a repo-local check, or workspace sources are missing or unreachable. | The current repo passes deterministic Studio checks using only local state. | It does not prove cross-repo reachability, workspace linkage, semantic correctness, or human approval. | Your app repo validates locally while the docs repo is offline. |
| `cfs validate` | The repo is workspace-aware and the needed sources are reachable. | The local repo and workspace-linked sources can be checked together under the current workspace config. | It still does not prove semantic correctness, product quality, or acceptance approval. | Docs and app repos both resolve, and cross-repo evidence can be checked before handoff. |

Remember:

- Local validation is not semantic review.
- Workspace-aware validation is stronger than local-only validation, but it is still not semantic review.
- CI passing is not human approval.
- Human review of learner-facing language stays outside the core Todo command canon. Use normal repo validation plus explicit reviewer judgement for wording quality.

### Lesson 10.3. Source-Truth Reconciliation Before Teaching Or Reuse

If you will teach, reuse, or adapt this course after the core Todo path, perform one explicit reconciliation pass against current source truth first.

Minimum deliverables:

- conflict table;
- approved phrasing list;
- exclusions or deferrals;
- reconciled routing/control-plane notes;
- version note confirming whether `1.0.0` still matches the real source you inspected.

Do not skip this because the draft "looks close enough." The learner-facing copy stays trustworthy only when the command canon and control-plane notes were explicitly reconciled.

Checkpoint:

- `docs/course-notes.md` includes one comparison row for `cfs validate --local-only` versus `cfs validate` and one sentence about what neither command proves.

### Lesson 10.4. Reference-Only Admin And Migration Topics

Some capabilities are real but not part of the core Todo path.

Reference-only means:

- Learn the term and when it applies.
- Do not run it in the capstone or list it in the final package unless your repo already depends on it or the assessor explicitly asks for it.

Reference-only examples:

- `cfs mirror` overrides: advanced admin material.
- Language governance review: keep it as human review plus normal validator evidence, not as a required Todo command.
- Cypilot migration commands: caveat material, not core coursework.

Cypilot migration caveat:

- deterministic stage can use the current v1.0.0 migration command documented by Studio for Cypilot-era projects;
- SDLC/OpenSpec migration uses the kit workflow `cf-studio migrate-openspec`; treat migration as a phased, code-verified, special-case workflow, not a Todo app command;
- during OpenSpec migration, code is treated as the ultimate source of truth, legacy spec claims may be rewritten to match actual code, outputs are registered with `FULL` traceability, and each phase gate requires explicit user approval before continuing;
- `.cf-workspace.toml` may be involved;
- preserved `@cpt-*` markers need attention;
- regenerated host integrations are required when migration touches agent files.

Treat migration as a special-case note, not as an ordinary Todo command canon item.

Checkpoint:

- You can mention migration without turning it into the Todo capstone.

## Module 11. Capstone

Context reset (optional): the capstone runs from the artifacts, plan, and code already on disk. Start it in a fresh chat to keep context lean — re-activate (`/cf`; on Codex also re-send `disable autonomous mode`) first.

### Capstone Goal

Produce a review-ready Todo package.

Your final package must include:

- brainstorm evidence: saved `.cf-studio/.cache/brainstorm/...` path when save mode was used, or the approved wrap-up summary recorded in `docs/course-notes.md`;
- SDLC artifact chain: PRD, ADR, DESIGN, DECOMPOSITION, and Todo FEATURE;
- `docs/course-notes.md`;
- the on-disk plan lifecycle evidence: active plan files, archived plan path, or terminal cleanup receipt as applicable;
- an explicit note for `briefs_only`, `prompts_emitted`, cleanup, or archive states when compiled phase files do not exist;
- TypeScript backend/API files, or a clear mapping to the existing architecture when that slice was already present;
- React UI files, or a clear mapping to the existing architecture when that slice was already present;
- validation output, including which commands passed, failed, or were not applicable;
- SDLC validation evidence, including artifact validation and code marker/coverage checks when available;
- behavior proof for list, create, toggle, and delete through targeted tests or a smoke checklist;
- semantic review findings;
- fixed findings;
- deferred findings with rationale;
- remaining risks;
- gate and approval decisions;
- `docs/review-handoff.md`;
- Module 7 brownfield/workspace evidence;
- Module 9 extension/governance note.

### Capstone Steps

1. Confirm setup.

```bash
cfs --version
cfs info
cfs validate-kits --kit sdlc
cfs validate --local-only
cfs validate --artifact docs/todocourse/PRD.md
cfs validate --artifact docs/todocourse/ADR/cpt-todocourse-adr-todo-architecture.md
cfs validate --artifact docs/todocourse/DESIGN.md
cfs validate --artifact docs/todocourse/DECOMPOSITION.md
cfs validate --artifact docs/todocourse/features/todo-crud.md
```

Replace every sample artifact path with the actual registered files in your repo.

If `cfs --version` does not resolve to `1.0.0`, stop and reconcile the install before continuing.

If Studio or kit behavior looks stale, stop the capstone run, reinstall the pinned `1.0.0` source you used in setup, regenerate the host integrations you use, and rerun validation. Do not assume the host surface refreshed itself.

2. Confirm the governing artifacts.

Claude Code prompt:

```text
/cf-sdlc-change-impact-analysis review the Todo SDLC artifact chain for unclear scope, missing acceptance evidence, broken references, and unsupported assumptions. Include the brainstorm cache path or approved wrap-up summary only as original input evidence. Do not modify files.
```

Codex prompt:

```text
$cf-sdlc-change-impact-analysis review the Todo SDLC artifact chain for unclear scope, missing acceptance evidence, broken references, and unsupported assumptions. Include the brainstorm cache path or approved wrap-up summary only as original input evidence. Do not modify files.
```

If PRD, ADR, DESIGN, DECOMPOSITION, or FEATURE is missing, create or repair those artifacts before planning code. Do not implement from brainstorm output alone.

3. Confirm or create the implementation plan.

If a current plan already exists, inspect `plan.toml` read-only first. Cite `plan.execution_status`, `plan.lifecycle_status`, and each `phases[].status` entry from disk before you choose the next phase.

If no current plan exists, or the current plan is stale after a scope or architecture change, use `cf-plan` to create or revise it.

Create-plan prompt.

Claude Code prompt:

```text
/cf-plan create a Todo implementation plan with backend/API, React UI, validation, findings triage, and handoff phases.
Use the Todo FEATURE artifact as the governing implementation artifact and preserve SDLC `@cpt-*` traceability.
Do not implement yet.
```

Codex prompt:

```text
$cf-plan create a Todo implementation plan with backend/API, React UI, validation, findings triage, and handoff phases.
Use the Todo FEATURE artifact as the governing implementation artifact and preserve SDLC `@cpt-*` traceability.
Do not implement yet.
```

Revise-plan prompt.

Claude Code prompt:

```text
/cf-plan revise the existing Todo implementation plan so it still has backend/API, React UI, validation, findings triage, and handoff phases.
Use the Todo FEATURE artifact as the governing implementation artifact and preserve SDLC `@cpt-*` traceability.
Do not implement yet.
```

Codex prompt:

```text
$cf-plan revise the existing Todo implementation plan so it still has backend/API, React UI, validation, findings triage, and handoff phases.
Use the Todo FEATURE artifact as the governing implementation artifact and preserve SDLC `@cpt-*` traceability.
Do not implement yet.
```

The capstone package is not complete if you can only point to a plan idea in chat. Keep the plan lifecycle artifacts on disk, or record a justified fallback in `docs/review-handoff.md`.

The plan response should report the created plan path. If it does not, recover it from the repo root:

```bash
find .cf-studio/.plans -name plan.toml -exec ls -t {} + | head -n 1
```

Before executing a phase in the capstone, cite the exact `phases[].status` entries from `plan.toml` in `docs/course-notes.md` and justify why the selected phase is next.
If your host offers guarded same-chat native execution for the selected compiled phase, use that. Otherwise use the new-chat startup prompt contract from Lesson 3.5 so the execution session reads `plan.toml`, resolves the phase from manifest state, updates status, and follows only the selected phase file. `cf-plan` is for plan creation or revision only.

4. Implement or finish the backend/API slice.

`cf-sdlc-implement` reports the target files, validation commands, write scope, FEATURE-sync scope, and traceability coverage before it writes; approve those exact paths.

Claude Code prompt:

```text
/cf-sdlc-implement implement or finish only the Todo TypeScript backend/API slice from the Todo FEATURE artifact.
Approved write scope:
- package.json, only to set scripts.dev:api to the real backend entrypoint after the API exists
- src/server/index.ts
- src/server/todoApi.ts
- src/server/todoStore.ts
- tests/todoApi.test.ts
- docs/todocourse/features/todo-crud.md, or the actual registered Todo FEATURE path, only for checkbox/status updates after tests pass
- docs/todocourse/DECOMPOSITION.md, or the actual registered DECOMPOSITION path, only for parent feature status update after every task-tracked FEATURE item is complete
Approved validation commands:
- npm test -- todoApi
- npm run build
- cfs validate --local-only
Report changed files and validation.
In FULL traceability mode, preserve scope markers and per-instruction `@cpt-begin` / `@cpt-end` block markers for implemented FEATURE IDs.
Switch `scripts.dev:api` to the real API entrypoint, such as `tsx src/server/index.ts`, before smoke testing.
Update only the relevant FEATURE checkboxes/status after implementation and validation prove completion; otherwise leave them unchecked and record the gap.
```

Codex prompt:

```text
$cf-sdlc-implement implement or finish only the Todo TypeScript backend/API slice from the Todo FEATURE artifact.
Approved write scope:
- package.json, only to set scripts.dev:api to the real backend entrypoint after the API exists
- src/server/index.ts
- src/server/todoApi.ts
- src/server/todoStore.ts
- tests/todoApi.test.ts
- docs/todocourse/features/todo-crud.md, or the actual registered Todo FEATURE path, only for checkbox/status updates after tests pass
- docs/todocourse/DECOMPOSITION.md, or the actual registered DECOMPOSITION path, only for parent feature status update after every task-tracked FEATURE item is complete
Approved validation commands:
- npm test -- todoApi
- npm run build
- cfs validate --local-only
Report changed files and validation.
In FULL traceability mode, preserve scope markers and per-instruction `@cpt-begin` / `@cpt-end` block markers for implemented FEATURE IDs.
Switch `scripts.dev:api` to the real API entrypoint, such as `tsx src/server/index.ts`, before smoke testing.
Update only the relevant FEATURE checkboxes/status after implementation and validation prove completion; otherwise leave them unchecked and record the gap.
```

Replace the sample paths and commands with the exact paths the skill reports before sending the real prompt.

5. Implement or finish the React UI slice.

`cf-sdlc-implement` reports the target files, validation commands, write scope, FEATURE-sync scope, and traceability coverage before it writes; approve those exact paths.

Claude Code prompt:

```text
/cf-sdlc-implement implement or finish only the Todo React UI slice from the Todo FEATURE artifact.
Approved write scope:
- ui/src/App.tsx
- ui/src/components/TodoList.tsx
- ui/src/api.ts
- docs/todocourse/features/todo-crud.md, or the actual registered Todo FEATURE path, only for checkbox/status updates after tests pass
- docs/todocourse/DECOMPOSITION.md, or the actual registered DECOMPOSITION path, only for parent feature status update after every task-tracked FEATURE item is complete
Approved validation commands:
- if a UI test harness exists: npm test -- TodoList
- if no UI test harness exists: npm run typecheck, npm run build, and the final smoke checklist
- npm run build
- cfs validate --local-only
Report changed files and validation.
In FULL traceability mode, preserve scope markers and per-instruction `@cpt-begin` / `@cpt-end` block markers for implemented FEATURE IDs.
Update only the relevant FEATURE checkboxes/status after implementation and validation prove completion; otherwise leave them unchecked and record the gap.
```

Codex prompt:

```text
$cf-sdlc-implement implement or finish only the Todo React UI slice from the Todo FEATURE artifact.
Approved write scope:
- ui/src/App.tsx
- ui/src/components/TodoList.tsx
- ui/src/api.ts
- docs/todocourse/features/todo-crud.md, or the actual registered Todo FEATURE path, only for checkbox/status updates after tests pass
- docs/todocourse/DECOMPOSITION.md, or the actual registered DECOMPOSITION path, only for parent feature status update after every task-tracked FEATURE item is complete
Approved validation commands:
- if a UI test harness exists: npm test -- TodoList
- if no UI test harness exists: npm run typecheck, npm run build, and the final smoke checklist
- npm run build
- cfs validate --local-only
Report changed files and validation.
In FULL traceability mode, preserve scope markers and per-instruction `@cpt-begin` / `@cpt-end` block markers for implemented FEATURE IDs.
Update only the relevant FEATURE checkboxes/status after implementation and validation prove completion; otherwise leave them unchecked and record the gap.
```

Replace the sample paths and commands with the exact paths the skill reports before sending the real prompt.

6. Finish Module 7 evidence before the final validation pass.

- Document the brownfield re-entry mapping: current conventions, what changed during the course, and what must stay untouched in future edits.
- Capture workspace boundary evidence: `cfs workspace-info` when configured, one traceability lookup, and whether `cfs validate` is local-only or workspace-aware in this repo.

7. Validate.

```bash
npm test
npm run typecheck
npm run build
cfs validate --local-only
```

If the repo is workspace-aware and the required sources are reachable, also run:

```bash
cfs validate
```

Also run SDLC/traceability checks through the host or CLI surfaces available in the repo:

Claude Code prompt:

```text
/cf-sdlc-implement validate code for the Todo FEATURE. Check `@cpt-*` marker references, missing implementations, orphan markers, and drift between code and FEATURE. Do not modify files.
```

Codex prompt:

```text
$cf-sdlc-implement validate code for the Todo FEATURE. Check `@cpt-*` marker references, missing implementations, orphan markers, and drift between code and FEATURE. Do not modify files.
```

Run only commands your repo actually supports. `npm` is an example, not a law. If your repo uses `pnpm`, `yarn`, or direct package scripts, use the equivalent commands. For every unsupported command, record `N/A` and the reason in `docs/review-handoff.md`.

Behavior proof is mandatory in the capstone. Use one of these:

- targeted automated tests that explicitly prove list, create, toggle, and delete; or
- a manual smoke checklist with the exact steps, expected result, and observed result for list, create, toggle, and delete.

If you cannot prove one of the four core behaviors, the capstone is not passing yet.

8. Review.

Claude Code prompt:

```text
/cf-coding review the final Todo app changes against the Todo FEATURE, DESIGN, DECOMPOSITION, and PRD. Focus on correctness, missing tests, scope creep, traceability gaps, validation gaps, review readiness, and remaining risk. Do not modify files.
```

Codex prompt:

```text
$cf-coding review the final Todo app changes against the Todo FEATURE, DESIGN, DECOMPOSITION, and PRD. Focus on correctness, missing tests, scope creep, traceability gaps, validation gaps, review readiness, and remaining risk. Do not modify files.
```

9. Fix blockers.

Use the same tight blocker-fix template from Lesson 6.1. Example:

Claude Code prompt:

```text
/cf-coding fix only the blocker findings from the final Todo review.
Use the Todo FEATURE artifact as the governing implementation artifact.
Finding IDs/text:
- BLOCKER-1: createTodo accepts blank titles and violates the trimmed non-empty title rule.
- BLOCKER-2: toggleTodo does not fail clearly for an unknown id.
Target files:
- src/server/todoApi.ts
- src/server/todoStore.ts
- tests/todoApi.test.ts
Acceptance rules:
- title must not be blank.
- createTodo trims title.
- toggleTodo fails clearly when the id is unknown.
- preserve required `@cpt-*` markers for affected FEATURE IDs.
Do not add new features.
After writing, report changed files, validation commands, and remaining risk.
```

Codex prompt:

```text
$cf-coding fix only the blocker findings from the final Todo review.
Use the Todo FEATURE artifact as the governing implementation artifact.
Finding IDs/text:
- BLOCKER-1: createTodo accepts blank titles and violates the trimmed non-empty title rule.
- BLOCKER-2: toggleTodo does not fail clearly for an unknown id.
Target files:
- src/server/todoApi.ts
- src/server/todoStore.ts
- tests/todoApi.test.ts
Acceptance rules:
- title must not be blank.
- createTodo trims title.
- toggleTodo fails clearly when the id is unknown.
- preserve required `@cpt-*` markers for affected FEATURE IDs.
Do not add new features.
After writing, report changed files, validation commands, and remaining risk.
```

After fixes, rerun the relevant validation commands and refresh the handoff evidence. A validation result from before the last fix does not close the loop.

Rerun behavior proof after the last blocker fix:

- If the blocker touched a core Todo flow, rerun the targeted tests for that flow or rerun the full list/create/toggle/delete smoke checklist.
- Replace stale behavior-proof entries in `docs/course-notes.md` and `docs/review-handoff.md`.
- If you cannot rerun the affected proof, mark the capstone `incomplete` or `not passing`.

Then run the final post-fix semantic review.

Claude Code prompt:

```text
/cf-coding review the final Todo app after blocker fixes against the Todo FEATURE, DESIGN, DECOMPOSITION, and PRD. Confirm whether the blocker findings are resolved, whether behavior proof is fresh, whether validation and traceability evidence are fresh, and whether any new scope creep or risk appeared. Do not modify files.
```

Codex prompt:

```text
$cf-coding review the final Todo app after blocker fixes against the Todo FEATURE, DESIGN, DECOMPOSITION, and PRD. Confirm whether the blocker findings are resolved, whether behavior proof is fresh, whether validation and traceability evidence are fresh, and whether any new scope creep or risk appeared. Do not modify files.
```

`docs/review-handoff.md` must cite this post-fix review result before submission.

Blockers are not deferrable in the capstone. Each blocker must be fixed and revalidated, or the submission must be marked incomplete or not passing. Only non-blocking findings may be deferred with rationale.

10. Package.

Fill `docs/review-handoff.md` with, at minimum:

- governing artifact;
- SDLC artifact chain and traceability evidence;
- plan artifacts or justified fallback;
- `docs/course-notes.md` as the checkpoint evidence log;
- changed files;
- validation commands with pass/fail/`N/A`;
- behavior proof for list, create, toggle, and delete;
- unsupported commands with reason;
- review findings;
- fixed findings;
- deferred findings with rationale;
- remaining risks;
- gate or approval decisions already made;
- human approval needed: reviewer name or role, exact decision requested, and open risks that decision must cover.

11. Optional author bridge.

Claude Code prompt:

```text
/cf-write-skills review one proposed project-local Todo rule or prompt improvement. Keep it as governance, not product behavior.
```

Codex prompt:

```text
$cf-write-skills review one proposed project-local Todo rule or prompt improvement. Keep it as governance, not product behavior.
```

### Capstone Rubric

| Area | Evidence required to pass |
|---|---|
| Source fidelity | `docs/review-handoff.md` names the governing artifact and uses repo-backed evidence only. |
| SDLC artifact chain | PRD, ADR, DESIGN, DECOMPOSITION, and FEATURE exist, validate or have justified non-blocking gaps, and the implementation follows FEATURE rather than the input brief alone. |
| Plan lifecycle | Active plan files, archived plan path, terminal cleanup receipt, or valid `briefs_only` / `prompts_emitted` evidence is present and matches `plan.toml`. |
| Scope control | Review output shows the Todo behavior stayed inside the Todo FEATURE and upstream SDLC artifacts, or any variance is explicitly approved through artifact updates first. |
| Backend/API evidence | The backend/API files are changed or explicitly mapped to the pre-existing architecture. |
| UI evidence | The React UI files are changed or explicitly mapped to the pre-existing architecture. |
| Behavior proof | There is explicit proof for list, create, toggle, and delete via targeted tests or a smoke checklist, and affected proof was rerun after the last blocker fix. |
| Validation discipline | Exact commands and outcomes are recorded per command, and the relevant commands were rerun after the last blocker fix. |
| Traceability discipline | Required `@cpt-*` markers are present or explicitly justified as not applicable, and marker/reference validation was run where available. |
| Review loop | Final post-fix semantic review findings exist, every blocker is fixed and revalidated, and only non-blocking findings are deferred with rationale. Any unfixed blocker means the capstone is incomplete or not passing. |
| M7 evidence | Brownfield re-entry and workspace boundary evidence are included. |
| Unsupported command handling | Every unsupported validation command is marked `N/A` with a reason in `docs/review-handoff.md`. |
| Dual-tool realism | Host differences are stated without claiming Claude/Codex parity. |
| Human approval | The reviewer role or person, requested decision, and open risks are plainly recorded. |

Final checkpoint:

- A human reviewer can understand what you built, how you validated it, what was reviewed, what remains risky, and whether the Todo app is ready to accept.

## Final Assessment

### Exact Submission Package

Submit:

- brainstorm evidence: saved `.cf-studio/.cache/brainstorm/...` path when save mode was used, or the approved wrap-up summary recorded in `docs/course-notes.md`;
- PRD, ADR, DESIGN, DECOMPOSITION, and Todo FEATURE artifacts;
- `docs/course-notes.md`;
- `docs/review-handoff.md`;
- active plan files, archived plan path, terminal cleanup receipt, or valid `briefs_only` / `prompts_emitted` evidence;
- the backend/API and React UI file set, or written architecture mappings for the slices that already existed;
- validation evidence for every supported command;
- SDLC validation and traceability evidence;
- behavior proof for list, create, toggle, and delete;
- submission status set to `passing`, `incomplete`, or `not passing` with a reason;
- final review findings plus fixed/deferred status;
- remaining risks and gate/approval decisions;
- Module 7 brownfield re-entry and workspace boundary evidence;
- Module 9 governance note.

### Assessor Checklist

- The governing FEATURE artifact exists and matches the implemented Todo behavior.
- The student can explain the boundary between PRD, ADR, DESIGN, DECOMPOSITION, FEATURE, and CODEBASE, using one concrete Todo example for each layer.
- Plan lifecycle evidence exists on disk, or the fallback is justified and credible.
- Validation commands are listed with pass/fail/`N/A`, and unsupported commands include reasons.
- Behavior proof exists for list, create, toggle, and delete.
- Claims about local-only versus workspace-aware validation match the commands actually run.
- The last blocker-fix step is followed by fresh validation evidence.
- Remaining risks and deferred findings are visible, not buried.
- No blocker is silently deferred. Any still-open blocker is marked as not passing or incomplete.
- Human approval is assigned to a person or role, with a concrete decision requested.

Binary completion rule:

- Complete only when every required package item exists and every evidence category has a concrete result, including local-only or workspace-aware status.
- If any required evidence item is missing, stale, or hand-waved, the capstone is incomplete.

## Appendix A. Command Reference

Use Appendix A while running the capstone, Appendix B when something goes wrong, and Appendix C when you need to explain where each capability fits in the course path.

Required or common in most runs:

```bash
cfs --version
cfs info
cfs validate-kits --kit sdlc
cfs validate --local-only
cfs validate --artifact docs/todocourse/PRD.md
cfs validate --artifact docs/todocourse/ADR/cpt-todocourse-adr-todo-architecture.md
cfs validate --artifact docs/todocourse/DESIGN.md
cfs validate --artifact docs/todocourse/DECOMPOSITION.md
cfs validate --artifact docs/todocourse/features/todo-crud.md
```

Claude Code quick prompts:

```text
/cf
/cf-brainstorm brainstorm the PRD-level product requirements for the Todo app: actors, goals, functional requirements, non-goals, constraints, acceptance criteria, and product scope boundaries. Do not plan implementation yet
/cf-sdlc-doc-prd make PRD for the Todo app from the approved brainstorm wrap-up
/cf-sdlc-doc-adr make the ADR for the Todo app from the PRD
/cf-sdlc-doc-design make the DESIGN for the Todo app from the PRD and ADR
/cf-sdlc-decompose decompose the Todo DESIGN into ordered feature scope
/cf-sdlc-doc-feature make FEATURE for todo-crud from DECOMPOSITION and DESIGN
/cf-plan create a bounded implementation plan for the Todo FEATURE
/cf-sdlc-implement implement the approved Todo backend/API slice from the Todo FEATURE
/cf-sdlc-implement implement the approved Todo React UI slice from the Todo FEATURE
/cf-coding review the Todo changes against the Todo FEATURE, DESIGN, DECOMPOSITION, and PRD
/cf-sdlc-implement validate code for the Todo FEATURE
```

Codex quick prompts:

```text
$cf
$cf-brainstorm brainstorm the PRD-level product requirements for the Todo app: actors, goals, functional requirements, non-goals, constraints, acceptance criteria, and product scope boundaries. Do not plan implementation yet
$cf-sdlc-doc-prd make PRD for the Todo app from the approved brainstorm wrap-up
$cf-sdlc-doc-adr make the ADR for the Todo app from the PRD
$cf-sdlc-doc-design make the DESIGN for the Todo app from the PRD and ADR
$cf-sdlc-decompose decompose the Todo DESIGN into ordered feature scope
$cf-sdlc-doc-feature make FEATURE for todo-crud from DECOMPOSITION and DESIGN
$cf-plan create a bounded implementation plan for the Todo FEATURE
$cf-sdlc-implement implement the approved Todo backend/API slice from the Todo FEATURE
$cf-sdlc-implement implement the approved Todo React UI slice from the Todo FEATURE
$cf-coding review the Todo changes against the Todo FEATURE, DESIGN, DECOMPOSITION, and PRD
$cf-sdlc-implement validate code for the Todo FEATURE
```

Workspace-aware checks:

```bash
cfs validate
cfs map
```

Claude Code prompt:

```text
/cf-auto-config
/cf-map explain local or workspace traceability edges for the Todo feature
```

Codex prompt:

```text
$cf-auto-config
$cf-map explain local or workspace traceability edges for the Todo feature
```

Course setup bootstrap:

```bash
cfs init
cfs kit install constructorfabric/studio-kit-sdlc
cfs info
cfs validate-kits --kit sdlc
cfs generate-agents --agent claude
cfs generate-agents --agent openai
```

During `cfs init`, accept the SDLC kit prompt if it appears. Use `cfs kit install constructorfabric/studio-kit-sdlc` if the kit was declined, skipped, missing, or not offered. `cfs validate-kits .` is useful as a broad kit-template check; `cfs validate-kits --kit sdlc` is the course's explicit SDLC-kit proof.

Workspace boundary commands:

```bash
cfs workspace-init --root ~/todo-workspace/ --output .cf-workspace.toml
cfs workspace-add --name docs --path ../todo-docs --role artifacts
cfs workspace-add --name app --path ../todo-app --role codebase
cfs workspace-info
cfs where-defined --id cpt-todo-feature-todo-crud
cfs list-ids --source docs
cfs validate --source docs
cfs validate --source docs --local-only
cfs map
```

Claude Code prompt:

```text
/cf-brainstorm choose the smallest safe first Todo app slice
/cf-write-skills review docs/project-workflow.md
/cf-explain build the explain handoff package for the Todo app
```

Codex prompt:

```text
$cf-brainstorm choose the smallest safe first Todo app slice
$cf-write-skills review docs/project-workflow.md
$cf-explain build the explain handoff package for the Todo app
```

## Appendix B. Troubleshooting

| Problem | Recovery |
|---|---|
| `cfs` not found | Repair install or PATH, then retry `cfs --version`. |
| `.cf-studio/` created in wrong directory | Stop, move to repo root, reinitialize intentionally. |
| Host ignores activation | Regenerate host integrations, reopen or reload host, retry from repo root. In Claude Code use `/cf`; in Codex use `$cf`. |
| Host writes when asked to analyze | Stop, inspect the diff, open a fresh session, restate read-only scope, and rerun the host gate before continuing. |
| Write is blocked by approval or a safety gate | Narrow the requested file scope, confirm the write explicitly, and retry through the correct write-capable workflow instead of forcing it. |
| Plan is too broad | Ask `cf-plan` to review the plan, then revise with smaller phases. |
| Validation fails | Triage and fix only blockers with `cf-coding`. |
| Local commands pass but CI fails | Compare the exact CI job command, package manager, working directory, environment, and workspace reachability. Record the mismatch in `docs/review-handoff.md` before claiming parity. |
| Missing `npm` scripts | Use the repo's real package manager or equivalent script entry point (`pnpm`, `yarn`, task runner, or direct command). Mark unsupported examples as `N/A` with a reason. |
| Input is too large for one review | Ask `cf-explore` to summarize or split the input into smaller review or fix phases, then continue with the smallest safe unit. |
| Workspace source unreachable | Record degraded state, use `workspace-info`, compare with local-only validation. |
| Review context is polluted | Start a fresh session or use host-specific clear behavior where available. |

Status cascade rule:

- Update FEATURE task checkboxes only after the matching implementation, markers, and tests/behavior proof pass.
- Update `featstatus` only after every task-tracked FEATURE item in that feature is complete.
- Update the parent DECOMPOSITION feature entry only after the FEATURE is complete and validation confirms the status is consistent.
- Record before/after FEATURE and DECOMPOSITION states in `docs/course-notes.md`.

## Appendix C. Module Map And Capability Summary

This course keeps traceability visible without letting it swallow the operator path.

Module map:

- Module 1. Orientation: what Constructor Studio adds.
- Module 2. Setup for Claude Code and Codex.
- Module 3. Create the SDLC artifact chain and plan the Todo work.
- Module 4. Implement the TypeScript HTTP API slice.
- Module 5. Implement the React UI slice.
- Module 6. Fix loop and review discipline.
- Module 7. Brownfield and workspace scenarios.
- Module 8. Explain, onboard, and teach the project.
- Module 9. Author and extension bridge.
- Module 10. Governance and team adoption.
- Module 11. Capstone.

Capability dispositions:

- Core path after Module 6: SDLC kit installation, PRD, ADR, DESIGN, DECOMPOSITION, FEATURE, bounded planning, compiled phase execution, backend generation, UI generation, validation, review, blocker-fix loop, and evidence packaging.
- Branch material: brownfield retrofit, workspace federation, explain packaging, author extension, and team governance.
- Added into core learning: SDLC artifact pipeline, plan lifecycle, routing/control plane, safety gates, host strategy, validation discipline, review discipline, traceability markers, and evidence capture in `docs/course-notes.md`.
- Reference-only: `cfs mirror`, human language review notes, and Cypilot migration.
- Excluded as canon: bare `cf-<workflow>` prompts as learner copy-paste examples. Course prompt cards use `/cf-<workflow>` for Claude Code and `$cf-<workflow>` for Codex.

## Appendix D. Routing And Control-Plane Glossary

Use this appendix when you need the under-the-hood states, not when you are simply trying to finish one bounded Todo phase.

- The `cf` skill loads its core rules at session start (`SessionInit` emits a load report), then `IntentRouting` offers the matching `cf-*` skill; there is no separate pre-routing guard unit.
- Intent routing offers the most relevant `cf-*` skill (tagged `(suggested)` when your prompt carries an intent).
- Compound `find + fix` requests go to `cf-coding`, which finds and then fixes through its review-fix loop.
- The size gates are separate:
  - raw input over about `500` lines hits the pre-routing overflow gate;
  - analyze stays safest within about `2000` lines of single-context material;
  - generate work estimated over about `2500` lines should escalate to `cf-plan`, which can decompose into smaller phases.
- `CF_PHASE_GATE` controls whether writes are allowed.
- `GIT_COMMIT_MODE` controls whether git actions may commit, stage, or do no git writes.
- `SUB_AGENTS_APPROVED` records whether native sub-agent execution was approved for the current chat session (with `SUB_AGENTS_INLINE` for the inline fallback).
- `INLINE_FALLBACK` is per workflow run; when `true`, the host falls back to inline or sequential execution instead of native sub-agent dispatch.
