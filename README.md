# Source Code Management (SCM) / Version Control Systems (VCS)
Source Code Management (SCM) or Version Control Systems (VCS) are essential tools in modern software development, tracking code changes, facilitating collaboration, and providing rollback mechanisms. SCM is especially beneficial in a DevOps pipeline where multiple team members collaborate, test, and deploy code continuously.
- This repo is maintained by [Devops with Mike](https://www.youtube.com/@DevOpsWithMike0/videos/)
- For interview preparation, use this platform [Wandaprep](http://www.wandaprep.com/)
- Visit my website for more inquiries and support [DevOpswithMike](https://devopswithmike.tech/).


## Types of Version Control Systems
1. **Centralized Version Control Systems (CVCS)** - Example: Subversion (SVN), Perforce.
2. **Distributed Version Control Systems (DVCS)** - Example: Git, Mercurial.
3. **Cloud Version Control Systems** - These offer Git-compatible services hosted on major cloud platforms, which integrate with other DevOps services provided by the same cloud. Examples include:
    - **AWS CodeCommit**: A fully managed source control service that hosts secure Git repositories, part of AWS DevOps tools.
    - **Azure Repos**: Part of Azure DevOps, offering Git and TFVC (Team Foundation Version Control) services.
    - **Google Cloud Source Repositories**: Managed Git repositories on Google Cloud, integrated with GCP’s CI/CD and monitoring services.
Each of these cloud-hosted version control systems offers integration with their respective cloud services, including CI/CD, monitoring, and alerting tools, making them suitable for cloud-native development and deployment workflows.

## What is Git?
Git is a free, open-source, distributed version control system that allows teams to manage code versions, track changes, and collaborate on codebases. Git takes snapshots of the codebase at any given time, providing a history of changes that enables branching, merging, and collaboration without conflicts.

## Practical Use Case of Git
Git allows multiple developers to work on separate features without impacting the main codebase. For instance, a developer working on a new feature creates a branch, implements the feature, and then submits a pull request to merge the changes. This ensures feature isolation and allows for easy tracking of all contributions.

## Essential Git Commands
Essential Git Commands
Git commands are divided into **local commands** (interacting with the local repository) and **remote commands** (interacting with remote repositories).

### Local Git Commands
1. `git init`
- **Description**: Initializes a new Git repository in the current directory.
- **Use Case**: Used to start tracking files in a new project with version control.

```
$ git init
Initialized empty Git repository in /path/to/project/.git/
```

**Sample Folder Structure (after running git init)**:
```
my_project/
├── .git/                # Contains Git-related metadata (hidden folder)
├── src/
│   ├── main.py          # Example main application file
│   └── helper.py        # Helper script
├── README.md            # Project README file
└── requirements.txt     # Dependency file

```
2. `git config`
- **Description**: Configures user-specific settings like user name and email for commits.
- **Use Case**: Setting up Git credentials for identifying the author of each commit.

```
$ git config --global user.name "John Doe"
$ git config --global user.email "johndoe@example.com"

```
3. `git status`
- **Description**: Shows the status of changes in the working directory and staging area.
- **Use Case**: Checking for modified, new, or deleted files before committing.

```
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        src/helper.py
        README.md

nothing added to commit but untracked files present (use "git add" to track)

```
4. `git add`
- **Description**: Adds changes from the working directory to the staging area, preparing them for a commit.
- **Use Case**: Selecting specific files or all files to be staged before committing.

```
$ git add README.md    # Stages a specific file

$ git add .            # Stages all changes in the project

```
**Sample Folder Structure (after running git add on specific files):**

```
my_project/
├── .git/               # Contains Git metadata
├── src/
│   ├── main.py         # Staged for commit
│   └── helper.py       # Not staged
├── README.md           # Staged for commit
└── requirements.txt    # Not staged

```
5. `git log`
- **Description**: Displays the commit history for the project.
- **Use Case**: Reviewing past commits, authors, and commit messages.

```
$ git log --oneline
a1b2c3d Initial commit
d4e5f6a Add helper script

```
6. `git commit`
- **Description**: Commits staged changes to the local repository, recording a snapshot of the project.
- **Use Case**: Saving a stable version of code with a description.

```
$ git commit -m "Initial commit"
[main (root-commit) a1b2c3d] Initial commit
 2 files changed, 10 insertions(+)
 create mode 100644 README.md
 create mode 100644 src/main.py

```
### Remote Git Commands

1. `git clone`
Description: Copies a remote repository to a local directory.
Use Case: Starting work on an existing project.

```
$ git clone https://github.com/user/repo.git
Cloning into 'repo'...
remote: Enumerating objects: 42, done.
remote: Counting objects: 100% (42/42), done.
remote: Compressing objects: 100% (30/30), done.
remote: Total 42 (delta 5), reused 42 (delta 5), pack-reused 0
Unpacking objects: 100% (42/42), done.

```
2. `git remote add`
- Description: Links a local repository to a remote one.
- Use Case: Setting up a connection to a remote repository for pushing and pulling.

```
$ git remote add origin https://github.com/user/repo.git

```
3. `git pull origin`
Description: Retrieves and merges changes from a remote branch to the local branch.
Use Case: Updating the local branch with the latest remote changes.

```
$ git pull origin main
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 5 (delta 2), reused 5 (delta 2), pack-reused 0
Unpacking objects: 100% (5/5), done.
From https://github.com/user/repo
 * branch            main       -> FETCH_HEAD
Updating a1b2c3d..d4e5f6a
Fast-forward
 README.md | 2 ++
 1 file changed, 2 insertions(+)

```
4. `git push --set-upstream`
- **Description**: Pushes commits to a remote branch and sets it as the upstream tracking branch.
- **Use Case**: Publishing local changes to a new remote branch.

```
$ git push --set-upstream origin main
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (5/5), 432 bytes | 432.00 KiB/s, done.
Total 5 (delta 0), reused 0 (delta 0)
To https://github.com/user/repo.git
 * [new branch]      main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.

```

## Git Branching and Merging
### Branching
Branches allow isolated development on new features or bug fixes. The m**ain branch** typically contains production-ready code, while feature branches allow changes without affecting the main codebase.
- Creating a Branch: `git branch feature-branch`
- Switching Branches: `git checkout feature-branch`

**Example Folder Structure:**

```
my_project/
├── .git/
├── src/
│   ├── main.py             # Current work happens here
│   └── helper.py
├── README.md
└── requirements.txt

```
**Practical Example**

```
git checkout -b feature-auth  # Creates and switches to a branch named "feature-auth"

```
### Merging Branches
Merging incorporates changes from one branch into another, typically to bring a feature branch into the main branch after completing development.

**Example**:
```
git checkout main
git merge feature-auth

```

## Pull Requests (PRs)
In platforms like GitHub, Pull Requests (PRs) are requests to merge changes from a feature branch into the main branch. PRs allow code review, ensuring code quality and maintaining consistency in the main branch.

**Example Workflow**
1. **Create a branch**: `git checkout -b feature-update`.
2. **Commit changes**: `git add .`, then `git commit -m "Updated feature"`.
3. **Push branch**: `git push origin feature-update`.
4. **Open PR on GitHub**: Compare `feature-update` to `main` and create a PR.

## Git Workflow
**Common Git Workflow in a Team Environment**
1. **Initialize Repository**: `git init`.
2. **Create a Feature Branch**: `git checkout -b feature-branch`.
3. **Make Changes**: Modify files, stage (`git add`) and commit (`git commit`) changes.
4. **Push Branch**: `git push origin feature-branch`.
5. **Create Pull Request (PR)**: Submit PR for code review on GitHub.
6. **Merge PR**: Once approved, merge to the main branch.
7. **Pull Latest Changes**: Other team members run `git pull origin main` to sync with the main branch.

## Integrating Git and GitHub with Cloud Platforms in a DevOps Pipeline
Cloud-hosted Git services like **AWS CodeCommit**, **Azure Repos**, and **Google Cloud Source Repositories** provide Git repository hosting integrated with CI/CD pipelines, monitoring, and infrastructure-as-code tools available on each platform. This integration allows seamless code versioning, deployment automation, and production monitoring.

1. **Version Control and Collaboration**: Developers push code to cloud-hosted Git repositories, such as CodeCommit (AWS), Repos (Azure), or Source Repositories (GCP).

2. **Continuous Integration (CI)**:
- CI tools like AWS CodePipeline, Azure DevOps, or GCP Cloud Build trigger automated builds and tests.

3. **Continuous Deployment (CD)**:
- Once changes pass tests, pipelines automatically deploy code to environments (e.g., staging, production).

4. **Monitoring and Feedback**:
- Integration with monitoring tools (e.g., AWS CloudWatch, Azure Monitor, GCP Monitoring) provides real-time feedback and metrics.


By leveraging Git, GitHub, and cloud-native Git services, DevOps teams can automate, scale, and maintain version control, allowing faster and more
