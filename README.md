# Agentic AI Workshop: Build Anything with Claude Code

A beginner-friendly workshop for going from messy idea to working app using Claude Code and AI agents.

**Goal:** Take a brain dump of an idea and turn it into something running in your browser (localhost) in 1-2 hours.

**Audience:** Anyone! Works for complete beginners, designers, PMs, musicians, artists - not just engineers. If you've used ChatGPT before, you can do this.

**For technical folks:** This guide includes explanations for beginners. Don't write it off - the workflow and agent patterns are useful regardless of your experience level. Skip the basics you already know.

---

## Quick Glossary (What These Words Mean)

Before we dive in, here's what some terms mean:

**Terminal** - A text-based way to talk to your computer. Instead of clicking icons, you type commands. It looks like a black or white window with text. Also called "command line" or "shell."
- **Mac:** Search for "Terminal" in Spotlight (Cmd + Space), or find it in Applications → Utilities → Terminal
- **Windows:** Search for "Command Prompt" or "PowerShell" in the Start menu. Or better: install [Windows Terminal](https://aka.ms/terminal) from the Microsoft Store

**GitHub** - A website where people store and share code. Think of it like Google Drive but for code projects. You don't need to know how to code to use it - we're just downloading files from it.

**Localhost** - Your own computer acting as a mini website server. When you see `localhost:3000` in your browser, that's a website running on YOUR machine, not the internet. Only you can see it.

**Comment** - In code examples below, you'll see lines starting with `#`. These are comments - notes for humans that the computer ignores. They explain what the next line does.

---

## What to Expect: Claude Will Ask Permission

One thing that surprises people: **Claude Code asks your permission before doing things** on your computer. This is a safety feature, not a bug!

You'll see prompts like:
```
Claude wants to run: npm install
Allow? (y/n)
```

**What to do:**
- Read what it's asking to do
- If you're unsure, just ask: "Explain what this command does before I approve it"
- Claude will break it down in plain English
- Then decide whether to approve

**Don't be scared by technical-looking commands.** You can always ask Claude to explain. That's literally what it's there for.

---

## Prerequisites (Do These Before the Workshop)

### 1. Laptop + charger + decent Wi-Fi

### 2. Claude Pro account ($20/mo)

Sign up at [claude.ai](https://claude.ai) and upgrade to Pro.

**Can't afford it?** Ask around - if you know someone with Claude Pro, they may be able to share a guest pass with you. Claude offers these to Pro subscribers to share with friends.

### 3. Open your Terminal

**On Mac:**
- Press `Cmd + Space` to open Spotlight
- Type "Terminal" and press Enter
- A window with a text prompt should appear

**On Windows:**
- Press the Windows key
- Type "Command Prompt" or "PowerShell"
- Click to open it
- (Or install [Windows Terminal](https://aka.ms/terminal) for a nicer experience)

You should see a blinking cursor waiting for you to type. That's it - you're in!

### 4. Install Claude Code

Follow the [official quickstart guide](https://docs.anthropic.com/en/docs/claude-code/quickstart).

After installing, test that it works:
```bash
# This command asks Claude Code to print its version number
# If it prints something like "1.0.0", you're good!
claude --version
```

### 5. Git installed (optional but helpful)

```bash
# This checks if Git is installed
# If it prints a version number, you have it
git --version
```

If you don't have Git, that's okay for this workshop. You can install it later if you want.

### 6. Come with 1-3 tiny project ideas

Or pick from our suggestions below. Something small you wish existed!

---

## For Facilitators: Running This Workshop

### Before People Arrive

- **Pick one AI tool for everyone** - This workshop uses Claude Code. Don't mix tools (Claude vs Gemini vs ChatGPT) or you'll spend the whole time debugging different interfaces.
- Clone/download this repo so you can share the prompts
- Test the full flow yourself at least once
- Have the [Claude Code usage page](https://console.anthropic.com/settings/usage) bookmarked to help people check their limits

### Opening the Workshop (15 min)

**Start with introductions.** Go around and have everyone share:
1. Their name
2. Their experience with AI tools:
   - "I use ChatGPT daily for work"
   - "I've tried the AI thing in Google search results"
   - "I built a whole app with Cursor last week"
   - "I have no idea what any of this is"
3. What idea they want to work on today (or "I don't know yet")

This does two things: helps you gauge the room, and gets people excited hearing each other's ideas.

### During the Workshop

- **Pair people up** - Put terminal newbies with someone more comfortable. Driver/navigator style works great.
- **Regroup every 10-15 min** - Quick "where is everyone?" check-ins prevent people from silently struggling
- **Celebrate loudly** - When someone gets their first "it's running in my browser!" moment, make noise about it
- **Walk through the prompts** - Don't just tell people to "use the planner agent." Open the prompt file, read through it together, explain what each section does. This demystifies what's happening.

### Closing the Workshop

- **Demo time is magic** - Have everyone share their screen for 1-2 min and show what they built. Even "it shows a button that doesn't work yet" is a win. The excitement is contagious.
- **Clear ending ritual** - Say explicitly: "That's the official end! If you want to hang and ask questions, I'll be here for another 15-20 min. But no pressure to stay."
- **Share next steps** - Point them to the "What's Next" section of this README

### What I Learned Running This

- Fewer agents = faster dopamine hit. Start with Planner → Builder only.
- TDD burns tokens fast - save for later sessions
- People need to SEE the prompts, not just use them abstractly
- The "it's running!" moment is everything. Optimize for getting there fast.
- End clearly so people don't feel awkward about leaving

---

## Workshop Flow (90-120 minutes)

### Step 1: Setup Check (10 min)

Open your terminal (see glossary above if you forgot how).

```bash
# Create a new folder for your project
# "mkdir" means "make directory" (directory = folder)
mkdir my-project

# Move into that folder
# "cd" means "change directory"
cd my-project

# Start Claude Code
claude
```

You should see Claude Code start up and greet you.

**Check your usage limits:** Open [console.anthropic.com/settings/usage](https://console.anthropic.com/settings/usage) in your browser. This shows how much you've used and what's left. Keep this tab open during the workshop.

### Step 2: Brain Dump Your Idea (5 min)

Just get your messy idea out. Don't worry about structure or being "correct."

> **Tip:** Consider using [Wispr](https://wispr.chat/) (free) or [Wispr Flow](https://wispr.chat/flow) (paid) for voice-to-text. Why? Because AI models handle messy human speech surprisingly well, and talking is 3-4x faster than typing. You can literally ramble your idea out loud and paste the transcript. But typing works fine too!

Example brain dumps:

> "I want an app where I can dump all my random ideas and it organizes them somehow, like clusters them by theme or something"

> "A practice log for music - track what I practiced, how long, my mood, and show me streaks"

> "Something to help me plan gifts for people with constraints like budget and what they already have"

### Step 3: Understand the Agents (10 min)

Before using the agents, let's look at what they actually are. Open the `/prompts` folder and skim through each one together:

**Planner Agent** (`prompts/planner.md`)
- Takes your messy idea and asks clarifying questions
- Proposes a tiny MVP (minimum viable product)
- Creates a `plan.md` file with scope, acceptance criteria, and tasks
- Key line: "The goal is to get something running fast, not to build something perfect"

**Builder Agent** (`prompts/builder.md`)
- Reads the plan and implements Phase 1 only
- Gets it running as a web app you can open in your browser
- Explains every command before asking permission
- Key line: "Ship it!"

**Verifier Agent** (`prompts/verifier.md`) - Optional
- Adds simple tests or a manual checklist
- Keeps it light - just enough confidence that it works

The whole point of looking at these prompts is to demystify what's happening. These aren't magic - they're just detailed instructions that shape how Claude approaches your project.

### Step 4: Create the Plan (15-20 min)

Copy the Planner prompt from `prompts/planner.md` and paste it into Claude Code, followed by your brain dump:

```
[paste the entire planner prompt here]

Now, turn this idea into a plan:

[paste your brain dump here]
```

The agent will:
- Ask 3-5 clarifying questions
- Propose a tiny MVP
- Create a `plan.md` with scope, acceptance criteria, and Phase 1 tasks

**Review the plan.** Give feedback. Ask it to revise until you're happy. This is a conversation!

### Step 5: Build It (30-45 min)

Copy the Builder prompt from `prompts/builder.md` and paste it:

```
[paste the entire builder prompt here]

Now implement Phase 1 from plan.md.
```

The agent will:
- Build the minimal version
- Run it locally as a web app
- Give you a URL like `http://localhost:3000` to open in your browser

**When Claude asks permission:** Remember, you can always say "Explain what this command does first." Don't just approve things you don't understand - use it as a learning moment.

### Step 6: Verify It Works (Optional, 10 min)

If you have time, use the Verifier agent for quick sanity checks:

```
[paste the verifier prompt]

Add some basic verification that this works.
```

### Step 7: Demo Time!

Share your screen and show what you built! Even "it loads and shows one thing" is a win. The group energy at this point is usually amazing.

---

## The Agents

### Core Agents (Start Here)

| Agent | What It Does | When to Use |
|-------|--------------|-------------|
| **Planner** | Turns messy ideas into clear plans | Always start here |
| **Builder** | Implements Phase 1 as a web app you can see in browser | After you have a plan |
| **Verifier** | Adds light tests or checklist | Optional, after building |

### Advanced Agents (Use Later)

| Agent | What It Does | When to Use |
|-------|--------------|-------------|
| **Business Analyst** | Prioritizes features, cuts scope | When idea is too big |
| **TDD Developer** | Test-driven implementation | When quality > speed |

Find all prompts in the `/prompts` folder.

---

## Setting Up the Agents

**For this workshop, copy and paste the prompts directly.** Here's why:

The whole point is learning how agents work. When you paste the prompt yourself, you see exactly what instructions Claude is following. It's not a black box - it's just text that shapes behavior.

```
[paste entire prompt from prompts/planner.md]

Now, turn this idea into a plan: [your idea]
```

> **Note:** Claude Code does have an `/agents` command for creating persistent agents. That's useful once you're comfortable, but for learning, pasting the prompts directly is more educational. You'll actually understand what's happening.

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

**Rule of thumb:** If it needs login/OAuth, payments, or deployment to the real internet - save it for later. Keep it local!

---

## Safety & Guardrails

This section is important. Read it before you start.

### Your Computer, Your Responsibility

Claude Code runs commands on YOUR computer. That's powerful, but it means:

- **Back up your laptop** before the workshop if you have important stuff on it
- **Ideally, use a secondary/old laptop** if you have one lying around
- If something goes wrong, it's on your machine

### Real Example: How I Bricked My Server

True story: I was running agents autonomously on my home server. They kept creating Docker images without cleaning up old ones. Eventually I ran out of disk space and the whole server locked up. I had to physically reset it.

**Lesson:** Agents are powerful but they don't think about resource limits. Keep an eye on things.

### The Permission System is Your Friend

When Claude asks to run a command:

1. **Read what it's asking** - Even if it looks technical
2. **Ask for explanation** - "What does this command do?" is always valid
3. **Then decide** - You're the human in the loop

Example interaction:
```
Claude: I'd like to run: rm -rf node_modules
You: What does that command do?
Claude: This deletes the node_modules folder, which contains
        installed dependencies. We're doing this to reinstall
        them fresh and fix the version conflict.
You: Ok, approved.
```

### Avoid "YOLO Mode"

Claude Code has a flag called `--dangerously-skip-permissions` (sometimes called "yolo mode"). This lets Claude run commands without asking you first.

**Don't use this** unless:
- You really understand what you're doing
- You're on an isolated machine you don't care about
- You've set up proper sandboxing

For this workshop, keep permissions ON. The asking is a feature, not a bug.

### What COULD Go Wrong (Honest List)

- Claude installs packages that conflict with stuff you already have
- Claude creates lots of files and clutters your project
- Claude runs a server that uses a port something else needs
- Claude doesn't clean up after itself (temp files, Docker images, etc.)
- Claude misunderstands and modifies the wrong file

None of these are catastrophic if you're paying attention and have backups. But they're real.

---

## Token-Saving Tips

Your Claude Pro subscription has limits. Here's how to not burn through them:

### Basic Tips

- **Keep scope tiny** - One feature, one screen, one file
- **Get the happy path working first** - Skip edge cases initially
- **Use Planner → Builder only** - The simpler flow uses fewer tokens

### Advanced Tips

- **`/clear`** - Clears your conversation and starts fresh. Use this between major tasks.
- **`/compact`** - Summarizes your conversation to reduce context size. Use when things feel slow.

### What Burns Tokens Fast

Having more specialized agents (like a Business Analyst doing detailed prioritization, or a TDD Developer writing dozens of tests) uses a LOT more tokens. That's great for production work, but for a first workshop, keep it simple. You can add sophistication later.

---

## What's Next (After the Workshop)

You built something! Here's where to go from here:

### Level Up Your Agents

- **Add more specialized agents** - Try the Business Analyst or TDD Developer in `/prompts/advanced`
- **Create your own agents** - Write custom prompts for your specific workflows
- **Use Claude to write agents** - Ask: "Help me write an agent prompt for [your use case]"

### Explore Advanced Patterns

- **Verification-Driven Development (VDD)** - A pattern where a "builder" AI and an "adversarial reviewer" AI iteratively improve code. [Learn more](https://gist.github.com/dollspace-gay/45c95ebfb5a3a3bae84d8bebd662cc25)
- **Agent chains** - String multiple agents together (Requirements → BA → PM → Dev → QA)
- **Autonomous loops** - Have agents work continuously until done (with appropriate guardrails!)

### Learn More About Claude Code

- [Official Claude Code Docs](https://docs.anthropic.com/en/docs/claude-code)
- [Creating custom agents](https://docs.anthropic.com/en/docs/claude-code/agents)
- [Slash commands reference](https://docs.anthropic.com/en/docs/claude-code/slash-commands)

### Keep Building!

The best way to learn is to keep making things. Try:
- Building something for a friend
- Recreating a simple tool you use daily
- Automating something tedious in your life

---

## Security & Ethics: The Bigger Picture

### On Using AI Responsibly

These tools are powerful. Some things to think about:

- **You're responsible for the output** - If Claude writes code with bugs or security issues, it's your code now
- **Review before deploying** - Never put AI-generated code in production without understanding it
- **Be honest about AI use** - If you're using AI to help with work, be transparent about it where appropriate

### On Data & Privacy

- Claude can see what you paste into it
- Don't paste sensitive data (passwords, API keys, private info) into prompts
- Your conversation may be used to improve the model (check Anthropic's data policy)

### Where This Is All Going

The field is moving fast. Some honest observations:

- These tools are getting better rapidly - what's hard today may be easy in 6 months
- The skills you're learning (prompting, breaking down problems, working with AI) will remain valuable
- "AI will take our jobs" vs "AI will augment us" is a false binary - the reality is more nuanced
- The people who learn to work WITH these tools effectively will have significant advantages

This isn't just for "SF techies." If you're reading this and you built something today, you're already ahead of most people. Keep going.

---

## Resources

- [Claude Code Quickstart](https://docs.anthropic.com/en/docs/claude-code/quickstart)
- [Claude Code Usage Dashboard](https://console.anthropic.com/settings/usage) - Check your limits here
- [Claude Prompting Best Practices](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
- [The Multiverse School](https://themultiverse.school/) - Great for learning AI fundamentals
- [Wispr](https://wispr.chat/) - Voice to text for faster brain dumps
- [VDD: Verification-Driven Development](https://gist.github.com/dollspace-gay/45c95ebfb5a3a3bae84d8bebd662cc25) - Advanced adversarial verification pattern

---

## Questions?

Open an issue or reach out!
