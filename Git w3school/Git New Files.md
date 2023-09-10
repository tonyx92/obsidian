## Git Adding New Files

You just created your first local Git repo. But it is empty.

So let's add some files, or create a new file using your favourite text editor. Then save or move it to the folder you just created.

If you want to learn how to create a new file using a text editor, you can visit our HTML tutorial:  
[HTML Editors](https://www.w3schools.com/html/html_editors.asp)

For this example, I am going to use a simple HTML file like this:

### Example
```html
<!DOCTYPE html>  
<html>  
<head>  
<title>Hello World!</title>  
</head>  
<body>  
  
<h1>Hello world!</h1>  
<p>This is the first file in my new Git Repo.</p>  
  
</body>  
</html>
```


And save it to our new folder as `index.html`.

Let's go back to the terminal and list the files in our current working directory:

### Example

```shell
ls
index.html
```

`ls` will **list** the files in the directory. We can see that `index.html` is there.

Then we check the Git `status` and see if it is a part of our repo:

### Example

```shell
git status
On branch master

No commits yet

Untracked files:
  (use "git add ..." to include in what will be committed)
    index.html

nothing added to commit but untracked files present (use "git add" to track)
```

Now Git is **aware** of the file, but has not **added** it to our repository!

Files in your Git repository folder can be in one of 2 states:

-   Tracked - files that Git knows about and are added to the repository
-   Untracked - files that are in your working directory, but not added to the repository

 When you first add files to an empty repository, they are all untracked. To get Git to track them, you need to stage them, or add them to the staging environment.

We will cover the staging environment in the next chapter.