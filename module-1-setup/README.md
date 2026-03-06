# Module 1: Mac Environment Setup

**Time:** ~15 minutes
**Goal:** Everyone has Python, Git, and uv installed and working.

> If you completed the pre-work, skip to [Step 4: Verify Everything](#step-4-verify-everything) to confirm your setup is good.

---

## Step 1: Open Terminal

Terminal is a built-in Mac app that lets you type commands to your computer. There are two ways to open it:

- **Spotlight:** Press **Cmd+Space**, type **Terminal**, press **Enter**
- **Finder:** Go to Applications > Utilities > Terminal

You should see a window with a blinking cursor. This is where you'll type commands.

### Quick Orientation

Try these commands to get comfortable (type each one and press Enter):

**Print your current location:**

```
pwd
```

You should see something like `/Users/yourname`.

**List files in the current folder:**

```
ls
```

You'll see your files and folders listed.

**Move to your Desktop:**

```
cd ~/Desktop
```

**Go back to your home folder:**

```
cd ~
```

That's all the terminal you need to know for now. Cursor has a built-in terminal, so you'll mostly use that instead of this separate app.

---

## Step 2: Install Homebrew

Homebrew is a package manager for Mac -- think of it as an app store for developer tools. You install it once, then use it to install everything else.

**Paste this entire command into Terminal and press Enter:**

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

What to expect:
- It will ask for your **Mac password**. When you type it, you won't see any characters -- that's normal. Just type it and press Enter.
- It will show you what it's going to install and ask you to press Enter to continue.
- It takes 2-5 minutes to complete.

**Important -- follow the "Next steps" at the end!**

When Homebrew finishes, it may print "Next steps" instructions. These add Homebrew to your shell so you can use the `brew` command. The instructions look something like:

```
echo >> ~/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

Copy and paste those lines into Terminal. If you don't see "Next steps," you're fine -- it means Homebrew was already configured.

**Verify Homebrew is installed:**

```
brew --version
```

You should see something like `Homebrew 4.x.x`.

---

## Step 3: Install Python, Git, and uv

Now that Homebrew is ready, install the tools we need with a single command:

```
brew install python git
```

This takes 1-2 minutes. It installs:
- **Python 3** -- the programming language we use for data scripts
- **Git** -- version control (tracks changes to your files, like "undo history" for your whole project)

Next, install **uv** -- a modern, fast Python package manager:

```
brew install uv
```

uv makes it much easier (and faster) to install Python libraries like pandas, snowflake-connector-python, etc.

---

## Step 4: Verify Everything

Run each of these commands. Each one should print a version number:

```
python3 --version
```

Expected output: `Python 3.12.x` or `Python 3.13.x` (any 3.x version is fine)

```
git --version
```

Expected output: `git version 2.x.x`

```
uv --version
```

Expected output: `uv 0.x.x`

```
brew --version
```

Expected output: `Homebrew 4.x.x`

If any of these don't work, raise your hand and we'll troubleshoot.

---

## Step 5: Configure Git (One-Time Setup)

Git needs to know your name and email for tracking who made changes. Run these two commands, replacing the placeholders with your info:

```
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

For example:

```
git config --global user.name "Jane Smith"
git config --global user.email "jane.smith@disneystreaming.com"
```

---

## Step 6: Open Cursor and Find the Built-In Terminal

1. Open **Cursor** from your Applications folder (or Spotlight: Cmd+Space, type "Cursor")
2. Press **Ctrl+`** (that's the backtick key, top-left of your keyboard next to the 1 key)
3. A terminal panel opens at the bottom of Cursor

This built-in terminal works exactly like the Terminal app, but it's right inside Cursor. You'll use this for the rest of the course.

Try running `python3 --version` in Cursor's terminal to confirm it works there too.

---

## Troubleshooting

**"command not found: brew"**
The Homebrew "Next steps" weren't run. Close Terminal and reopen it, then try again. If it still doesn't work, re-run the Homebrew install command.

**"command not found: python3"**
Try closing and reopening Terminal. If that doesn't work: `brew install python`.

**"Permission denied" errors during Homebrew install**
This usually means you need admin rights on your Mac. Make sure you enter your Mac password when prompted during the Homebrew installation. If you get permission errors with `brew install`, try closing Terminal and reopening it, then retry.

**Cursor's terminal doesn't recognize brew/python3/git**
Close and reopen Cursor entirely. The terminal needs to pick up the new installations.

---

You're all set! Everything from here on out happens inside Cursor.
