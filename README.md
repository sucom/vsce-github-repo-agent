# GitHub Repo Agent

<p align="center">
  <img src="images/icon-sm.png" alt="Git Snapshots logo" width="120"/>
</p>

Frictionless, one-click GitHub repository setup with user control automation. Designed for educators, bootcamp hosts, and workshop trainers who need to distribute code instantly.

Git Repo Agent eliminates the administrative friction of creating repositories and inviting dozens of students manually. Just drop a text file with their GitHub usernames, click one button, and start teaching.

#### Other related extensions

- [Git Snapshots](https://marketplace.visualstudio.com/items?itemName=spajs.git-snapshots) - Instantly back up your work before taking the next step.
- [Git Pull Agent](https://marketplace.visualstudio.com/items?itemName=spajs.git-pull-agent) - For pulling changes from a remote repo.
- [Backup File](https://marketplace.visualstudio.com/items?itemName=spajs.backup-file) - For simple file snapshots without custom tags.
- [Tagged File Snapshots](https://marketplace.visualstudio.com/items?itemName=spajs.tagged-file-snapshots) - For simple file snapshots with tags.
- [Tagged Snapshots](https://marketplace.visualstudio.com/items?itemName=SPAjs.tagged-snapshots) - For Tagged snapshots of editor files (all/active tab group)
- [Backup Folder](https://marketplace.visualstudio.com/items?itemName=spajs.backup-folder) - To backup/snapshot a folder.


## ⚡ Quick Start

1. **Install** Git Repo Agent from the VS Code Marketplace.
2. **Create** a `.vscode/repo-users.txt` file in your project folder.
3. **Add** student GitHub usernames (one per line).
4. **Click** the `Git Repo Agent` status bar icon and select **Setup / Update Repository**.
5. **Enter** your Profile details (first time only) and select HTTPS or SSH handoff.

## 🚀 Installation

- Install from [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=spajs.github-repo-agent)
- Command Line: `code --install-extension spajs.github-repo-agent`

## ✨ Features

- **The Command Center**: A clean, single status bar entry point `$(github) Your-Profile` that handles both repository initialization and profile management.
- **Automated Invitations**: Automatically loops through your student list and sends GitHub collaborator invitations.
- **Explicit Removal**: Prepend a `-` to a username in your list to instantly revoke their access.
- **Stateful Memory**: Remembers which profile you are using for each specific local repository across VS Code restarts.
- **Secure Secret Storage**: Uses your operating system's native keychain (via VS Code) to securely encrypt your Personal Access Tokens (PATs).
- **Multiple Identities**: Seamlessly juggle "Work", "Personal", and "Bootcamp" profiles without constantly logging in and out.
- **Perfect Handoff**: Sets up the remote URL (`origin`) using your preferred transport (HTTPS or SSH) and steps aside so your native Git CLI can push the code.

## ⚙️ Configuration

### `repo-users.txt` Setup

The core of the extension relies on a simple text file to manage students.

```text
# .vscode/repo-users.txt

# Add users simply by typing their GitHub username
student-handle-1
student-handle-2 # Inline comments are ignored

# Remove users who dropped the class by prepending a minus sign
- dropped-student-handle
```


## ⚙️ Extension Settings [ ctrl + , ] / githubRepoAgent
- `githubRepoAgent.usersFilePath`: Relative path to the users list file within the workspace. [default: `.vscode/repo-users.txt`]
*Change this if you use an alternative editor (e.g., .codium/users.txt) or prefer storing the list elsewhere.*


## 🔐 Authentication & Setup Guide
Because Git Repo Agent interacts with the GitHub REST API to create repositories and manage users, it requires a Personal Access Token (PAT).

### 1. Generating the Right PAT (GitHub)

1. Go to GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic).

2. Click Generate new token (classic).

3. Select scope: Check repo (Full control of private repositories) and User Scope.

4. Set an Expiration (e.g., 30 days for a bootcamp).

5. Copy the token (you won't see it again).

### 2. The HTTPS vs SSH Handoff

Once the repository is created via this extension, it asks how you want to push your actual code (the Transport Layer).

- HTTPS (Recommended for Simplicity): The extension links the standard HTTPS URL. Your OS's native Git Credential Manager will handle the push authentication automatically.

- SSH (Advanced/Multiple Accounts): Links the git@github.com:... URL. Ensure you have your ~/.ssh/config and SSH keys properly configured on GitHub.

## 💡 Pro-Tip: The "Read-Only" Student Workaround
**The Goal**: You want students to be able to pull the codebase during the workshop, but you do not want them to push changes back to your repository.

**The GitHub Limitation**: If you create a repository under a standard Personal GitHub Account, anyone invited as a collaborator automatically receives both read AND write access. GitHub's free tier ignores requests for "Read-Only" access on personal accounts.

#### **The Solution**:

1. Create a Free GitHub Organization (e.g., github.com/My-Mastery-Bootcamps).

2. Free Organizations do support granular permissions.

3. When using Git Repo Agent, use the Organization's name as the "GitHub Username" in your active profile.

4. The extension automatically sends a pull (Read-Only) permission request, which the Organization will respect, perfectly securing your workshop code!

## ☑️ Requirements

- VS Code v1.85.0 or higher.

- Git installed on your system.

## ⚖️ License

MIT
