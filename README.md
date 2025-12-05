# TÂCHES Codex Resources

A growing collection of custom Codex resources built for real workflows.

## Philosophy

When you use a tool like Codex, it's your responsibility to assume everything is possible.

I built these tools using that mindset.

Dream big. Happy building.

— TÂCHES

## What's Inside

**[Prompts](#prompts)** (27 total) - Slash-style prompts that expand into structured workflows
- **Meta-Prompting**: Separate planning from execution with staged prompts
- **Todo Management**: Capture context mid-work, resume later with full state
- **Thinking Models**: Mental frameworks (first principles, inversion, 80/20, etc.)
- **Deep Analysis**: Systematic debugging methodology with evidence and hypothesis testing

**[Skills](#skills)** (7 total) - Autonomous workflows that research, generate, and self-heal
- **Create Plans**: Hierarchical project planning for solo developer + Codex workflows
- **Create Agent Skills**: Build new skills by describing what you want
- **Create Meta-Prompts**: Generate staged workflow prompts with dependency detection
- **Create Slash Commands**: Build custom prompts with proper structure
- **Create Subagents**: Build specialized Codex instances for isolated contexts
- **Create Hooks**: Build event-driven automation
- **Debug Like Expert**: Systematic debugging with evidence gathering and hypothesis testing

**[Agents](#agents)** (3 total) - Specialized subagents for validation and quality
- **skill-auditor**: Reviews skills for best practices compliance
- **slash-command-auditor**: Reviews prompts for proper structure
- **subagent-auditor**: Reviews agent configurations for effectiveness

## Installation

### Manual Install

```bash
# Clone the repo
git clone https://github.com/glittercowboy/taches-cc-resources.git
cd taches-cc-resources

# Install prompts
cp -r prompts/* ~/.codex/prompts/

# Install skills
cp -r skills/* ~/.codex/skills/
```

Prompts install globally to `~/.codex/prompts/`. Skills install to `~/.codex/skills/`. Project-specific data (prompts, todos) lives in each project's working directory.

## Prompts

### Meta-Prompting

Separate analysis from execution. Describe what you want in natural language, Codex generates a rigorous prompt, then runs it in a fresh sub-agent context.

- [`/create-prompt`](./prompts/create-prompt.md) - Generate optimized prompts with XML structure
- [`/run-prompt`](./prompts/run-prompt.md) - Execute saved prompts in sub-agent contexts

### Todo Management

Capture ideas mid-conversation without derailing current work. Resume later with full context intact.

- [`/add-to-todos`](./prompts/add-to-todos.md) - Capture tasks with full context
- [`/check-todos`](./prompts/check-todos.md) - Resume work on captured tasks

### Context Handoff

Create structured handoff documents to continue work in a fresh context. Reference with `@whats-next.md` to resume seamlessly.

- [`/whats-next`](./prompts/whats-next.md) - Create handoff document for fresh context

### Create Extensions

Wrapper prompts that invoke the skills below.

- [`/create-agent-skill`](./prompts/create-agent-skill.md) - Create a new skill
- [`/create-meta-prompt`](./prompts/create-meta-prompt.md) - Create staged workflow prompts
- [`/create-slash-command`](./prompts/create-slash-command.md) - Create a new slash command
- [`/create-subagent`](./prompts/create-subagent.md) - Create a new subagent
- [`/create-hook`](./prompts/create-hook.md) - Create a new hook

### Audit Extensions

Invoke auditor subagents.

- [`/audit-skill`](./prompts/audit-skill.md) - Audit skill for best practices
- [`/audit-slash-command`](./prompts/audit-slash-command.md) - Audit command for best practices
- [`/audit-subagent`](./prompts/audit-subagent.md) - Audit subagent for best practices

### Self-Improvement

- [`/heal-skill`](./prompts/heal-skill.md) - Fix skills based on execution issues

### Thinking Models

Apply mental frameworks to decisions and problems.

- [`/consider:pareto`](./prompts/consider/pareto.md) - Apply 80/20 rule to focus on what matters
- [`/consider:first-principles`](./prompts/consider/first-principles.md) - Break down to fundamentals and rebuild
- [`/consider:inversion`](./prompts/consider/inversion.md) - Solve backwards (what guarantees failure?)
- [`/consider:second-order`](./prompts/consider/second-order.md) - Think through consequences of consequences
- [`/consider:5-whys`](./prompts/consider/5-whys.md) - Drill to root cause
- [`/consider:occams-razor`](./prompts/consider/occams-razor.md) - Find simplest explanation
- [`/consider:one-thing`](./prompts/consider/one-thing.md) - Identify highest-leverage action
- [`/consider:swot`](./prompts/consider/swot.md) - Map strengths, weaknesses, opportunities, threats
- [`/consider:eisenhower-matrix`](./prompts/consider/eisenhower-matrix.md) - Prioritize by urgent/important
- [`/consider:10-10-10`](./prompts/consider/10-10-10.md) - Evaluate across time horizons
- [`/consider:opportunity-cost`](./prompts/consider/opportunity-cost.md) - Analyze what you give up
- [`/consider:via-negativa`](./prompts/consider/via-negativa.md) - Improve by removing

### Deep Analysis

Systematic debugging with methodical investigation.

- [`/debug`](./prompts/debug.md) - Apply expert debugging methodology to investigate issues

## Agents

Specialized subagents used by the audit prompts.

- [`skill-auditor`](./agents/skill-auditor.md) - Expert skill auditor for best practices compliance
- [`slash-command-auditor`](./agents/slash-command-auditor.md) - Expert slash command auditor
- [`subagent-auditor`](./agents/subagent-auditor.md) - Expert subagent configuration auditor

## Skills

### [Create Plans](./skills/create-plans/)

Hierarchical project planning optimized for solo developer + Codex. Create executable plans that Codex runs, not enterprise documentation that sits unused.

**PLAN.md IS the prompt** - not documentation that gets transformed later. Brief → Roadmap → Research (if needed) → PLAN.md → Execute → SUMMARY.md.

**Domain-aware:** Optionally loads framework-specific expertise from `~/.codex/skills/expertise/` (e.g., macos-apps, iphone-apps) to make plans concrete instead of generic. Domain expertise skills are created with [create-agent-skills](#create-agent-skills) - exhaustive knowledge bases (5k-10k+ lines) that make task specifications framework-appropriate.

**Quality controls:** Research includes verification checklists, blind spots review, critical claims audits, and streaming writes to prevent gaps and token limit failures.

**Context management:** Auto-handoff at 10% tokens remaining. Git versioning commits outcomes, not process.

**Commands:** `/create-plan` (invoke skill), `/run-plan <path>` (execute PLAN.md with intelligent segmentation)

See [create-plans README](./skills/create-plans/README.md) for full documentation.

### [Create Agent Skills](./skills/create-agent-skills/)

Build skills by describing what you want. Asks clarifying questions, researches APIs if needed, and generates properly structured skill files.

**Two types of skills:**
1. **Task-execution skills** - Regular skills that perform specific operations
2. **Domain expertise skills** - Exhaustive knowledge bases (5k-10k+ lines) that live in `~/.codex/skills/expertise/` and provide framework-specific context to other skills like [create-plans](#create-plans)

**Context-aware:** Detects if you're in a skill directory and presents relevant options. Progressive disclosure guides you through complex choices.

When things don't work perfectly, `/heal-skill` analyzes what went wrong and updates the skill based on what actually worked.

Prompts: `/create-agent-skill`, `/heal-skill`, `/audit-skill`

### [Create Meta-Prompts](./skills/create-meta-prompts/)

The skill-based evolution of the meta-prompting system. Builds prompts with structured outputs (research.md, plan.md) that subsequent prompts can parse. Adds automatic dependency detection to chain research → plan → implement workflows.

**Note:** For end-to-end project building, consider [create-plans](#create-plans) - it's the more structured evolution of this approach with full lifecycle management (brief → roadmap → execution → handoffs). Use create-meta-prompts for abstract workflows and Codex→Codex pipelines. Use create-plans for actually building projects.

Prompts: `/create-meta-prompt`

### [Create Slash Commands](./skills/create-slash-commands/)

Build slash-style prompts that expand into full workflows when invoked. Describe the prompt you want, get proper YAML configuration with arguments, tool restrictions, and dynamic context loading.

Prompts: `/create-slash-command`, `/audit-slash-command`

### [Create Subagents](./skills/create-subagents/)

Build specialized Codex instances that run in isolated contexts. Describe the agent's purpose, get optimized system prompts with the right tool access and orchestration patterns.

Prompts: `/create-subagent`, `/audit-subagent`

### [Create Hooks](./skills/create-hooks/)

Build event-driven automation that triggers on tool calls, session events, or prompt submissions. Describe what you want to automate, get working hook configurations.

Prompts: `/create-hook`

### [Debug Like Expert](./skills/debug-like-expert/)

Deep analysis debugging mode for complex issues. Activates methodical investigation protocol with evidence gathering, hypothesis testing, and rigorous verification. Use when standard troubleshooting fails or when issues require systematic root cause analysis.

Prompts: `/debug`

---

## Recommended Workflow

**For building projects:** Use `/create-plan` to invoke the [create-plans](#create-plans) skill. After planning, use `/run-plan <path-to-PLAN.md>` to execute phases with intelligent segmentation. This provides hierarchical planning (BRIEF.md → ROADMAP.md → phases/PLAN.md), domain-aware task generation, context management with handoffs, and git versioning.

**For domain expertise:** Use [create-agent-skills](#create-agent-skills) to create exhaustive knowledge bases in `~/.codex/skills/expertise/`. These skills are automatically loaded by create-plans to make task specifications framework-specific instead of generic.

**Other tools:** The [create-meta-prompts](#create-meta-prompts-1) skill and `/create-prompt` + `/run-prompt` commands are available for custom Codex→Codex pipelines that don't fit the project planning structure.

---

More resources coming soon.

---

**Community Ports:** [OpenCode](https://github.com/stephenschoettler/taches-oc-prompts)

—TÂCHES
