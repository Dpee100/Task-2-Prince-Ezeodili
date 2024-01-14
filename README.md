# Basic Version Control

## Version Control

Version control is a system that records changes to a file or set of files over time, allowing you to track and manage different versions of your project. It is a crucial tool in software development, but it can also be used for various other types of projects where tracking changes is important. The primary goals of version control are to:

1. **Track Changes:** Version control systems (VCS) keep a historical record of changes made to files. This includes details such as who made the change, when it was made, and what specific changes were implemented.

2. **Collaboration:** Version control facilitates collaboration among multiple contributors. Multiple people can work on the same project simultaneously without interfering with each other's work. The VCS helps in merging changes made by different team members.

3. **Rollback and Recovery:** If mistakes are made or if there's a need to revert to a previous state, version control allows you to roll back to a specific version of your project. This helps in recovering from errors or unwanted changes.

4. **Branching and Merging:** Version control systems support branching, where you can create separate lines of development. This is useful for working on new features or bug fixes without affecting the main project. Later, these branches can be merged back into the main line.

5. **Documentation:** Version control provides a log of changes, essentially serving as a form of documentation. This helps in understanding the evolution of the project, who made specific changes, and why those changes were made.

### There are two main types of version control systems

1. **Centralized Version Control Systems (CVCS):** These have a single, central repository that stores the complete history of the project. Examples include CVS (Concurrent Versions System) and Subversion.

2. **Distributed Version Control Systems (DVCS):** These systems create multiple, independent repositories, each with its complete history. Examples include Git, Mercurial, and Bazaar. Git, in particular, has become one of the most widely used version control systems.

Git is often favored due to its speed, flexibility, and the ability to work offline. It is extensively used in open-source and commercial projects, supporting collaboration and enabling efficient management of project versions.

## Differences between git and github

1. **Definition:** Git is a distributed version control system (DVCS) that allows developers to track changes in their source code during software development.
While, GitHub is a web-based platform that provides hosting for Git repositories and adds a web-based interface for various Git functionalities.

2. **Functionality:** Git provides the core version control functionalities, such as tracking changes, creating branches, mergiGit and GitHub are related but serve different purposes in the context of version control and collaborative software development.
2.ng branches, and facilitating collaboration among developers.
While, GitHub extends the capabilities of Git by providing a centralized platform for collaboration. GitHub offers features like issue tracking, pull requests, code review tools, and a web-based repository browser.

3. **Usage:** Git is typically used locally on a developer's machine. Developers can commit changes to their local repository, create branches, and perform various version control tasks without needing to connect to a network.
While, GitHub serves as a hosting service for Git repositories. Developers can push their local Git repositories to GitHub, making it easier to share code with others and collaborate on projects.

4. **Standalone & Collaboration:** Git is standalone and can be used independently of any online platform. Developers can use Git without connecting to a centralized server or repository.
While, GitHub facilitates collaboration among developers by providing tools for code review, managing issues, and discussing changes. It is widely used for open-source projects, team-based development, and collaborative work.

In summary, Git is the version control system itself, providing the fundamental functionalities for tracking changes and managing source code. GitHub, on the other hand, is a web-based platform built around Git, offering additional tools and features to enhance collaboration, code sharing, and project management. While Git can be used independently, GitHub is a hosting service that leverages Git to provide a collaborative and web-based environment for developers. Other similar services include GitLab and Bitbucket, which also offer Git repository hosting and collaboration features.

## Differences between git fetch and git pull

git fetch and git pull are both Git commands used to update a local repository with changes from a remote repository. However, they differ in their approach and the actions they perform.

**git fetch:**

1. **Purpose:** The primary purpose of git fetch is to retrieve changes from a remote repository without automatically merging them into the current branch.

2. **Operation:** When you run git fetch, Git contacts the remote repository, fetches any new changes, and updates the remote tracking branches in your local repository. However, it does not modify your working directory or merge the changes into your current branch.

3. **Advantages:** Fetching allows you to see what changes exist in the remote repository before deciding to integrate them into your local work.

```markdown
git fetch origin
```

**git pull:**

1. **Purpose:** The main purpose of git pull is to fetch changes from a remote repository and automatically merge them into the current branch.

2. **Operation:** When you run git pull, Git performs a git fetch to get the changes from the remote repository and then automatically merges them into your current branch. It's essentially a combination of git fetch and git merge.

3. **Advantages:** git pull is a convenient way to quickly update your local working directory with the latest changes from the remote repository and incorporate them into your current branch.

```markdown
git pull origin master
```

Choosing Between git fetch and git pull:

- Use git fetch when you want to see what changes are in the remote repository but don't want to automatically merge them into your current branch.
  
- Use git pull when you want to fetch changes from the remote repository and automatically merge them into your current branch.

In summary, git fetch is more cautious and gives you control over when and how you integrate remote changes, while git pull is a more automatic way to update your local repository and working directory with the latest changes from the remote repository.

## git rebase and the command for it

In simple terms, git rebase is a Git command used to change the base of your current branch. It allows you to move or combine a sequence of commits to a different starting point, typically a more recent commit or branch. This can result in a cleaner and more linear project history.

Imagine you started working on a feature branch, and in the meantime, changes were made in the main branch. Instead of merging those changes with a regular merge commit, git rebase lets you integrate the changes more fluidly by placing your changes on top of the latest main branch commit.

Here's a basic example:

1. Before Rebase:

```css
   
   A---B---C (main)
        \
         D---E---F (feature)
```

1. After Rebase:

```css

   A---B---C (main)
               \
                D'---E'---F' (feature)

```

In the example, commits D, E, and F from the feature branch are reapplied on top of the latest commit in the main branch, resulting in a linear history.

Now, the command for `git rebase`:

```bash
git rebase <base-branch>
```

- `<base-branch>` is the branch you want to set as the new base for your current branch.

Here's an example using actual branch names:

```bash
# Assuming you are on the feature branch
git checkout feature

# Fetch the latest changes from the main branch
git fetch origin main

# Rebase your feature branch on top of the latest main branch commit
git rebase origin/main
```

Remember, use `git rebase` when you want a cleaner and more linear history, but be cautious when rebasing commits that have been pushed to a shared repository, as it can rewrite commit history. It's generally considered safe to rebase local, unshared branches.

## git cherry-pick and the command for it

In simple terms, `git cherry-pick` is a Git command that allows you to pick and apply specific commits from one branch and apply them onto another branch. It's like taking selected changes from one branch and copying them onto another branch.

Here's a basic example:

1. Before Cherry-Pick:

```css
   
   A---B---C (main)
        \
         D---E---F (feature)
```

1. After Cherry-Pick:

```css
   
   A---B---C---F' (main)
        \
         D---E---F (feature)
```

In this example, the commit "F" from the feature branch is cherry-picked and applied onto the main branch, creating a new commit "F'" in the process.

Now, the command for `git cherry-pick`:

```bash
git cherry-pick <commit-hash>
```

- `<commit-hash>` is the hash of the commit you want to cherry-pick.

Here's an example using actual commit hashes:

```bash
# Assuming you are on the main branch
git checkout main

# Cherry-pick the commit from the feature branch
git cherry-pick <commit-hash-of-F>
```

After running this command, Git will apply the changes from the specified commit onto your current branch.

Keep in mind that while `git cherry-pick` is useful, it's important to be cautious when cherry-picking commits that have already been shared or pushed to a remote repository, as it can create duplicate or conflicting commits. It's generally considered safe for local branches or when collaborating with others who are aware of the cherry-picked changes.
