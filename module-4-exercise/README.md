# Module 4: Hands-On Exercise -- Build a Data Script with Cursor

**Time:** ~10 minutes
**Goal:** Use Cursor Agent mode to write, run, and iterate on a Python data script.

---

## Setup

Copy the sample data file into your project folder. The easiest way:

1. In Cursor, open your project folder (`~/Desktop/my-bi-project`)
2. Find `sample_data.csv` in the course materials (the `module-4-exercise` folder)
3. Drag and drop it into your project's file explorer in Cursor

Or use the terminal (adjust paths if your folders are in different locations):

```
cp ~/Desktop/cursor-course/module-4-exercise/sample_data.csv ~/Desktop/my-bi-project/
```

---

## Exercise: Subscriber Analysis

You have a CSV file with subscriber data. You'll ask Claude to build a Python script that analyzes it -- step by step.

### Step 1: Explore the Data

Open the chat panel (Cmd+L) and make sure you're in **Agent** mode. Type:

> Look at sample_data.csv and tell me what's in it. Summarize the columns and give me some quick stats.

Watch how Claude reads the file and describes its contents. This is a great way to get oriented with any dataset.

### Step 2: Write an Analysis Script

Now ask Claude to build something:

> Write a Python script called analyze_subscribers.py that:
> - Reads sample_data.csv
> - Filters to only active subscribers
> - Groups by plan_name and calculates total revenue and subscriber count per plan
> - Prints a summary table to the terminal
> - Saves the result to a file called active_subscriber_summary.csv

Claude will create the script. **Review the code before accepting** -- look at:
- Does it use pandas? (It should, per our python-standards rule)
- Does it have a `if __name__ == "__main__":` block?
- Does the logic make sense?

Click **Accept** when you're satisfied.

### Step 3: Run It

Claude may offer to run the script for you. If not, ask:

> Run analyze_subscribers.py

If it fails because pandas isn't installed, ask:

> Install pandas using uv and then run the script again

Watch Claude handle the error, install the dependency, and re-run. This is a common workflow -- **Claude can troubleshoot its own errors**.

### Step 4: Iterate

Now try a follow-up request to improve the script:

> Update the script to also show a breakdown by region, and add a column for average revenue per subscriber.

Watch how Claude modifies the existing script rather than starting over. Review the diff to see exactly what changed.

### Step 5: Commit Your Work

Ask Claude to save your progress:

> Commit everything with a message describing what we built.

---

## What You Just Learned

- **Agent mode** can read files, write code, install packages, and run scripts
- **Iterating** is natural -- just ask for changes in plain English
- **Error handling** works automatically -- Claude sees errors and fixes them
- **Git commits** can be done through conversation
- **@-mentions** let you point Claude at specific files for context

---

## Bonus (If Time Permits)

Try one of these on your own:

1. *"Add a bar chart using matplotlib that shows revenue by plan type. Save it as a PNG file."*
2. *"Rewrite the script to accept the input filename as a command-line argument instead of hardcoding it."*
3. *"Add error handling so the script prints a helpful message if the CSV file doesn't exist."*
