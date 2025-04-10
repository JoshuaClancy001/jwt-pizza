# Git Branches Curiosity Report

## Motivation behind the Curiosity about Git Branches
1. When I first heard of git branches I had no idea what they were but we dont really talk about them in the CS program at BYU
2. After taking CS 324 I learned about forking processes and how they can be used to create new processes that are similar to the parent process. I thought that git branches were similar to this concept.
3. I have heard of git branches before but I have never used them. I have always just used the master branch and never really thought about using branches.
4. I am trying to get into the Sandbox program and realize that I need to use branches because I am working with another developer and we need to be able to work on the same project at the same time.

## What I learned about Git Branches
1. There are other ways to create copies of your code but they typically copying over the entir project which is very inefficient.
2. Branches are a way to create a copy but is super lightweight so creating and switching between branches is very fast.
3. Git stores Data in snapshots so when you commit it creates a commit object that stores a pointer to the snapshot of the content you staged.
4. Branches are just pointers to a commit object so when you create a new branch it just creates a new pointer to the same commit object.
5. Branches are super useful when you are working on a project with multiple people because you can work on different features at the same time without interfering with each other.

## Steps to create a new branch and what happens
1. Use the command `git branch <branch-name>` to create a new branch
2. Doing this will create a new pointer to the same commit object that the current branch is pointing to
3. You can then use the command `git checkout <branch-name>` to switch to the new branch
4. Git keeps a HEAD pointer to keep track of the current branch you are on
5. When you commit on the new branch it will create a new commit object and move the branch pointer and HEAD pointer to the new commit object
6. The Master branch (the branch you were on when you ran the checkout command) will not be affected by the new branch and stay at the same commit object
7. You can then merge the new branch back into the master branch by using the command `git merge <branch-name>`

## Conclusion
1. Git branches are super useful when working on a project with multiple people
2. They are super lightweight and fast to create and switch between
3. They are just pointers to commit objects so they are very efficient
4. They are a great way to work on different features at the same time without interfering with each other
5. I will definitely be using branches in the future when working on projects with other people