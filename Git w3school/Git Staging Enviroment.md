## Git Staging Environment

One of the core functions of Git is the concepts of the Staging Environment, and the Commit.

As you are working, you may be adding, editing and removing files. But whenever you hit a milestone or finish a part of the work, you should add the files to a Staging Environment.

**Staged** files are files that are ready to be **committed** to the repository you are working on. You will learn more about `commit` shortly.

For now, we are done working with `index.html`. So we can add it to the Staging Environment:

### Example

```shell
git add index.html
```

The file should be **Staged**. Let's check the status::

### Example

```shell
git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached ..." to unstage)
    new file: index.html
```

Now the file has been added to the Staging Environment.

---

## Git Add More than One File

You can also stage more than one file at a time. Let's add 2 more files to our working folder. Use the text editor again.

A `README.md` file that describes the repository (recommended for all repositories):

### Example

# hello-world  
Hello World repository for Git tutorial  
This is an example repository for the Git tutoial on https://www.w3schools.com  
  
This repository is built step by step in the tutorial.

A basic external style sheet (`bluestyle.css`):

### Example

body {  
background-color: lightblue;  
}  
  
h1 {  
color: navy;  
margin-left: 20px;  
}

And update `index.html` to include the stylesheet:

### Example

<!DOCTYPE html>  
<html>  
<head>  
<title>Hello World!</title>  
<link rel="stylesheet" href="bluestyle.css">  
</head>  
<body>  
  
<h1>Hello world!</h1>  
<p>This is the first file in my new Git Repo.</p>  
  
</body>  
</html>

Now add all files in the current directory to the Staging Environment:

### Example

```shell
git add --all
```

Using `--all` instead of individual filenames will `stage` all changes (new, modified, and deleted) files.

### Example

```shell
git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached ..." to unstage)
        new file:   README.md
        new file:   bluestyle.css
        new file:   index.html
```

Now all 3 files are added to the Staging Environment, and we are ready to do our first `commit`.

**Note:** The shorthand command for `git add --all` is `git add -A`