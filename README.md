# TÂCHES Claude Code Resources

A growing collection of my favourite custom Claude Code resources in one place.

## Quick Start

```bash
# Clone the repo
git clone https://github.com/glittercowboy/taches-cc-resources.git
cd taches-cc-resources

# Install prompts
cp prompts/meta-prompting/*.md ~/.claude/commands/
cp prompts/todo-management/*.md ~/.claude/commands/
cp prompts/context-handoff/*.md ~/.claude/commands/

# Install skills
cp skills/create-agent-skills/commands/*.md ~/.claude/commands/
cp -r skills/create-agent-skills/skills/* ~/.claude/skills/
```

Commands install globally to `~/.claude/commands/`. Skills install to `~/.claude/skills/`. Project-specific data (prompts, todos) lives in each project's working directory.

## Prompts

### [Meta-Prompting](./prompts/meta-prompting/)

A systematic approach to building complex software by delegating prompt engineering to Claude itself. Instead of telling Claude what to do, you tell Claude what you want, and it figures out how to ask itself to do it.

Perfect for complex refactoring, new features, and multi-step tasks where you want rigorous specifications without manually crafting detailed prompts.

### [Todo Management](./prompts/todo-management/)

Capture ideas mid-conversation without losing focus. When you spot a bug, think of a feature, or notice something to refactor - but don't want to derail your current work - `/add-to-todos` captures it with full context. Later, `/check-todos` resumes exactly where you left off.

Perfect for staying focused while building a backlog of improvements, features, and research tasks that won't be forgotten.

### [Context Handoff](./prompts/context-handoff/)

Continue work in a fresh context without losing progress. `/whats-next` analyzes the current conversation and creates a structured handoff document with what was completed, what remains, and critical context. Reference it in your next chat to resume seamlessly.

Perfect for when your context is getting full, you need a clean slate, or you're switching between tasks and want to preserve exactly where you left off.

## Skills

### [Create Agent Skills](./skills/create-agent-skills/)

Build skills by describing what you want. `/create-agent-skill` asks clarifying questions, researches APIs if needed, and generates properly structured skill files. When things don't work perfectly, `/heal-skill` analyzes what went wrong and updates the skill based on what actually worked.

Perfect for packaging repeatable workflows—PDF processing, API integrations, chart generation—into skills that Claude can execute consistently. Let your mind go wild!

---

More resources coming soon.

---

**Community Ports:** [OpenCode](https://github.com/stephenschoettler/taches-oc-prompts)

—TÂCHES
