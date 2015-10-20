---
published: true
description: Background technology guide.
title: "Background Technology I: Git and Github"
---






In this post we will introduce the background technology involved in the project. This means: The technology which we are going to use to manage and develop the project, not the actual technology that runs the project.

#Version control: Git & Github
Git is the actual standard in distributed version control. This is easier when you see an example.


##Setup Git

Download Git: [git-scm](http://git-scm.com/)
And install it. Is recommended to let the things in the installer as defaults.

Install a Git GUI Interface for easy interaction. One of the most useds is the client from Github: [Github Desktop](https://desktop.github.com/)

With Git, we have installed the git bash, that is like a command line but with the powerful of the unix command-lines. I will show you basic Bash commands to navigate and operate in folders:

    cd [folderName]: access the folder
    cd .. : go up one folder
    ls: List the files and folders in the directory
    rm [folder-fileName]: remove the folder or file
    cat [fileName]: show content of file
    mkdir [folderName]: create new folder
    touch [fileName]: create new file

You can read a more deep Cheat Sheet here: [Linux Bash Cheat Sheet](https://docs.google.com/viewer?url=http%3A%2F%2Fcli.learncodethehardway.org%2Fbash_cheat_sheet.pdf)
    
And there are some basic Git commands to work with it:

	git init [project-name]: Creates a new local repository with specified name
    git clone [url]: Downloads a project from the url
    git status: Lists all new or modified files to be committed
    git add [file]: Add the file to the next commit. Tip: git add . (adds everything new in the folder)
    git commit -m "[description]": Save the commit into the history
    git push [alias] [branch]: Uploads the local branch to the remote repository
    git pull: Update the local repository
   
You can take a look at the very nice cheat sheet made by the guys from Github [Git Cheat-Sheet](https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf).


##Creating a new repo and adding something to it

Let's create a new repository in our local machine. For this we're going to create a folder and create a new directory with Git:

```bash	
mkdir newProject
cd newProject
git init
```

Now this is an empty repo. Let's create something to add to our repo and see the status of the repo:

	touch README.md 
	git status

With the first command we create a markdown file, and with the second we get the actual status of the files in the repo. We see that the README.md file is in red color under the Untracked list. This means that the file is not being tracked for the next commit. 

If we add it now and see the status again we should see it under the tracked list of changes or new files:

	git add .
    git status

![Adding file](http://i.imgur.com/ZuFxBFB.gif)

Now that we are tracking the changes, we should commit for have a log of the changes we made.

	git commit -m "Init commit"

##Creating a remote repository in Github

Now we have to go to [Github](!github.com) and if we don't have an account we have to create one. Once created we're going to create a new repository. First click in the cross at the right-up corner and click in **New repository**. Give a name to the repository and a description and let the rest default. Now click on Create repository button. 

![Creating a new repo on github](http://i.imgur.com/3ZFaDrg.gif)

And then, we have to tell to our local repository where it has to upload the files (the remote repo), so you can copy the commands directly from the page after creating the repo:

	git remote add origin https://github.com/[GITHUBNAME]/[REPONAME].git
	git push -u origin master
    
The first one adds the remote repository with the name *origin* and the second one upload the files to Github.

##Branching
Branching is a very useful concept to know. When we are using Git we are allways using a branch where our commits and stuff goes. By default this is the Master branch. 

Think we have a game and we want to add a new feature to this game like for example the score of the game. So in order to do this we will create a new branch called for example *feature_score*. So now when we are in this branch all the stuff we made is not present in the *master* branch, so for example if we do some mistakes and break the game we can destroy this branch or change to the master branch and the game stil running (without the score, of course). Its a bit difficult to understand without seeing it, but let's try to get it with some examples.

![Branchs](http://i.imgur.com/NlgiE1W.png)

Create new branch named *feature_score*:

	git checkout -b feature_score

Now in the git bash we can see we are in the feature_score branch. Now add the score to the game (we're going to create just a txt file), add it, commit to the branch and push it:
	
    touch score.txt
    git add score.txt
    git commit -m "added score"
    git push origin feature_score
    
To look what happend list the folder with **ls**. And you should see two files:
	README.md
    score.txt

Now we're changing to the master branch, which en theorical doesn't have the score yet:

	git checkout master
    ls

Now when we list the folder again we only see the **README.md** file. That's it! We have a new feature. So if everything is working, now we are going to merge it into the master branch, so first we should change our active branch to the master, and use **git merge [branch]** to merge:

	git checkout master
	git merge feature_score
    
Now we have the both branchs merged but locally, let's push to Github to the other users with **git push origin master**.
