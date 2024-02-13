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

## files
Let's make a basic file to commit to our repository. In the same folder/directory, create a new file. You can do this one of two ways: First, open your File Explorer UI, navigate to the folder, and right click to create a new file. Alternatively, you can enter into the command line prompt
```shell
touch example.py
```
Great! Now we should have a basic python file. Open it in the text editor of your choice - I'll be using VSCode.
