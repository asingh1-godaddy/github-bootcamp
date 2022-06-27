 # Git(Hub) 101

## Table of Contents
- [Git(Hub) 101](#github-101)
  - [Table of Contents](#table-of-contents)
  - [Prequisites](#prequisites)
  - [Optional Prequisites](#optional-prequisites)
  - [Overview](#overview)
- [Git vs Github](#git-vs-github)
  - [What is Git?](#what-is-git)
  - [What is Github?](#what-is-github)
  - [Github Alternatives and Tools](#github-alternatives-and-tools)
- [Walkthrough Lab](#walkthrough-lab)
  - [Cloning](#cloning)
  - [Branching](#branching)
    - [Checking Out Branches](#checking-out-branches)
  - [Remote vs Local Branch](#remote-vs-local-branch)
  - [Saving and Committing Changes](#saving-and-committing-changes)
  - [Pushing up your changes](#pushing-up-your-changes)
  - [Opening a Merge Request](#opening-a-merge-request)
- [Other Common Scenarios](#other-common-scenarios)
  - [Forks](#forks)
  - [Reverts and Resets](#reverts-and-resets)
  - [Rebases](#rebases)
  - [Merge Conflicts](#merge-conflicts)
  - [Finding Help](#finding-help)
- [Tools Demo](#tools-demo)
  - [VSCode](#vscode)
  - [Github Desktop](#github-desktop)
- [Github Console Features](#github-console-features)
  - [Issues](#issues)
  - [Branch Summary](#branch-summary)
  - [Versioning](#versioning)
  - [Discussions](#discussions)
  - [Projects](#projects)
  - [Wiki](#wiki)

---

## Prequisites
- [Create a github account](https://github.com) (if not already present)
- [Install git](https://git-scm.com/downloads)


## Optional Prequisites
- [Install Visual Studio Code](https://code.visualstudio.com/) (or use an editor of your choice) (link here)
- [Install github desktop](https://desktop.github.com/)

---
 
## Overview
Git is a version control tool that helps keep track of written code history and management as well as
coordinate work between multiple people writing into the same code base

<br/>

Quick Terminology (will go into further depth later):
- Branch: Independent copy of the repository/project. Changes do not affect other active copies.
- Commit: A summary of saved changes within the project, packaged as a single instance
- Pull Request: An operation to submit changes from the copy back into the main

Simple Flow:

<br/>

![Simple Worflow](https://i0.wp.com/build5nines.com/wp-content/uploads/2018/01/GitHub-Flow.png)
*note: master branches are now referred to as main branches

<br/>

---

# Git vs Github
Whereas Git is the tool which does bulk of the work, Github is the online interface that helps you
visualize all the operations you are performing and even perform them for you in some cases. It also
stores the repository online so your work is no longer just local to your computer hard drive
 
---

## What is Git?
 
Git is a CLI (command line interface) program used primarily within a terminal. e.g.
 
- Mac/Linux built in terminal
 
- Windows options via [Git Bash](https://gitforwindows.org/)
 
You might've heard of commands such as `ls`, `echo`, or `pwd` that list your current directory, it's contents, and such
 
---

**Usage Examples**
```
git checkout <branch name>
git add <file>
git commit -m "<commit message>"
```
Format is usually `<program name> <command> <options>`
 
In this case, `git add <file>`

---
 
## What is Github?
 
**Diagrams/Images**
 
---

## Github Alternatives and Tools


[GitLab](https://about.gitlab.com/)

[BitBucket](https://bitbucket.org/product)
 
[Github Desktop](https://desktop.github.com/)
 
---
# Walkthrough Lab
 
## Cloning

Cloning a repository refers to downloading a copy of the main branch onto your hard drive.
Changes you make to that code won't reflect the online copy until those changes are "committed" and "pushed".

The git file or file source link is needed to clone it. Github itself offers a multitude of ways to clone a repo, which you can find with the green `Code` button at the top right of the github repo page:

<br/>

![](images/github_clone.png)

- HTTPS
- SSH
- GitHub CLI
- GitHub Desktop
- Download ZIP

**Lab Objectve**
 
- "Clone" a local workable copy of the repo

Command: `git clone <link to .git file>`

Note: 
* Preferably you should organize your projects and clone into some sort of documents/tutorials directory
* Not everyfile will be dumped into where you run the command, but the contents of the copy will be put into another folder with the project name as its title
  * i.e. cloning this repo into `~/Documents` won't create `~/Documents/README.md`, `~/Documents/<all your files>`, etc but rather `Documents/github-bootcamp/<all your files>`

---
 
## Branching
 
 A branch is an independent copy of the repository. Changing one branch will not change another. Branches typically follow a hierarchy where the main branch rarely changes and has the most stable and working version. There may also be developer, test, and feature branches with their own unique changes that adopt each other in at some point. 

 Branches can be based off of any other branch, or any other commit. When put that way, a branch is really nothing but the latest commit in a culmination of isolated commits (isolated as in saved in not actively affecting other branches, unless those branches choose to take them in manually).

<br/>

A little more complex diagram:

<br/>

![](https://user-images.githubusercontent.com/18033666/40845164-dbb9a75e-6583-11e8-8a17-8bc2b03d0350.png)

People typically only work on mostly one, if not sometimes a few unrelated branches, at a time. Even then they don't become complex webs of related commits. Just keep on coding and you'll see it's easier to conceptualize than a lot of graphs portray
 
---
 
### Checking Out Branches
 
When you want to make or "checkout" a new branch, you can do so via the terminal or github. Think of "checking out" the same way you would a library book, except there's unlimited copies.

Via terminal:
- To make a new branch: `git checkout -b <new branch name>`
- To view other branches:
  - When you initially clone a repo you generally only have what branches already existed at time of cloning and any new branches you've made
  - If someone makes a new branch you'd like to see, after you've cloned it, you will need to
    - To download the latest respository "state": `git fetch` (will explain more next slide)
    - To actually switch to a branch after update: `git checkout <branch name>`
  - Else you can switch to the branches you already know you have
    - If a branch you checked out is "out of date" (someone made )

Via Github:

- On the top right of the repo page, you'll see the branch icon with the name of the current branch you are viewing. From here, you can view (aka check out) other people's branches or create a new branch by typing the a name in the search bar (provided that branch name doesn't already exist)

![](images/github_branching.png)
 

 Note:
- The naming of a branch typically has conventions dictated by your team or project. Examples include
  - `name/title` e.g. `robert/login-page`
  - `scope/title`  e.g. `bugfix/incorrect_sum`
  - `title` e.g. `center_login_div`

**Lab Objectve**
 
- Checkout an existing branch `sammy/aboutme` and notice the new file under `/labfiles/sammy.md`
- Checkout the main branch again (titled master)
- Checkout a new branch with convention `<your name>/aboutme`

<br/>

---

## Remote vs Local Branch
 
A remote branch is the saved branch data as known by your online Github account.

A local branch is the saved branch data as known by your hard drive.

<br/>

If I make changes to my aboutme file in my editor, those changes only exist on my computer. If you try to fetch and pull my changes, you won't see the changes I've saved since I haven't modified my remote branch. AKA github.com doesn't know I've made those changes because I haven't "told" github about it yet; I haven't "pushed up" those changes. Therefore it can't communicate to you the changes I made and you cannot view them. The same goes for everyone else's branches. Whatever you `File > Save` or `Cmd + S` will not immediately be known by github.

<br/>

---
 
## Saving and Committing Changes
 
**Explanation**
(add and commit)
 
**Diagrams/Images**
 
---
 
## Pushing up your changes
 
**Explanation**
 
---
 
## Opening a Merge Request
 
**Explanation**
(includes commenting and approving/denying, squashing)
 
**Diagrams/Images**

---
 
# Other Common Scenarios

 
## Forks
 
**Explanation**
 
**Diagrams/Images**
 
---
## Reverts and Resets
 
**Explanation**
 
**Diagrams/Images**
 
---
## Rebases
 
**Explanation**
 
**Diagrams/Images**
 
---
 
## Merge Conflicts
 
**Explanation**
 
**Diagrams/Images**
 
---
 
## Finding Help
 
**Explanation**

**Diagrams/Images**
 
---
 
# Tools Demo
 
## VSCode
 
## Github Desktop

 
---
 
# Github Console Features

 
## Issues
 
**Explanation**
 
**Diagrams/Images**
 
---
 
## Branch Summary
 
**Explanation**
 
**Diagrams/Images**

---

## Versioning
 
**Explanation**
 
**Diagrams/Images**
 
---
 
## Discussions
 
**Explanation**
 
**Diagrams/Images**
 
---
 
## Projects
 
**Explanation**
 
**Diagrams/Images**
 
---
 
## Wiki
 
**Explanation**
 
**Diagrams/Images**