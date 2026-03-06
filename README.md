# Cursor Enablement Course -- Getting Started with AI-Assisted Development

**Duration:** ~60 minutes (instructor-led, hands-on)
**Audience:** BI Enablement team (Mac users, new to terminal)
**Goal:** By the end, everyone has a working dev environment, understands Cursor's core features, and has built something with AI assistance.

---

## Pre-Work (Send to Team Before the Session)

Have everyone complete these steps before the session to save time. If they get stuck, we'll troubleshoot at the start.

1. **Download and install Cursor** from [cursor.com](https://www.cursor.com/). It installs like any Mac app -- drag to Applications.
2. **Open Terminal.app** once to make sure it launches. You can find it in Applications > Utilities > Terminal, or search for "Terminal" in Spotlight (Cmd+Space).
3. **Install Homebrew** by pasting this into Terminal and pressing Enter:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

It will ask for your Mac password (you won't see characters as you type -- that's normal). Follow any "Next steps" instructions it prints at the end.

4. **Install Python and Git** by pasting this into Terminal:

```
brew install python git
```

5. **Verify** by running these two commands (each should print a version number):

```
python3 --version
git --version
```

If any step fails, don't worry -- we'll fix it together at the start of the session.

---

## Course Outline

| Time | Module | What We Cover |
|------|--------|---------------|
| 0:00 | **Module 1** -- Environment Setup | Terminal basics, verify tools, install uv |
| 0:15 | **Module 2** -- How Cursor Works | Chat, Agent mode, inline edit, @-mentions |
| 0:25 | **Module 3** -- Project Setup for AI Success | Folder structure, README, .cursor/rules, git init |
| 0:45 | **Module 4** -- Hands-On Exercise | Build a Python data script with Cursor Agent |
| 0:55 | **Module 5** -- Power Features & Next Steps | Skills, MCPs, subagents, where to learn more |

---

## Module 1: Environment Setup (15 min)

**Materials:** [module-1-setup/README.md](module-1-setup/README.md)

### Instructor Notes

- Open Cursor on the projector and show that it has a built-in terminal (Ctrl+` or View > Terminal). This is where they'll run most commands.
- Walk through the module-1 guide step by step. If pre-work was done, this becomes a quick verification round.
- For anyone who didn't do the pre-work, pair them with someone who did while you keep moving.

### Key Points to Emphasize

- The terminal is just a way to type commands to your computer. Nothing scary.
- Homebrew is the Mac "app store" for developer tools.
- **uv** is a modern Python tool that makes managing packages fast and simple.
- They'll rarely need to use the terminal directly -- Cursor's agent can run commands for them.

---

## Module 2: How Cursor Works (10 min)

### Instructor Notes

This is a live demo, not a hands-on module. Screen-share Cursor and walk through each feature.

### Demo Script

1. **Open a file** in Cursor (use the course README itself).

2. **Chat (Cmd+L):** Select some text, press Cmd+L, and ask "What does this do?" Show how Claude explains the selected code/text. This is the "ask a question" mode.

3. **Agent Mode:** Open the chat panel. Show that "Agent" is the default mode at the top. Type a request like: *"Create a file called hello.py that prints 'Hello from BI Enablement'"*. Show how Claude:
   - Proposes the change
   - You can review the diff
   - Click "Accept" or "Reject"
   - It can also run the file for you

4. **Inline Edit (Cmd+K):** Open a file, select a line, press Cmd+K, and type an instruction like "make this uppercase". Show the inline diff.

5. **@-mentions:** In the chat, type `@` and show the autocomplete menu:
   - `@file` -- reference a specific file
   - `@folder` -- reference an entire folder
   - `@web` -- search the web for current information
   - `@docs` -- reference documentation

6. **Plan Mode:** In the chat panel dropdown, switch from "Agent" to "Ask". Explain: Ask mode is read-only -- Claude can research and plan but won't change files. Useful for thinking through a problem before acting.

### Key Points to Emphasize

- **Agent mode is the workhorse.** It can read files, write files, run terminal commands, and iterate.
- **@-mentions are how you give Claude context.** The more context, the better the result.
- **You're always in control.** Claude proposes changes, you approve them.

---

## Module 3: Setting Up a Project for AI Success (20 min)

**Materials:** [module-3-project/sample-rules/](module-3-project/sample-rules/)

### Instructor Notes

This is fully hands-on. Everyone follows along in Cursor.

### Walkthrough Script

**Step 1: Create a new project folder**

Have everyone create a folder on their Desktop (or wherever they prefer):

```
mkdir ~/Desktop/my-bi-project
```

Then open it in Cursor: File > Open Folder > select the folder.

**Step 2: Initialize git**

Open Cursor's terminal (Ctrl+`) and run:

```
git init
```

Explain: Git tracks every change you make. It's your safety net -- you can always undo. Claude also uses git to manage the changes it makes.

**Step 3: Create a README.md**

This is the most important file in any project. Claude reads it to understand what the project is about. Ask Claude in Agent mode:

> Create a README.md for a BI data analysis project. The project uses Python and connects to Snowflake. It's for the BI Enablement team.

Review what Claude generates. Point out how having a good README means Claude already knows your context in future conversations.

**Step 4: Create .cursor/rules/**

This is how you give Claude persistent instructions for your project. Rules are loaded automatically every time Claude works on your project.

Create the rules folder:

```
mkdir -p .cursor/rules
```

Copy the two sample rule files from the course materials into the new project. Walk through each one and explain what the rules do:

- **project-context.mdc** -- Tells Claude about the team, tech stack, and conventions
- **python-standards.mdc** -- Tells Claude how you want Python code written

Show the sample files at [module-3-project/sample-rules/](module-3-project/sample-rules/) and have everyone customize them for their work.

**Step 5: Let Agent mode set up the project**

Ask Claude in Agent mode:

> Set up this project with a requirements.txt that includes pandas and snowflake-connector-python. Also create a tasks/todo.md with a checklist for our first analysis.

Watch Claude create the files. Review and accept.

**Step 6: Make a first commit**

Ask Claude:

> Commit all these files as our initial project setup.

Show how Claude stages and commits everything.

### Key Teaching Point

**The better your project is organized and documented, the better Claude can help you.** A README gives Claude the "what." Rules give Claude the "how." Together, they make Claude feel like a team member who already knows your conventions.

---

## Module 4: Hands-On Exercise (10 min)

**Materials:** [module-4-exercise/](module-4-exercise/)

### Instructor Notes

Have everyone copy `sample_data.csv` from the course materials into their project folder, then follow the exercise instructions in [module-4-exercise/README.md](module-4-exercise/README.md).

Walk through it together, one prompt at a time. Pause after each step so everyone stays together.

### Exercise Summary

Participants use Cursor Agent to:
1. Read and explore the sample CSV
2. Write a Python script to filter and transform the data
3. Run the script and review the output
4. Iterate with a follow-up prompt to improve the script

This ties together everything from the previous modules: Agent mode, @-mentions, terminal, reviewing changes.

---

## Module 5: Power Features & Next Steps (5 min)

### Instructor Notes

This is a quick overview, not hands-on. The goal is awareness -- they'll explore these on their own.

### Topics to Cover

**Skills**
Skills are pre-built instruction sets that teach Claude specialized workflows. Some useful ones:
- **create-rule** -- Helps you create new .cursor/rules files
- **create-skill** -- Helps you build custom skills for your team
- **update-cursor-settings** -- Helps you configure Cursor preferences

You can use a skill by telling Claude: *"Use the create-rule skill to add a new rule for SQL formatting."*

**MCPs (Model Context Protocol)**
MCPs are external tool integrations that extend what Claude can do. For example:
- **Browser automation** -- Claude can open a browser, navigate to web apps, and interact with pages
- **Database connectors** -- Claude could query databases directly (future setup)

These are configured in Cursor Settings > MCP.

**Custom Subagents**
You can create specialized AI agents for specific tasks -- like a "SQL reviewer" that checks your queries, or a "data validator" that verifies data transformations.

**Git Integration**
Claude can help with all git operations:
- Creating commits with good messages
- Creating branches
- Making pull requests (with the GitHub CLI)
- Reviewing diffs

**Where to Get Help**
- Ask Claude itself -- *"How do I do X in Cursor?"*
- [Cursor documentation](https://docs.cursor.com)
- Team Slack channel
- This course folder -- it's a reference you can come back to

---

## Wrap-Up Checklist

By the end of the session, everyone should have:

- [ ] Homebrew, Python 3, Git, and uv installed
- [ ] Cursor installed and configured
- [ ] Created a project with README, .cursor/rules, and git initialized
- [ ] Used Agent mode to write and run a Python script
- [ ] Made at least one git commit through Cursor
