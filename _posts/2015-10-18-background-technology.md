---
published: true
description: Background technology guide
title: Background Technology
---


In this post we will introduce the background technology involved in the project. This means: The technology which we are going to use to manage and develop the project, not the actual technology that runs the project.

##Version control: Git & Github
Git is the actual standard in distributed version control. This is easier when you see an example.


###Setup Git

Download Git: [git-scm](http://git-scm.com/)
And install it. Is recommended to let the things in the installer as defaults.

Install a Git GUI Interface for easy interaction. One of the most useds is the client from Github: [Github Desktop](https://desktop.github.com/)

With Git, we have installed the git bash, that is like a command line but with the powerful of the unix command-lines. I will show you basic Bash commands to navigate and operate in folders:

	cd folderName: access the folder
    cd .. : go up one folder
	ls: List the files and folders in the directory
    rm folder-fileName: remove the folder or file
    cat fileName: show content of file
    mkdir folderName: create new folder
    touch fileName: create new file
    
###Creating a new repo

we're going to create a new repository in our local machine. For this we're going to create a folder and create a new directory with Git:
	
    mkdir newProject
    cd newProject
    git init