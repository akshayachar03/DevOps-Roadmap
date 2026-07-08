# Git Collaboration Workflow & Essential Git Commands Interview Questions

## Most Frequently Asked Interview Questions

### Question 1

**Question**

What is the standard Git collaboration workflow followed in most organizations?

**Answer**

A typical enterprise Git workflow is:

1. Clone the repository.
2. Create a feature branch.
3. Make code changes.
4. Stage changes.
5. Commit changes.
6. Push the feature branch.
7. Create a Pull Request.
8. Review and resolve comments.
9. Merge into the main branch.
10. Synchronize the local repository.

**Explanation**

This workflow enables parallel development while protecting the production branch.

**Used in Production**

Followed by almost every software company using Git.

**Common Mistake**

Candidates often develop directly on the `main` branch instead of creating feature branches.

---

### Question 2

**Question**

How do you clone a Git repository?

**Answer**

Clone using:

```bash
git clone https://github.com/user/project.git
```

or

```bash
git clone git@github.com:user/project.git
```

**Explanation**

Cloning creates a complete local copy of the remote repository, including its history and branches.

**Used in Production**

The first step when joining a new project.

---

### Question 3

**Question**

Why should developers create a feature branch before making changes?

**Answer**

Feature branches isolate changes from the main branch, allowing independent development and safe code reviews.

Example:

```bash
git switch -c feature-login
```

**Explanation**

Branching prevents unstable code from affecting the production-ready branch.

**Used in Production**

Every new feature, bug fix, or enhancement is typically developed in its own branch.

---

### Question 4

**Question**

What is the purpose of `git status`?

**Answer**

`git status` displays:

- Current branch
- Modified files
- Staged files
- Untracked files
- Merge conflicts

Example:

```bash
git status
```

**Explanation**

It helps developers understand the current state of their working directory.

**Used in Production**

Frequently executed before staging or committing changes.

---

### Question 5

**Question**

What is the difference between `git add` and `git commit`?

**Answer**

| git add | git commit |
|----------|------------|
| Stages changes | Saves staged changes permanently |
| Prepares files | Creates a new commit |

Examples:

```bash
git add .
```

```bash
git commit -m "Add login feature"
```

**Explanation**

`git add` prepares changes, while `git commit` records them in the repository history.

**Common Mistake**

Candidates often think `git add` saves changes permanently.

---

### Question 6

**Question**

What is the difference between `git switch` and `git checkout`?

**Answer**

`git switch`

- Used primarily for switching branches.
- Easier and safer for branch operations.

Example:

```bash
git switch develop
```

`git checkout`

- Can switch branches.
- Can restore files.
- Performs multiple functions.

Example:

```bash
git checkout develop
```

**Explanation**

Modern Git recommends `git switch` for branch navigation because it is more intuitive.

---

### Question 7

**Question**

What is the difference between `git fetch`, `git pull`, and `git push`?

**Answer**

| Command | Purpose |
|----------|---------|
| `git fetch` | Downloads remote changes only |
| `git pull` | Downloads and merges remote changes |
| `git push` | Uploads local commits to the remote repository |

Examples:

```bash
git fetch
```

```bash
git pull
```

```bash
git push origin main
```

**Explanation**

Each command synchronizes repositories in a different direction.

---

### Question 8

**Question**

What are the purposes of `git log`, `git diff`, and `git show`?

**Answer**

`git log`

Shows commit history.

```bash
git log
```

`git diff`

Shows differences between file versions.

```bash
git diff
```

`git show`

Displays detailed information about a commit or tag.

```bash
git show HEAD
```

**Explanation**

These commands help developers inspect repository history and code changes.

---

### Question 9

**Question**

When should you use `git restore`, `git reset`, and `git revert`?

**Answer**

| Command | Purpose |
|----------|---------|
| `git restore` | Discard local file changes |
| `git reset` | Move HEAD or unstage changes |
| `git revert` | Safely undo committed changes by creating a new commit |

**Explanation**

Each command serves a different recovery scenario.

**Used in Production**

`git revert` is preferred for undoing changes on shared branches.

---

### Question 10

**Question**

Why is `git remote` important?

**Answer**

`git remote` manages remote repository connections.

View remotes:

```bash
git remote -v
```

Add remote:

```bash
git remote add origin https://github.com/user/project.git
```

**Explanation**

It defines where Git pushes and fetches code.

**Used in Production**

Every collaborative Git repository uses remotes.

---

### Question 11

**Question**

Which Git commands are used most frequently in day-to-day development?

**Answer**

Common daily commands include:

```bash
git status
git add
git commit
git pull
git push
git branch
git switch
git fetch
git log
git diff
```

Other commonly used commands:

```bash
git clone
git merge
git restore
git revert
git tag
```

**Explanation**

These commands form the core of the daily Git workflow for most developers and DevOps engineers.

**Common Mistake**

Candidates often memorize commands without understanding when each should be used.

---

## Scenario-Based Interview Questions

### Scenario 1

**Question**

You join a new development team and need to start working on an existing project. What steps would you follow?

**Answer**

1. Clone the repository.

```bash
git clone https://github.com/company/project.git
```

2. Switch to the appropriate branch.

```bash
git switch develop
```

3. Create a feature branch.

```bash
git switch -c feature-login
```

**Explanation**

This ensures development starts from the latest project state while keeping changes isolated.

---

### Scenario 2

**Question**

You complete a new feature. What is the typical workflow before the code reaches production?

**Answer**

1. Check repository status.

```bash
git status
```

2. Stage changes.

```bash
git add .
```

3. Commit changes.

```bash
git commit -m "Implement login feature"
```

4. Push the branch.

```bash
git push origin feature-login
```

5. Create a Pull Request.

6. Address review comments.

7. Merge after approval.

**Explanation**

This is the standard enterprise collaboration workflow.

---

### Scenario 3

**Question**

Before starting today's work, how do you synchronize your local repository with the latest remote changes?

**Answer**

Run:

```bash
git pull origin main
```

or

```bash
git fetch
```

followed by a merge if required.

**Explanation**

Keeping the local repository up to date minimizes merge conflicts.

---

### Scenario 4

**Question**

You accidentally staged several files that should not be included in the next commit. What command would you use?

**Answer**

```bash
git reset HEAD filename
```

**Explanation**

This removes the file from the staging area while preserving local modifications.

---

### Scenario 5

**Question**

You accidentally modified a file and want to discard the changes before committing. Which command should you use?

**Answer**

```bash
git restore filename
```

**Explanation**

`git restore` reverts the file to its last committed state.

---

### Scenario 6

**Question**

A teammate asks you to investigate changes introduced by a specific commit. Which command would you use?

**Answer**

```bash
git show <commit-id>
```

**Explanation**

`git show` displays detailed information about a commit, including metadata and code changes.

---

### Scenario 7

**Question**

Your local branch is behind the remote branch, but you want to review incoming changes before merging them. Which command should you use?

**Answer**

```bash
git fetch
```

**Explanation**

Fetching updates remote-tracking branches without modifying the working branch.

---

### Scenario 8

**Question**

A production issue is traced back to a recently merged commit. The commit has already been pushed to the shared repository. How would you safely undo it?

**Answer**

Use:

```bash
git revert <commit-id>
```

**Explanation**

`git revert` creates a new commit that reverses the earlier changes while preserving repository history.

---

### Scenario 9

**Question**

You need to identify what changed between two versions of a file before reviewing a Pull Request. Which Git command should you use?

**Answer**

```bash
git diff
```

**Explanation**

`git diff` highlights differences between file versions or commits, making it ideal for code reviews.

---

### Scenario 10

**Question**

Your team is preparing a production release and wants to permanently identify the release version. What should you do?

**Answer**

Create an annotated tag:

```bash
git tag -a v2.0.0 -m "Production Release"
```

Push the tag:

```bash
git push origin v2.0.0
```

**Explanation**

Tags provide immutable references to release versions, simplifying deployments and rollbacks.

---

### Scenario 11

**Question**

You are assigned a new feature in an enterprise DevOps project. Describe the complete Git collaboration workflow from receiving the task until the code is merged into the main branch and your local repository is synchronized.

**Answer**

A typical workflow is:

1. Clone the repository:

```bash
git clone https://github.com/company/project.git
```

2. Switch to the latest development branch:

```bash
git switch develop
```

3. Update your local repository:

```bash
git pull origin develop
```

4. Create a feature branch:

```bash
git switch -c feature-payment
```

5. Implement the feature.

6. Verify changes:

```bash
git status
git diff
```

7. Stage and commit:

```bash
git add .
git commit -m "Implement payment feature"
```

8. Push the feature branch:

```bash
git push -u origin feature-payment
```

9. Create a Pull Request.

10. Address review comments by committing and pushing additional changes to the same branch.

11. After approvals and successful CI/CD validation, merge the Pull Request.

12. Synchronize your local repository:

```bash
git switch develop
git pull origin develop
```

13. Delete the merged feature branch if it is no longer needed.

**Explanation**

This end-to-end workflow reflects how Git is used in modern DevOps environments. It demonstrates repository synchronization, feature branching, staging, committing, reviewing, merging, and post-merge synchronization—skills that are routinely evaluated in DevOps, Cloud Engineer, Platform Engineer, and SRE interviews.
