# GitHub Setup Guide for the BI Enablement Team

This guide walks you through getting set up on GitHub -- both the public github.com (where the Cursor Training repo lives) and the enterprise GitHub at github.twdcgrid.net.

Pick the tier that matches what you need right now. You can always come back and do the next tier later.

---

## Tier 1: View Only (No Account Needed)

The [Cursor_Training repo](https://github.com/ccrouch-disney/Cursor_Training) is public. You can:

- **Browse** all files directly at https://github.com/ccrouch-disney/Cursor_Training
- **Download everything** as a ZIP: click the green **Code** button > **Download ZIP**

This is enough to follow along with the training course. If that's all you need right now, you're done.

---

## Tier 2: github.com Account (For Cloning Repos and Using Git)

If you want to clone repos, push code, or access private repositories on github.com, you need a free account.

### Step 1: Create a GitHub Account

1. Go to [github.com/signup](https://github.com/signup)
2. Use your **work email address**
3. Choose a username (something recognizable like `firstname-lastname-disney`)
4. Complete the email verification

### Step 2: Install the GitHub CLI

The GitHub CLI (`gh`) handles authentication so you don't have to manage tokens manually. In your terminal (or Cursor's built-in terminal):

```
brew install gh
```

Verify it installed:

```
gh --version
```

### Step 3: Authenticate

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

### Step 4: Clone the Training Repo

```
git clone https://github.com/ccrouch-disney/Cursor_Training.git
```

This creates a `Cursor_Training` folder with all the course materials.

### Step 5: Authorize SSO (If You Join a Disney Org on github.com)

This is the most common source of "I'm logged in but it says permission denied" errors.

When an organization uses SAML SSO on github.com, you have to **explicitly authorize your credentials** for that org. GitHub doesn't do this automatically.

**If you get a permission error accessing an org's private repos:**

1. Go to [github.com/settings/tokens](https://github.com/settings/tokens)
2. Find your active token (the one created by `gh auth login`)
3. Next to the org name, click **Authorize** (or **Enable SSO**)
4. Complete the SSO sign-in flow

If you're using SSH keys instead of HTTPS:
1. Go to [github.com/settings/keys](https://github.com/settings/keys)
2. Next to your SSH key, click **Configure SSO**
3. Authorize it for the org

After authorizing, retry the `git clone` or `git push` that failed.

---

## Tier 3: Enterprise GitHub (github.twdcgrid.net)

The enterprise GitHub is a completely separate system from github.com. Different accounts, different logins, different repos. Think of them as two unrelated websites that happen to look the same.

### Step 1: Log In to Enterprise GitHub

1. Go to [github.twdcgrid.net](https://github.twdcgrid.net)
2. Sign in with your **corporate SSO credentials** (the same login you use for other internal tools)

If login fails:
- Try an **incognito/private browser window** (clears stale cookies)
- Make sure you're on the corporate network or VPN
- Clear your browser cookies for `github.twdcgrid.net` and try again
- If it still fails, contact IT -- your account may need to be provisioned or migrated

### Step 2: Authenticate the GitHub CLI for Enterprise

The `gh` CLI supports multiple GitHub instances. To add the enterprise one:

```
gh auth login --hostname github.twdcgrid.net
```

When it asks:
- **Preferred protocol?** --> `HTTPS`
- **Authenticate with?** --> `Login with a web browser`

Follow the browser flow just like you did for github.com.

### Step 3: Verify Both Accounts

Run this to see all your authenticated GitHub accounts:

```
gh auth status
```

You should see two entries:

```
github.com
  Logged in to github.com account your-username
  Active account: true

github.twdcgrid.net
  Logged in to github.twdcgrid.net account your-corp-username
  Active account: true
```

### Step 4: Cloning Enterprise Repos

When cloning from the enterprise GitHub, the URL uses `github.twdcgrid.net` instead of `github.com`:

```
git clone https://github.twdcgrid.net/your-org/your-repo.git
```

Git and `gh` will automatically use the correct credentials based on the hostname.

---

## Troubleshooting

### "Permission denied" when cloning or pushing

**On github.com:** Your token likely isn't SSO-authorized. Follow [Step 5 in Tier 2](#step-5-authorize-sso-if-you-join-a-disney-org-on-githubcom).

**On github.twdcgrid.net:** Run `gh auth login --hostname github.twdcgrid.net` to re-authenticate.

### "I can log into github.com but not github.twdcgrid.net" (or vice versa)

These are completely separate systems. Having an account on one does not give you access to the other. You need separate logins for each.

### "My token stopped working after a migration"

Org migrations can invalidate SSO authorizations. Re-authorize your token:
1. Go to [github.com/settings/tokens](https://github.com/settings/tokens)
2. Find your token
3. Re-authorize it for the new/migrated org

### "Cursor can't push or pull"

Cursor uses whatever git credentials are configured in its built-in terminal. Fix this by running `gh auth login` **from inside Cursor's terminal** (Ctrl+`), not from a separate Terminal.app window. This ensures the credential helper is set up for Cursor's environment.

### "I'm not sure which GitHub I should be using"

- **github.com** -- Public repos, open source, personal projects, and the Cursor Training repo
- **github.twdcgrid.net** -- Internal/enterprise repos, production code, anything that's company-private

When in doubt, ask the team.

### Quick diagnostic command

Run this anytime to see exactly what's configured:

```
gh auth status
```

This shows every GitHub account you're logged into, which tokens are active, and what permissions they have.
