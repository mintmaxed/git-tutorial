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
```
If you run the program, it should output `hello!`

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
Let's edit `example.py` a bit. To the end of the file, add 
```python
print(a + b)
```
Now, if you run the program, it should output
```shell
hello!
3
```
Save your changes, and then switch back to the command line terminal. If we run `git status` now, you can see that `example.py` is marked in red as "modified," because changes have been made but have not yet been staged or committed. Let's fix that. Once again, to stage our changes, use the command:
```shell
git add example.py
```
and to commit them, use
```shell
git commit -m "print a + b"
```
You can double check that your staging and commits have been done correctly by entering `git status` at any point in this process.

## stashing
Stashing is a functionality where you can save your local changes, but clean the working tree. Any edits will be reverted to the previous commit, but your stashed changes can be recovered at any time. Having a clean working tree is especially useful when working with branches.

Let's make some sample changes to stash. To the bottom of example.py, add the following code: 
```python
# stashing
d = "secret stashed changes"
print(d)
```
Once you save, the full program should look like this:
```python
a = 1
b = 2
c = 3

print("hello!")
print(a + b)

#stashing
d = "secret stashed changes"
print(d)
```
and the output should be
```shell
hello!
3
secret stashed changes
```

If you run `git status` right now, you will see the same "modified: example.py" message in red as before.
Now, enter `git stash`. If you check example.py, you will see that the section we just added under the "stashing" comment no longer exists, because the file has been reverted to the previous commit. If you run `git status`, you will see that the working tree is clean.

To restore your stashed changes, you can use `git stash pop` or `git stash apply`. In this case, we won't be restoring our stashed changes, because we need the working tree to stay clean for our next section: branching.

## branching
### new branch
Git makes it possible to maintain different versions of the same project simultaneously using a system called branching. Just like with a real tree, git branches stem from common versions/commits but can each add their own unique changes without disturbing the status of any other branch. Let's try an example ourselves.

First, let's make a new branch. Enter:
```shell
git branch branch1
```
The terminal won't give you any feedback from the command itself, but we can verify that a new branch has been created by running only `git branch` (without any further arguments after branch). This should return:
```shell
  branch1
* master
```
The asterisk next to `master` indicates where we are currently working. To make changes to `branch1`, we will first need to move the head. To do this, run
```shell
git switch branch1
```

If you use `git branch` again, you will see that the asterisk has moved, and we can now continue with modifying branch1. Your `example.py` file should look the same as before, because this branch stems from our most recent commit and we have not made any changes yet.

### making changes (again)
To the bottom of `example.py` let's add a section just for branch1.
```python
# branch1
d = "teehee"
print(d)
print("this is a new branch!")
```
Commit your changes as usual:
```shell
git add example.py
git commit -m "branch1 updates"
```
branch1 is now set. To demonstrate how different branches work, let's make some different changes for the same file on the `master` branch. Switch back using
```shell
git switch master
```
The `example.py` file should have reverted once again to the original commit before `branch1`, with none of our `branch1` changes or previously stashed changes showing.
Let's make some different changes for the `master` branch.
