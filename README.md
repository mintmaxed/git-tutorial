# git tutorial s24

## introduction
### basics of git
Git and github are a basic system for organizing and storing files, primarily useful for managing larger coding projects and storing progress outside of local machines. This tutorial will explain the basics of what git is, how it is organized, and how it can be accessed using the command line.
For the purposes of this tutorial, it will be assumed that the user has git, bash, and python already installed and up to date.

### initialization
To start, open the **Terminal** app on your machine. We will initialize our git repository by using the command
```shell
git init
```

If you would like to initialize within a particular directory on your device, you can `cd` into the desired folder before intializing.

The terminal should return:
```shell
Initialized Git repository in C:/Users/[user]/[location]/.git/
```

### new file
Let's make a basic file to commit to our repository. In the same folder/directory, create a new file. You can do this one of two ways: First, open your File Explorer UI, navigate to the folder, and right click to create a new file. Alternatively, you can enter into the command line prompt
```shell
touch example.py
```
Great! Now we should have a basic python file. Open it in the text editor of your choice - I'll be using VSCode. Here is my sample program example.py: 
```python
a = 1
b = 2
c = 3

print("hello!")
print(a + b)
print(b + c)
```

## commits
### committing
If you check the status now by entering in the command line `git status` you will see "example.py" show up in red: that is because we have not staged or tracked our changes yet. **Staging** is the process of preparing updates to be committed. We can stage "example.py" by entering the following command:
```shell
git add example.py
```

Now, if you run `git status` again, you will see `example.py` in green, labeled as "Changes to be committed." This is great! We've staged example.py, and can now push it to the main repository. We will commit it by using the command
```shell
git commit -m "initial commit"
```
Every commit comes with a message attached. This is especially useful in larger-scale projects, so you can let yourself (and others) know what changes you have made. Whatever message you put within the quotation marks will get logged as the commit message. 

If you check `git status` again, there should be no red or green messages, because the local is fully up to date with the repository.

### making changes
