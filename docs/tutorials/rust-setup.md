* Primary author: [Joseph Zheng](https://github.com/joz2005)
* Reviewer: [Zhi Hang Yang](https://github.com/zyang310)

# Rust Setup

## Prerequisites

Before continuing, make sure you have the following:<br><br>
1. A **GitHub Account**: If you don't have one, [sign up here](https://github.com)<br>
2. **Git Installed**: If not installed, [click here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)<br>
3. **Visual Studio Code (VS Code)**: The code editor we're going to use, install it [right here](https://code.visualstudio.com/)<br>
4. **Docker**: The development container to be used, [install it here](https://www.docker.com/products/docker-desktop)

# Part 1: Setting up Git and GitHub Project

## Step 1: Initialize your Git Repository

(A) Open your terminal or command prompt<br>
(B) Create a new directory for your project
!!! note "If you want to organize your project"

    If you want to organize this project in your own manner, 
    ``` cd ``` into the desired parent's directory first.

```
mkdir rust-tutorial

```

(C) Initialize a new Git repository using the command below:

```
git init
```

(D) Create a **README** file:

```
echo "Rust Tutorial Setup" > README.md
git add README.md
git commit -m "Initial commit with README"
```

## Step 2: Creating your Remote Repository on GitHub

(A) Log in to your GitHub account and navigate to the [Create a New Repository](https://github.com/new) page.<br>
(B) Fill in the details accordingly below:<br>

* **Repository Name:** `rust-tutorial`
* **Description:** "This is a tutorial for setting up a Rust in a dev container"
* **Visibility:** Public

(C) Do not initialize the repository with a README, .gitignore, or license.<br>
(D) Proceed to **Create Repository**.

## Step 3: Link your Local Repo to GitHub

(A) In your terminal in VS Code, enter

```
git remote add origin https://github.com/<your-username>/rust-tutorial.git
```

Enter your GitHub username as a replacement for `<your-username>`

(B) Check your default branch name with the subcommand `git branch`. If it's not `main`, rename it to `main` using the command, ```git branch -M main```. It's often standard to have the default primary branch name to be `main`, so let's uphold this standard.<br>

(C) Push local commits to the GitHub repository:

```
git push --set-upstream origin main
```

!!! note "What is `--set-upstream`?"

    `--set-upstream` is a special flag that pushes newly **untracked** branches onto the remote repository origin. Because branches are highly efficient and useful within workflows, it's important understand how a programmer can fully utilize this feature of git. This flag has a short form, `-u`.    

(D) In your web browser, refresh your GitHub repository to see the same commit you've made locally has now been *pushed* to remote. You can also use `git log` locally in VS Code to see the commit ID and message, which should match the ID of the most recent commit on your repository. 

# Part 2: Creating a new Dev Container in Rust

## Step 1: Setting up Extension
(A) Go to **Extensions** tab on VS Code **(Ctrl+Shift+X) on Windows** or **(Shift+Cmd+X) on Mac**<br>
(B) Search for **"Remote Development"** published by **Microsoft** and [install it](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)

## Step 2: Configuring Dev Container
(A) Open up **Command Palette (Ctrl+Shift+P, Shift+Cmd+P)** and search for **Add Dev Container Configuration Files...**<br>
(B) Select **Add configuration to workspace**, then search for **Rust**<br>
(C) Under **Rust**, select **bullseye** (should be *default*)<br>
(D) After selecting, you're prompted with additional features -- since we're starting out, just click **OK**

After completing these steps above, you should be greeted with a **devcontainer.json** file that is in a **.devcontainer** directory.

!!! note "Inside the .json file"

    You should see different fields within the **.json** file, 
    where **"name"** is set to **"Rust"** and the **"image"** 
    set to the according Rust dev container we've just made.
    This file mainly serves as a configuration file for your 
    dev container.