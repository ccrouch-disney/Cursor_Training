# GitHub Setup Guide for the BI Enablement Team

Everything for our team lives on **github.com** under the [dss-data-arch](https://github.com/dss-data-arch) organization (Disney Streaming Services Data Architecture). This includes the Looker repo, BI Enablement, and all our team projects.

This guide gets you set up step by step.

---

## Quick Start: Just Viewing the Training Repo

The [Cursor_Training repo](https://github.com/ccrouch-disney/Cursor_Training) is public. You can:

- **Browse** all files directly at https://github.com/ccrouch-disney/Cursor_Training
- **Download everything** as a ZIP: click the green **Code** button > **Download ZIP**

This is enough to follow along with the training course. But to work with the team's repos (Looker, BI Enablement, etc.), keep going.

---

## Step 1: Create a GitHub Account

1. Go to [github.com/signup](https://github.com/signup)
2. Use your **work email address**
3. Choose a username (something recognizable like `firstname-lastname-disney`)
4. Complete the email verification

If you already have a github.com account, skip to Step 2.

---

## Step 2: Get Added to the dss-data-arch Org

You need to be a member of the **dss-data-arch** organization to access the team's private repos. Ask your manager or an org admin to invite you.

Once invited, you'll get an email from GitHub. Click the link to accept the invitation.

**Our team's repos in dss-data-arch:**

| Repo | What It Is |
|------|------------|
| `dss-data-arch/bi_enablement` | BI Enablement Composable Workspace |
| `dss-data-arch/looker-test` | Looker development and testing |
| `dss-data-arch/bitools` | Shared BI tooling |
| `dss-data-arch/perf_intel_bi` | Performance intelligence BI |
| `dss-data-arch/launch_hq` | Launch HQ reporting |

---

## Step 3: Install the GitHub CLI

The GitHub CLI (`gh`) handles authentication so you don't have to manage tokens manually. In your terminal (or Cursor's built-in terminal):

```
brew install gh
```

Verify it installed:

```
gh --version
```

---

## Step 4: Authenticate

Run this command and follow the prompts:

```
gh auth login
```

When it asks:
- **Where do you use GitHub?** --> `GitHub.com`
- **Preferred protocol?** --> `HTTPS` (simpler to start with)
- **Authenticate with?** --> `Login with a web browser`

It will give you a one-time code, open your browser, and ask you to paste it. Once done, you're authenticated.

Verify with:

```
gh auth status
```

You should see something like:

```
github.com
  Logged in to github.com account your-username
  Active account: true
```

---

## Step 5: Authorize SSO for the dss-data-arch Org

**This is the #1 source of "I'm logged in but it says permission denied" errors.**

The dss-data-arch org uses SAML SSO. GitHub requires you to **explicitly authorize your credentials** for SSO-protected orgs -- it does not happen automatically.

**After running `gh auth login`, do this:**

1. Go to [github.com/settings/tokens](https://github.com/settings/tokens)
2. Click **Tokens (classic)** in the sidebar if you don't see your tokens
3. Find the token created by `gh auth login` (it will be the most recent one)
4. Look for **dss-data-arch** in the SSO section next to the token
5. Click **Authorize**
6. Complete the SSO sign-in flow (your corporate login)

If you're using SSH keys instead of HTTPS:
1. Go to [github.com/settings/keys](https://github.com/settings/keys)
2. Next to your SSH key, click **Configure SSO**
3. Authorize it for **dss-data-arch**

**You must do this step or you will not be able to clone, push, or pull from any dss-data-arch repo.**

---

## Step 6: Clone a Repo

Now you can clone any repo you have access to:

```
git clone https://github.com/dss-data-arch/bi_enablement.git
```

Or the training repo:

```
git clone https://github.com/ccrouch-disney/Cursor_Training.git
```

---

## Troubleshooting

### "Permission denied" or "403" when cloning or pushing

This almost always means your token isn't SSO-authorized for dss-data-arch. Go back to [Step 5](#step-5-authorize-sso-for-the-dss-data-arch-org) and authorize SSO.

### "Repository not found" when cloning a dss-data-arch repo

Two possible causes:
1. You haven't been added to the org yet -- ask an admin to invite you
2. Your token isn't SSO-authorized -- go back to [Step 5](#step-5-authorize-sso-for-the-dss-data-arch-org)

### "My token stopped working after a migration"

Org migrations can invalidate SSO authorizations. Re-authorize your token:
1. Go to [github.com/settings/tokens](https://github.com/settings/tokens)
2. Find your token
3. Click **Authorize** next to **dss-data-arch** again
4. Complete the SSO flow

### "Cursor can't push or pull"

Cursor uses whatever git credentials are configured in its built-in terminal. Fix this by running `gh auth login` **from inside Cursor's terminal** (Ctrl+`), not from a separate Terminal.app window. Then authorize SSO (Step 5) again if needed.

### "I also have access to github.twdcgrid.net -- what's that?"

That's a separate enterprise GitHub instance. Some teams use it, but our team's repos live on **github.com** under **dss-data-arch**. If you need access to twdcgrid for other work, you can authenticate the CLI for it separately:

```
gh auth login --hostname github.twdcgrid.net
```

This won't affect your github.com authentication -- they're independent.

### Quick diagnostic command

Run this anytime to see exactly what's configured:

```
gh auth status
```

This shows every GitHub account you're logged into, which tokens are active, and what permissions they have.
