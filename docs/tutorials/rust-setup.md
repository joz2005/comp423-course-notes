* Primary author: [Joseph Zheng](https://github.com/joz2005)
* Reviewer: [Zhi Hang Yang](https://github.com/zyang310)

# Rust Setup

## Prerequisites

Before continuing, make sure you have the following:<br><br>
1. A **GitHub Account**: If you don't have one, [sign up here](https://github.com){:target="_blank"}<br>
2. **Git Installed**: If not installed, [click here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git){:target="_blank"}<br>
3. **Visual Studio Code (VS Code)**: The code editor we're going to use, install it [right here](https://code.visualstudio.com/){:target="_blank"}<br>
4. **Docker**: The development container to be used, [install it here](https://www.docker.com/products/docker-desktop){:target="_blank"}

## Part 1: Setting up Git and GitHub Project

### Step 1: Initialize your Git Repository

(A) Open your terminal or command prompt<br>
(B) Create a new directory for your project
!!! note "If you want to organize your project"

    If you want to organize this project in your own manner, 
    ``` cd ``` into the desired parent's directory first.

``` bash
mkdir rust-tutorial
cd rust-tutorial

```

(C) Initialize a new Git repository using the command below:

``` bash
git init
```

(D) Create a **README** file:

``` bash
echo "Rust Tutorial Setup" > README.md
git add README.md
git commit -m "Initial commit with README"
```

### Step 2: Creating your Remote Repository on GitHub

(A) Log in to your GitHub account and navigate to the [Create a New Repository](https://github.com/new){:target="_blank"} page.<br>
(B) Fill in the details accordingly below:<br>

* **Repository Name:** `rust-tutorial`
* **Description:** "This is a tutorial for setting up Rust in a dev container."
* **Visibility:** Public

(C) Do not initialize the repository with a README, .gitignore, or license.<br>
(D) Proceed to **Create Repository**.

### Step 3: Link your Local Repo to GitHub

(A) In your terminal in VS Code, enter

``` bash
git remote add origin https://github.com/<your-username>/rust-tutorial.git
```

Enter your GitHub username as a replacement for `<your-username>`

(B) Check your default branch name with the subcommand `git branch`. If it's not `main`, rename it to `main` using the command, ```git branch -M main```. It's often standard to have the default primary branch name to be `main`, so let's uphold this standard.<br>

(C) Push local commits to the GitHub repository:

``` bash
git push --set-upstream origin main
```

!!! note "What is `--set-upstream`?"

    `--set-upstream` is a special flag that pushes newly **untracked** branches onto the remote repository origin. Because branches are highly efficient and useful within workflows, it's important understand how a programmer can fully utilize this feature of git. This flag has a short form, `-u`.    

(D) In your web browser, refresh your GitHub repository to see the same commit you've made locally has now been *pushed* to remote. You can also use `git log` locally in VS Code to see the commit ID and message, which should match the ID of the most recent commit on your repository. 


## Part 2: Installing Rust

Per this tutorial, you're going to be installing **Rust**. You might be asking, why Rust? Rust is a flexible language with the benefits of memory safety at compile time, even without a garbage collection. Not only is it fast as C or C++, it also provides high-level code without sacrificing the benefits of low-level control over system resources. That's partly what makes Rust such a great language.

(A) Go to their website [here](https://www.rust-lang.org/tools/install){:target="_blank"}

* Install your bit version, whether it be 32 or 64

!!! note "If you're on an OS other than windows"

    Proceed to install Rust using the terminal command listed on the installation site!

(B) Once installed, a new instance of command prompt will be shown with some text

* Type **1**, then hit **Enter**
* If asked to allow changes, hit **Allow**

!!! note "**READ THIS BEFORE CONTINUING!**"

    If you are on a Mac, or have already installed Visual Studio 2022 (different from VS Code), you can skip (C) and (D)

(C) After completing previous steps, a **Visual Studio Installer** application will pop up

* Hit **Continue**

(D) After installation, you're prompted with installation for **C++ Build Tools** and **Windows 11 SDK**

* **Uncheck both of them**, and proceed to install:

!!! note "A heads up"

    This installation is pretty significant, so make sure your system has enough space!

(E) After the installation, go back to the command prompt, and type **1** and hit **Enter**

* After completing these steps, you should see multiple essential components of Rust being installed

(F) Hit **Enter** to close command prompt after installing

(G) Before moving on, reopen command prompt, and enter: 

``` bash
rustc --version
```

This should show your current version of Rust, which then means you installed Rust correctly!
Congratulations!


## Part 3: Creating a new Dev Container in Rust

### Step 1: Setting up Extension

(A) Go to **Extensions** tab on VS Code **(Ctrl+Shift+X) on Windows** or **(Shift+Cmd+X) on Mac**<br>
(B) Search for **`rust-analyzer`** published by **The Rust Programming Language** and [install it](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer){:target="_blank"}

### What is a Development (Dev) Container?

A dev container is a premade development environment that makes programming consistent between multiple machines. These environments
are determined by the configuration files we're about to create. Think of it as a virtual machine (VM) or a smaller computer running
inside your own computer.

### Step 2: Configuring Dev Container
(A) There are many ways to create this essential part to a dev container. Let's do it in the terminal. Make sure you're in your **project folder**, and run in terminal:
``` bash
mkdir .devcontainer
```
(B) We want to put the **dev container configurations** inside this folder. Let's relocate into that configuration directory using:
``` bash
cd .devcontainer
```
(C) You should see your **local directory in your terminal change**, as you've relocated into .devcontainer. Let's create the dev container configuration file by running this command:
``` bash
touch devcontainer.json
```
(D) You should've created a **.json** file. Let's edit it manually -
copy and paste the below code into the file:
``` json
{
    "name": "Rust Tutorial",
    "image": "mcr.microsoft.com/devcontainers/rust:latest",
    "customizations": {
        "vscode": {
            "settings": {},
            "extensions": [
                "rust-lang.rust-analyzer"
            ]
        }
    }
}
```

What do these fields mean? Here are some basic descriptions:

* `name`: A descriptive name for your dev container
* `image`: The Docker image you use, which in this case is the latest version of a Rust environment
* `customizations`: Adds useful configurations to VS Code, like the Rust extension you installed earlier. In the VS Code extensions marketplace, you can find these customizations with a keyword. Having this field in this configuration makes sure other developers have these extensions installed in their containers automatically.

### Step 3: Starting the Dev Container
(A) Open up **Command Palette (Ctrl+Shift+P, Shift+Cmd+P)** and search for `Dev Containers: Reopen in Container`<br>
(B) After running the above operations, you should see some changes to your workspace. Parts of your terminal should be highlighted, and in the bottom left of your workspace, there should be a light-blue highlight showing that you're in a dev container

Congratulations for making it this far! You're almost done!

## Part 4: Creating your first Rust program!
Remember the components of Rust we've installed earlier? One useful one is **Cargo**, the official **package manager and build system** of Rust projects, dependencies, and builds. It's like the `pip` for Python, `npm` for Node.js and `make` for C/C++.

(A) Let's create a new project within our workspace. Make sure you're in the **/rust-tutorial** directory. If not, `cd` into that directory. Run the following command in the terminal:
```
cargo new my_project --bin --vcs none
```
!!! note "What do these commands do?"
    * `cargo`: The package manager and build system of Rust
    * `new`: Creates a new directory with necessary Rust project file, including `Cargo.toml` and `src` (You can check this in your own files)
    * `my_project`: The name of your new project directory
    * `--bin`: Specifies that the project should be **binary project**, basically producing an executable. This also generates the `main.rs` file under `src` with some starter code inside
    * `--vcs none`: This flag prevents Cargo from initializing a version control system, since we've already done that earlier in this tutorial

Great job so far for understanding this tutorial! Just a couple more steps left!

(B) Let's observe the Rust file we've just created!

* `fn`: Represents a function in Rust
* `main`: The default function name, and the first function ran in this Rust file
* `println!()`: The function to print stuff onto the console for Rust
* `Hello, world!`: The initialized string literal that's created when running the previous command

Let's change the `Hello, world!` string to `Hello COMP423!` to fit our course!


(C) What we want to do now is to compile that `main.rs` executable. To start, let's maneuver into our created project:
``` bash
cd my_project
```

(D) Let's then run:
``` bash
cargo build
```
!!! note "What does `cargo build` do?"
    For some much needed explanation, `cargo build` generates a compiled binary in the `target/debug` directory. It's very similar to `gcc`'s compiling system, where the command `gcc -c <your-file>.c` with the flag `-c` compiles a `.c` file into an `.o` object file. 

(E) For our last step, let's run our Rust file! Run this command:
``` bash
cargo run
```

In your terminal, you should see "Hello COMP423!", meaning you've successfully executed the Rust file!

!!! note "Difference between `build` and `run`"
    `cargo build` **only compiles** the project and generates the binary code for that project, while `cargo run` can **compile** the project if necessary, and **executes** the binary immediately

## Congrats, you've finished this Rust setup tutorial!
- Tested on Mac OS