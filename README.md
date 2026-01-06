# Agentic AI Workshop: Build Anything with Claude Code

A beginner-friendly workshop for going from messy idea to working app using Claude Code and AI agents.

**Goal:** Take a brain dump of an idea and turn it into something running locally in 1-2 hours.

**Audience:** Anyone! Works for terminal newbies, designers, PMs, musicians, artists - not just engineers.

---

## Prerequisites (Do These Before the Workshop)

1. **Laptop + charger + decent Wi-Fi**

2. **Claude Pro account ($20/mo)** - Sign up at [claude.ai](https://claude.ai)

3. **Install Claude Code** - Follow the [quickstart guide](https://docs.anthropic.com/en/docs/claude-code/quickstart)
   ```bash
   # After installing, test it works:
   claude --version
   ```

4. **Git installed** (optional but helpful)
   ```bash
   # Check if you have it:
   git --version
   ```

5. **Come with 1-3 tiny project ideas** (or pick from our suggestions below)

---

## Workshop Flow (90-120 minutes)

### Step 1: Setup Check (10 min)

Open your terminal and navigate to a project folder:
```bash
mkdir my-project
cd my-project
claude
```

You should see Claude Code start up. If you're on a subscription, run `/usage` to see your limits.

### Step 2: Brain Dump Your Idea (5 min)

Just talk (or type) your messy idea. Don't worry about structure. Examples:

> "I want an app where I can dump all my random ideas and it organizes them somehow"

> "A practice log for music - track what I practiced, how long, my mood"

> "Something to help me plan gifts for people with constraints like budget"

### Step 3: Create the Plan (15-20 min)

Use the **Planner agent** to turn your brain dump into a clear plan:

```
Use the planner agent to turn this idea into a plan:

[paste your brain dump here]
```

The agent will:
- Ask 3-5 clarifying questions
- Propose a tiny MVP
- Create a `plan.md` with scope, acceptance criteria, and Phase 1 tasks

**Review the plan.** Give feedback. Ask it to revise until you're happy.

### Step 4: Build It (30-45 min)

Use the **Builder agent** to implement Phase 1:

```
Use the builder agent to implement Phase 1 from plan.md.
Keep it simple and tell me how to run it when you're done.
```

The agent will:
- Build the minimal version
- Run it locally
- Give you the URL or command to see your app

**Important:** When Claude asks permission to run commands, read what it's doing. Ask it to explain if you're unsure.

### Step 5: Verify It Works (Optional, 10 min)

Use the **Verifier agent** for quick sanity checks:

```
Use the verifier agent to add some basic tests or a checklist.
Keep it light - just enough to know it works.
```

### Step 6: Demo Time!

Show what you built! Even "it runs and does one thing" is a win.

---

## The Agents

### Core Agents (Start Here)

| Agent | What It Does | When to Use |
|-------|--------------|-------------|
| **Planner** | Turns messy ideas into clear plans | Always start here |
| **Builder** | Implements Phase 1, gets it running | After you have a plan |
| **Verifier** | Adds light tests or checklist | Optional, after building |

### Advanced Agents (Use Later)

| Agent | What It Does | When to Use |
|-------|--------------|-------------|
| **Business Analyst** | Prioritizes features, cuts scope | When idea is too big |
| **TDD Developer** | Test-driven implementation | When quality > speed |

Find all prompts in the `/prompts` folder.

---

## Setting Up the Agents

### Option A: Create Agents with /agents command

In Claude Code, run `/agents` and follow the prompts. Paste the agent prompt from the `/prompts` folder.

### Option B: Just Use the Prompts Directly

You don't need formal agents. Just paste the prompt when you need it:

```
You are a Planner agent. Your job is to turn a messy idea into a clear, buildable plan...
[rest of prompt]

Now, turn this idea into a plan: [your idea]
```

---

## Project Ideas (If You Need Inspiration)

### For Musicians
- **Practice log** - Track what you practiced, minutes, mood; weekly summary
- **Setlist planner** - Drag/drop songs, total duration, key changes warning
- **Lyric fragments organizer** - Dump fragments, cluster themes, export drafts

### For Artists/Makers
- **Art prompt queue** - Ideas + tags + "next up" queue
- **Commission tracker** - Status board: inquiry → sketch → final → delivered
- **Palette vault** - Save hex palettes, name and search them

### For Everyone
- **Idea compost** - Dump random ideas, organize into clusters and plans
- **Meeting to actions** - Paste notes → tasks + owners + due dates
- **Gift idea generator** - Person + constraints → ranked gift list

**Rule of thumb:** If it needs OAuth, payments, or deployment - save it for later. Keep it local!

---

## Safety & Guardrails

- **Review permissions:** Claude will ask before running commands. Read them. Ask it to explain if unsure.
- **Stay in safe mode:** Avoid `--dangerously-skip-permissions` (yolo mode) unless you really know what you're doing.
- **Ask questions:** "Explain what this command does" is always valid.

---

## Token-Saving Tips

- Use the **Planner → Builder** flow (skip BA and TDD at first)
- Keep scope tiny: one feature, one screen, one file
- If running low, run `/compact` to reduce context
- Skip edge cases - get the happy path working first

---

## Resources

- [Claude Code Quickstart](https://docs.anthropic.com/en/docs/claude-code/quickstart)
- [Claude Prompting Best Practices](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
- [The Multiverse School](https://themultiverse.school/) - Great for learning fundamentals
- [Whispr](https://whispr.chat/) - Voice to text (models handle messy braindumps great)

---

## Instructor Notes

If you're running this workshop for others:

**Before the workshop:**
- Pick one stack (Python or Node) for everyone
- Have this repo cloned and ready to share
- Test the flow yourself first

**During the workshop:**
- Pair terminal newbies with someone comfortable
- Build in "regroup" pauses every 10-15 min
- Celebrate the first "it runs!" moment loudly

**What I learned running this:**
- Fewer agents = faster dopamine hit
- TDD burns tokens fast - save for advanced users
- People need explicit agent setup demos
- End with a clear "we're done, optional hangout now" ritual

---

## Questions?

Open an issue or reach out!
