## What is Source Code Management?

Source Code Management (SCM) is the systematic process of tracking, controlling, and managing changes to software code. It not only enables teams to collaborate seamlessly but also preserves the entire history of a project's evolution. SCM is fundamental for modern software development, ensuring that codebases remain stable, traceable, and adaptable over time.

SCM involves a series of best practices and tools that allow developers to:
- **Track Changes:** Every alteration to the code, along with the author and an accompanying explanation, is recorded. This detailed tracking simplifies debugging and empowers teams to revert to previous stable versions when necessary.
- **Enhance Collaboration:** Multiple developers can work on different parts of the code simultaneously without interfering with each other’s progress. Merging changes and resolving conflicts become efficient and streamlined.
- **Maintain History:** A comprehensive history of changes provides invaluable insights into the project's development, serving as both a record for troubleshooting and a learning resource.
- **Support Rollbacks:** If a newly introduced change causes issues, SCM makes it possible to quickly revert to a previous, working version without dramatic setbacks.


## How Was Source Code Managed Before Modern Version Control Systems

Before dedicated version control systems became the industry standard, managing source code was largely a manual process. Here are the key practices that shaped early SCM approaches:

### Manual File Duplication & Naming Conventions
- **Method:** Developers often saved each iteration of a file as a distinct copy with names like `project_v1`, `project_v2`, etc.
- **Challenge:** While this method captured changes, it became cumbersome and increased the chance for human error. Tracking the evolution of files and identifying which version contained specific modifications was a significant challenge.

### Manual Change Logs
- **Method:** Changes were documented manually in separate text files or logs. This log recorded what had been updated, why the change was made, and who introduced it.
- **Challenge:** Maintaining these logs required extra effort, and discrepancies between the log and actual file changes were common, reducing the reliability of the change history.

### Offline Archives and Physical Printouts
- **Method:** Some developers printed out code or stored codebases on external media for backup purposes.
- **Challenge:** This approach was not only inefficient but also made it difficult to synchronize changes, collaborate with others, or quickly revert to previous versions.

### Early Scripting and Utility Tools
- **Method:** Tools like `diff` and `patch` were used to compare file versions manually and attempt automated merging.
- **Challenge:** Although innovative for their time, these solutions required a deep technical understanding and still left much to be desired when dealing with complex, concurrent changes.

These early practices highlighted the limitations in scalability and reliability, eventually paving the way for the emergence of automated version control systems.



## What is a Version Control System?

A **Version Control System (VCS)** is software designed to help developers manage changes to source code over time. Its key functionalities include:

- **Change Tracking:** Every modification is logged with metadata detailing who made the change, when it was made, and why. This detailed history is essential for debugging and accountability.
  
- **Branching and Merging:** Developers can experiment with new features in isolated branches. When the work is complete, these changes are merged back into the main codebase, ensuring a smooth integration process.
  
- **Collaboration:** Multiple contributors can work on a single project concurrently. VCS handles complex scenarios like merging simultaneous changes, greatly reducing the risk of conflicts.
  
- **Version History:** A complete historical record allows for rollbacks to previous states, provides context for changes, and facilitates auditing.

By encapsulating these capabilities, VCS not only safeguards the integrity of the project but also empowers developers to innovate rapidly while minimizing risk.


##  History of Version Control Systems

The evolution of version control mirrors the growing complexity of software development. Here’s how we arrived at the systems we rely on today.

### Pre-VCS Era: Manual Versioning

Before dedicated version control systems emerged:
  
- **File Duplication:** Developers managed changes by saving multiple copies of files (e.g., `file_v1.txt`, `file_v2.txt`). This was prone to human error, confusion, and lost changes.
- **Manual Logs:** Change records were maintained in separate documents, making it hard to ensure consistency or retrieve precise historical data.

These methods were inefficient and error-prone, highlighting the need for a more systematic approach to managing code changes.

### Early VCS: SCCS and RCS

The first generation of VCS solutions provided automated ways to track changes:
  
- **Source Code Control System (SCCS):** Introduced in the 1970s, SCCS offered the first systematic method for tracking modifications, although it was limited in its ability to manage multiple files in a project.
- **Revision Control System (RCS):** Building on SCCS, RCS provided the "check-out" and "check-in" workflow, allowing for more efficient management of individual file revisions in Unix environments.

These systems laid the groundwork for automated version tracking, although they focused mostly on single-file versioning.

### Centralized Version Control Systems

As projects grew, so did the need for more robust solutions:
  
- **Concurrent Versions System (CVS):** Developed in the 1990s, CVS introduced a centralized repository concept. It permitted multiple developers to work simultaneously on a single codebase but had limitations with branching and non-linear development.
- **Subversion (SVN):** Emerging in the early 2000s, SVN improved upon CVS by offering better support for branching, merging, and managing binary files, addressing some of the shortcomings of its predecessor.

These centralized systems provided a more structured approach but were still inherently limited by their reliance on a single central repository.

### Distributed Version Control Systems (DVCS)

The next major evolution came with distributed systems, which fundamentally restructured how developers work:
  
- **Git:** Launched in 2005 by Linus Torvalds for Linux kernel development, Git revolutionized version control by allowing each developer to maintain a complete copy of the repository locally. This decentralized model supports robust branching and merging, enabling high-performance workflows.
- **Mercurial and Bazaar:** Other DVCS tools emerged to offer alternative workflows and user experiences, but Git quickly established itself as the industry standard.

DVCS has empowered developers with offline capabilities, faster operations, and flexible collaboration strategies, driving modern development practices globally.



Here’s a detailed explanation of **Git** and the different types of **Git platforms**, along with examples you can use for a **GitHub Page** or documentation:

---

## 🧠 What is Git?

**Git** is a **distributed version control system** used to track changes in source code during software development.

### 🔹 Key Features:
- Tracks changes to files over time.
- Allows multiple developers to collaborate.
- Supports branching and merging.
- Works offline (local repository).
- Maintains a full history of changes.

### 🔹 Why Use Git?
- Helps manage code versions.
- Enables collaboration without overwriting each other's work.
- Makes it easy to roll back to previous versions.

---

## 🌐 Popular Git Platforms

These platforms host Git repositories and provide collaboration tools like issue tracking, pull requests, CI/CD, and more.

### 1. **GitHub**
- **URL**: https://github.com
- **Owned by**: Microsoft
- **Best for**: Open-source projects, collaboration, GitHub Pages (static websites)
- **Features**:
  - Pull requests, issues, actions (CI/CD)
  - GitHub Pages for hosting websites
  - Marketplace for integrations

### 2. **GitLab**
- **URL**: https://gitlab.com
- **Owned by**: GitLab Inc.
- **Best for**: DevOps lifecycle, private repositories
- **Features**:
  - Built-in CI/CD
  - Issue tracking and project management
  - Self-hosted or cloud-hosted options

### 3. **Bitbucket**
- **URL**: https://bitbucket.org
- **Owned by**: Atlassian
- **Best for**: Integration with Jira, private teams
- **Features**:
  - Free private repos
  - Pipelines for CI/CD
  - Tight integration with Jira and Trello

### 4. **SourceForge**
- **URL**: https://sourceforge.net
- **Best for**: Hosting legacy open-source projects
- **Features**:
  - Project hosting
  - Download mirrors
  - Basic Git support

### 5. **Azure Repos**
- **URL**: Part of Azure DevOps
- **Owned by**: Microsoft
- **Best for**: Enterprise DevOps pipelines
- **Features**:
  - Git and TFVC support
  - Integrated with Azure Pipelines
  - Permissions and policies for enterprises
---

## 📁 What is a Repository?

A **repository (repo)** is like a **project folder** that stores all your code, files, and the entire history of changes.

### 🔹 Key Features:
- Contains source code, documentation, and configuration files.
- Tracks every change made to the project.
- Can be **local** (on your computer) or **remote** (on GitHub, GitLab, etc.).

---

## 🏠 Local Repository

A **local repository** is the Git repository stored on your **own computer**. You can commit, branch, and manage history locally.


### 🔹 What it includes:
- Your working directory (the actual files).
- A `.git` folder that stores the full history of commits, branches, and tags.
- Staging area (index) for preparing commits.

### 🔹 What you can do locally:
- Create branches
- Make commits
- View history
- Merge changes
- Revert to previous versions

### 🧠 Example:
```bash
git init
```
Creates a new local Git repository.

---

## 🌐 Remote Repository

A **remote repository** is a Git repository hosted on a **server or platform** like GitHub, GitLab, or Bitbucket. Remote repository is hosted on a server (like GitHub). Used for sharing and collaborating with others.


### 🔹 Purpose:
- Enables **collaboration** with others.
- Acts as a **central source of truth** for the project.
- Used to **push** and **pull** changes between developers.

### 🔹 Common Commands:
```bash
git remote add origin https://github.com/user/repo.git
git push origin main
git pull origin main
```

---

## 🔄 How They Work Together

1. You **clone** a remote repo → creates a local copy.
2. You make changes and **commit** locally.
3. You **push** changes to the remote repo.
4. Others **pull** your changes to their local repos.

---

## 🌿 What is a Branch?

A **branch** is a **separate line of development** in your repository.

### 🔹 Why Use Branches?
- To work on new features or bug fixes without affecting the main code.
- Allows multiple developers to work in parallel.

### 🔹 Common Branches:
- `main` or `master`: The main production-ready code.
- `dev`: Development branch.
- `feature/login`: A feature-specific branch.

### 🧠 Example:
```bash
git checkout -b feature/login
```
Creates and switches to a new branch called `feature/login`.

---

## 🏷️ What is a Tag?

A **tag** is a **snapshot** of your repository at a specific point in time, usually used to mark **releases**.

### 🔹 Why Use Tags?
- To label versions like `v1.0`, `v2.1.3`, etc.
- Useful for deployments and rollbacks.

### 🧠 Example:
```bash
git tag v1.0
```
Creates a tag named `v1.0`.

---

## 📝 What is a Commit?

A **commit** is a **record of changes** made to the codebase.

### 🔹 What It Includes:
- A unique ID (SHA hash)
- Author and timestamp
- A message describing the change
- The actual changes (diff)

### 🔹 Why Commits Matter:
- They form the **history** of your project.
- Allow you to **track, revert, or review** changes.

### 🧠 Example:
```bash
git commit -m "Add login feature"
```
Creates a commit with a message describing the change.

---

## 🔄 Git Workflow

1. **Working Directory (WD)**  
   - Where you make changes to your files.
   - Example: `code.py` is edited.

2. **Staging Area (SA)**  
   - Temporary area to prepare changes before committing.
   - Command:  
     ```bash
     git add code.py
     ```

3. **Local Repository (LR)**  
   - Stores your commits locally.
   - Command:  
     ```bash
     git commit -m "Add new feature"
     ```

4. **Remote Repository (RR)**  
   - Hosted on GitHub, GitLab, etc., for collaboration.
   - Commands:  
     ```bash
     git push origin main   # Send changes  
     git pull origin main   # Get updates
     ```

5. **Checkout**  
   - Move between branches or commits.
   - Command:  
     ```bash
     git checkout feature-branch
     ```

---

### 🔄 Git Workflow Explained

1. **Working Directory (WD)**  
   - Where you make changes to your files.
   - Example: `code.py` is edited.

2. **Staging Area (SA)**  
   - Temporary area to prepare changes before committing.
   - Command:  
     ```bash
     git add code.py
     ```

3. **Local Repository (LR)**  
   - Stores your commits locally.
   - Command:  
     ```bash
     git commit -m "Add new feature"
     ```

4. **Remote Repository (RR)**  
   - Hosted on GitHub, GitLab, etc., for collaboration.
   - Commands:  
     ```bash
     git push origin main   # Send changes  
     git pull origin main   # Get updates
     ```

5. **Checkout**  
   - Move between branches or commits.
   - Command:  
     ```bash
     git checkout feature-branch
     ```

---

## 🏠 Working Directory (WD)
This is where you make changes to your files.

- Example: You edit `index.html` or `app.py`.
- These changes are not yet tracked by Git.

---

## 🧺 Staging Area (SA)
A temporary area where you prepare changes before committing.

- Command:
  ```bash
  git add filename
  ```
- Example:
  ```bash
  git add app.py
  ```

---

## 🗃️ Local Repository (LR)
This is your local Git database where commits are stored.

- Command:
  ```bash
  git commit -m "Your message"
  ```
- Example:
  ```bash
  git commit -m "Add login feature"
  ```

---

## 🌐 Remote Repository (RR)
A shared repository hosted on platforms like GitHub, GitLab, or Bitbucket.

- Push changes to remote:
  ```bash
  git push origin main
  ```
- Pull changes from remote:
  ```bash
  git pull origin main
  ```

---

## 🔁 Summary of Git Commands

| Stage             | Command Example                  | Purpose                          |
|------------------|----------------------------------|----------------------------------|
| Working Directory| `git status`                     | Check file changes               |
| Staging Area     | `git add file.txt`               | Stage changes                    |
| Local Repository | `git commit -m "message"`        | Save changes locally             |
| Remote Repository| `git push origin branch-name`    | Upload changes to remote         |
| Remote to Local  | `git pull origin branch-name`    | Download changes from remote     |

---

## ✅ Tips
- Use `git log` to view commit history.
- Use `git branch` to manage branches.
- Use `git clone` to copy a remote repo locally.

```
---

## 🔁 Git Flow

**Created by:** Vincent Driessen  
**Best for:** Large projects with scheduled releases (e.g., enterprise software)

### 🔧 Branches in Git Flow

1. **`main` (or `master`)** – Always contains production-ready code.
2. **`develop`** – Integration branch for features; reflects the latest delivered development changes.
3. **`feature/*`** – Used for developing new features.
4. **`release/*`** – Prepares code for production release.
5. **`hotfix/*`** – Used to quickly patch production issues.

### 🔄 Workflow

1. **Start a feature** from `develop`:
   ```bash
   git checkout develop
   git checkout -b feature/awesome-feature
   ```

2. **Finish a feature**:
   ```bash
   git checkout develop
   git merge feature/awesome-feature
   git branch -d feature/awesome-feature
   ```

3. **Create a release**:
   ```bash
   git checkout develop
   git checkout -b release/1.0.0
   ```

4. **Finish a release**:
   ```bash
   git checkout main
   git merge release/1.0.0
   git tag -a 1.0.0
   git checkout develop
   git merge release/1.0.0
   ```

5. **Hotfix a bug**:
   ```bash
   git checkout main
   git checkout -b hotfix/1.0.1
   ```

6. **Finish a hotfix**:
   ```bash
   git checkout main
   git merge hotfix/1.0.1
   git tag -a 1.0.1
   git checkout develop
   git merge hotfix/1.0.1
   ```

### ✅ Pros
- Clear structure for managing releases and hotfixes.
- Ideal for parallel development and long-term projects.

### ❌ Cons
- Can be **complex** and **heavy** for small teams or fast-paced environments.
- Requires discipline in managing multiple branches.

---

## 🌐 GitHub Flow

**Created by:** GitHub  
**Best for:** Continuous deployment, web apps, startups

### 🔧 Branches in GitHub Flow

1. **`main`** – Always deployable.
2. **Feature branches** – Created from `main` for each new piece of work.

### 🔄 Workflow

1. **Create a branch**:
   ```bash
   git checkout -b feature/short-description
   ```

2. **Push and open a Pull Request (PR)**:
   - Push to GitHub.
   - Open a PR to `main`.

3. **Discuss and review**:
   - Team reviews the PR.
   - CI/CD runs tests.

4. **Merge to `main`**:
   - Once approved and tested, merge the PR.
   - Deploy immediately if needed.

### ✅ Pros
- **Simple and fast** – great for continuous delivery.
- Encourages frequent integration and deployment.
- Easy to understand and adopt.

### ❌ Cons
- No built-in support for release or hotfix branches.
- Not ideal for complex release cycles or multiple environments.

---

## 🆚 Git Flow vs GitHub Flow

| Feature               | Git Flow                          | GitHub Flow                      |
|-----------------------|-----------------------------------|----------------------------------|
| Complexity            | High                              | Low                              |
| Best for              | Scheduled releases                | Continuous deployment            |
| Branches              | `main`, `develop`, `feature/*`, `release/*`, `hotfix/*` | `main`, `feature/*`              |
| Release Management    | Built-in                          | Manual or external tools needed  |
| Hotfix Support        | Yes                               | Manual                           |

---
