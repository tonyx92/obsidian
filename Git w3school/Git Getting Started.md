## Git Install

You can download Git for free from the following website: [https://www.git-scm.com/](https://git-scm.com/)

---

## Using Git with Command Line

To start using Git, we are first going to open up our Command shell.

For Windows, you can use Git bash, which comes included in Git for Windows. For Mac and Linux you can use the built-in terminal.

The first thing we need to do, is to check if Git is properly installed:

### Example

```shell
git --version
git version 2.30.2.windows.1
```

If Git is installed, it should show something like `git version X.Y`

---

## Configure Git

Now let Git know who you are. This is important for version control systems, as each Git commit uses this information:

### Example

```shell
git config --global user.name "w3schools-test"
git config --global user.email "test@w3schools.com"
```

Change the user name and e-mail address to your own. You will probably also want to use this when registering to GitHub later on.

**Note:** Use `global` to set the username and e-mail for **every repository** on your computer.

If you want to set the username/e-mail for just the current repo, you can remove `global`

---

## Creating Git Folder

Now, let's create a new folder for our project:

### Example

```shell
mkdir myproject
cd myproject
```

`mkdir` **make**s a **new directory**.

`cd` **changes** the **current working directory**.

Now that we are in the correct directory. We can start by initializing Git!

**Note:** If you already have a folder/directory you would like to use for Git:

Navigate to it in command line, or open it in your file explorer, right-click and select "Git Bash here"

---

## Initialize Git

Once you have navigated to the correct folder, you can initialize Git on that folder:

### Example

```git
git init 
Initialized empty Git repository in /Users/user/myproject/.git/
```

You just created your first Git Repository!

**Note:** Git now knows that it should watch the folder you initiated it on.

Git creates a hidden folder to keep track of changes.