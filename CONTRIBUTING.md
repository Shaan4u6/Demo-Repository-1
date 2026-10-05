# Contributing

Welcome. This repository exists so that people can make their first ever open
source contribution, so this guide assumes you have never done it before. If you
have, skip to [The workflow](#the-workflow).

---

## The one-paragraph version

Claim an issue by commenting `/claim`. It names one file in
`python-open-source-challenge/`. That file is a small Python program that is
broken on purpose. Fix it — minimally, following the `# TODO:` comments — until
running it prints `All checks passed!`. Open a pull request that says
`Closes #<number>`. Done.

---

## What you need

Three things, and you may already have all three.

| Thing | How to check |
|---|---|
| **A GitHub account** | Sign in at [github.com](https://github.com). [Sign up](https://github.com/signup) — free, two minutes. |
| **Git on your laptop** | Run `git --version`. If it prints a number, you have it. |
| **Python 3** | Run `python3 --version`. If it prints a number, you are ready. |

If `git --version` says "command not found", install it from
[git-scm.com/downloads](https://git-scm.com/downloads). On a Mac, running
`git --version` may offer to install it for you — say yes.

No `pip install`, no virtual environment, no editor requirements.

**First time using Git on this machine?** Run these two lines once, with your
own details:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Skip them and Git stops you at your first commit with `Please tell me who you are`.

---

## The whole thing, in eight steps

```
1. Pick an issue    ->  comment /claim
2. Fork             ->  your own copy on GitHub
3. Clone            ->  download it to your laptop
4. Branch           ->  git checkout -b fix/issue-42
5. Fix one file     ->  until it prints All checks passed!
6. Commit           ->  save the change with a message
7. Push             ->  send it back to GitHub
8. Pull request     ->  ask us to merge it
```

Everything below is those eight steps, slowly. Most people finish their first
one in under twenty minutes.

**You cannot break anything.** You work on your own copy, on a branch, and a
human reads your change before it goes anywhere near this repository.

---

## The workflow

### 1. Claim an issue

Browse the [open issues](../../issues) and comment **`/claim`** on one that looks
interesting. A bot assigns it to you within seconds and adds `status: claimed`.

**Only claim what you will actually work on.** You can hold two issues at a time.
If you go quiet for five days the bot releases your claim so somebody else can
take it — no hard feelings, just come back and claim another.

If an issue is already assigned, pick a different one. There are ninety.

### 2. Fork it

**Fork** means "make my own copy of this project". Click **Fork** at the top
right of this page, then **Create fork**.

You now have your own copy at `github.com/YOUR-USERNAME/Demo-Repository-1`. You
can do anything you like to it. **You cannot break the original.**

### 3. Clone your fork

**Clone** means "download my copy so I can open the files".

First check you are on **your fork** — the URL must show *your* username, not
`github-community-gitam`. Then click the green **`< > Code`** button, copy the
HTTPS link, and:

```bash
git clone https://github.com/YOUR-USERNAME/Demo-Repository-1.git
cd Demo-Repository-1

# point at the original, so you can pull in other people's merged work later
git remote add upstream https://github.com/github-community-gitam/Demo-Repository-1.git

# verify: origin must be YOUR username, upstream must be the org
git remote -v
```

> **The single most common mistake.** Cloning the original instead of your fork.
> Everything works until you push, which then fails with **permission denied**.
> `git remote -v` catches it in two seconds.

### 4. Make a branch

Never work on `main`. Name the branch after your issue:

```bash
git switch main
git pull upstream main          # start from the latest version
git checkout -b fix/issue-42
```

| Prefix | Use it for |
|---|---|
| `fix/` | Repairing one of the ninety programs — almost always this one |
| `docs/` | README, CONTRIBUTING, comments |
| `ci/` | Workflows |

### 5. Fix the file

Open the one file your issue names. Run it first, so you can see what failing
looks like:

```bash
python3 python-open-source-challenge/issue-42.py
```

You will get an `AssertionError`. Read it — it tells you the input that was
given, what the code returned, and what it should have returned.

Now work through the `# TODO:` comments. Each one sits next to something that is
wrong or missing. They are clues, not answers.

Three rules, and they matter:

- **Do not rewrite the program from scratch.** Reading somebody else's code and
  making a small careful change is the skill being taught here. Starting over
  skips the lesson.
- **Do not edit `check_solution()`.** That is the marking scheme. Changing the
  test so it agrees with your code is not a fix, and it will be spotted in review.
- **Do not delete the `# TODO:` comments** unless the thing they describe is
  genuinely done. If you fixed it, removing the comment is correct and welcome.

### 6. Check it

```bash
python3 python-open-source-challenge/issue-42.py
```

You are finished when it prints:

```
All checks passed!
```

Nothing else counts as done.

### 7. Commit

```bash
git add python-open-source-challenge/issue-42.py
git commit -m "fix: correct the department average calculation in issue 42"
```

Write commit messages as `<type>: <what changed>`. Use `fix`, `docs`, `test`,
`ci`, `refactor` or `chore`.

### 8. Push and open a pull request

```bash
git push -u origin fix/issue-42
```

GitHub then shows a yellow banner on your fork with a **Compare & pull request**
button. Click it, fill in the template, and click **Create pull request**.

Make sure the description contains:

```
Closes #42
```

That line is what links your work to the issue and closes it automatically when
you are merged. Without it a maintainer has to close the issue by hand, which is
how issues get forgotten.

> If `git push` fails with **permission denied** or **repository not found**, you
> cloned the original instead of your fork. Run `git remote -v` and check whose
> username is there.

### 9. Review

A maintainer will read it. They may ask for changes — that is normal and is not a
criticism. Push more commits to the same branch and the pull request updates
itself.

---

## What the automatic check does

When you open a pull request, a robot runs **only the file or files you changed**
and requires each to print `All checks passed!`.

It deliberately does not run the other eighty-nine. Those are still broken, by
design, and they are not your problem.

**A red X is not a rejection.** It is information. Click **Details** next to the
red check and read the log. To fix it: change the file, commit, and push to the
**same branch** — the pull request updates itself. You do not open a new one.

If the check goes red, open the log. It prints the same error you would see on
your own machine, and the failing `assert` names the exact input and expected
result. You can always reproduce it in one line:

```bash
python3 python-open-source-challenge/issue-42.py
```

---

## Using AI tools

You may use ChatGPT, GitHub Copilot, or anything else.

What you may not do is open a pull request you cannot explain. You are
responsible for understanding the change, running it yourself, and answering
questions about it in review. That is not a rule against AI — it is the whole
reason this repository exists.

---

## What gets rejected

So that nobody wastes an afternoon:

| Rejected | Why |
|---|---|
| The program rewritten from scratch | Skips the actual exercise |
| `check_solution()` edited so the test agrees with the code | Changing the marking scheme is not a fix |
| Whitespace-only or comment-only changes to game files | No substance |
| Several unrelated issues in one pull request | Unreviewable. One issue, one pull request |
| A pull request with no `Closes #<number>` | Cannot be traced to an issue |
| Work on an issue claimed by somebody else | Somebody else got there first |

If your pull request is closed for one of these, it is not personal. Claim
another issue and have another go.

---

## Getting unstuck

- **Read `check_solution()` first.** The `assert` lines describe the expected
  behaviour more precisely than the sentence at the top of the file.
- **Run the file constantly.** After every small change. It takes half a second.
- **Add `print()` statements.** Put one inside the loop to see what the code
  actually does versus what you assumed.
- **Still stuck?** Comment on your issue and say what you have tried. Asking is
  not failing — a good question is itself a contribution.
- **Come to a PR Debug Clinic** (Oct 12, Oct 21). Bring your laptop and your
  broken branch — that is the entire point of the session.

### When Git throws something at you

Nine times out of ten it is one of these:

| What you see | What it means |
|---|---|
| `permission denied` on push | You cloned the original, not your fork. Check `git remote -v` |
| `fatal: not a git repository` | You are in the wrong folder. `cd` into the project |
| `Please tell me who you are` | First time using Git. Run the two `git config` lines it prints |
| `Everything up-to-date` but nothing on GitHub | You never committed. Run `git status` |
| `error: failed to push some refs` | Someone changed `main`. `git pull upstream main`, then push again |
| Checks are red on your PR | Click **Details**. It names the file and the line |
| `merge conflict` | Two people edited the same lines. Ask — this one is worth a human |

### Command cheat sheet

```bash
# 1. clone YOUR fork
git clone https://github.com/YOUR-USERNAME/Demo-Repository-1.git
cd Demo-Repository-1

# 2. branch
git checkout -b fix/issue-12

# 3. ... make your change in an editor ...

# 4. see what you changed
git status
git diff

# 5. check it works
python3 python-open-source-challenge/issue-42.py

# 6. commit
git add .
git commit -m "fix: short description of what changed"

# 7. push
git push -u origin fix/issue-12

# then open the pull request, with "Closes #12" in the description
```

Useful when you need to undo something:

```bash
git log --oneline -5             # what did I commit?
git pull upstream main           # get the latest changes
git restore <file>               # throw away uncommitted changes to a file
git switch main                  # go back to the main branch
```

### Where to look things up

| I want to... | Go to |
|---|---|
| Understand a word like "upstream" | [Glossary](https://github-community-gitam.github.io/open-source-launchpad/glossary.html) |
| Check a question others have asked | [FAQ](https://github-community-gitam.github.io/open-source-launchpad/faq.html) |
| Walk through Git again, slowly | [Git basics](https://github-community-gitam.github.io/open-source-launchpad/git-basics.html) |
| Check my PR before I open it | [PR checklist](https://github-community-gitam.github.io/open-source-launchpad/pr-checklist.html) |

---

## Code of conduct

By taking part you agree to the [Code of Conduct](CODE_OF_CONDUCT.md). Be kind to
people who are learning. Everybody here is new at something.
