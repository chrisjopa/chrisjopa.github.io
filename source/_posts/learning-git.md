---
title: Learning Git
date: 2016-03-24 21:34:08
tags:
---

Git is the standard Version Control System for software developers. Version control systems like Git enable developers to reliably collaborate with one another. Git also saves a snapshot of every version of your code, which comes in handy when you need to track down software bugs. Git is a complex piece of software. In this post I'm going to give a brief history of Git and explain how it works.

<!--more-->

## History

GIT was developed in 2005 by Linus Torvalds of Linux so their development team can efficiently share files with each other. Torvalds is the man behind the Linux kernel, which is a Unix-like operating system. Originally changes to the system were sent around using patches and archive files. After a decade, they began using BitKeeper, which is a proprietary distributed revision control system. Eventually, BitKeeper revoked every free user license since a developer named Andrew Tridgell created a client, which interoperated with BitKeeper to give free users some features which only commercial users had. Torvalds did not want to go back to sharing files with patches so he created Git.

Since coding is a collaborated effort and many things can go wrong in a project, version control systems are absolutely essential for a programmer. Before version control systems, programmers would share code through emails and floppy disks which makes it very tedious to track bugs and changes to the code. Version control systems help programmers keep track of code revisions. Also, they acknowledge that there is only one version of the project and all past versions and variants are saved within the system, which can be accessed at any time. Every time a new version of a project is saved, you are required to provide a short description what was changed. Because of version control systems, coders have an easier time saving their changes and knowing what is actually different between each commit.

## How Git Works

Git is a distributed version control system that keeps a central server storing the history of the files, and collaborators have their own local history as well. Team members have their version of different files that they can work on when they please. Everyone on the team can commit or merge all their changes into one common version. Git saves these versions or snapshots of the project so there will be no question where the most recent version of the project is located. 

The main difference between Git and other version control systems is how Git perceives its data. Other systems think of their information as a set of files and how each file changes over time. Git thinks of its data more like a set of “snapshots” of a repository. Every time you commit or save a state of your project, Git stores a picture of what your files looks like at that moment. If some files do not change between commits, Git does not store that file again but links it to the previous identical file. Git thinks about its information more like a “stream of snapshots”. This makes Git act like a mini file system with some powerful tools.

By using Git, different versions of a project between a team can saved and viewed efficiently.  A team member can modify a few different files in a project to fix bugs or for whatever reason. First, this team member made these changes locally to their own version of the file. Then they can tell Git to take a snapshot of their changes with the add command which stores their changes in the staging area. With the commit command, snapshots of the files are saved in your Git repository that can be pushed to the server. These changes can be shared throughout the team on their server while any team member can make changes to these files without erasing any other files. 

Git lets developer teams efficiently save, share, and modify different versions of their repository. For new developers it is essential to learn Git because it is the industry standard for software engineering. 

## Resources

1. [Git History Article](https://git-scm.com/book/en/v2/Getting-Started-A-Short-History-of-Git)
2. [Why Use Git Article](https://www.git-tower.com/learn/git/ebook/command-line/basics/why-use-version-control)
3. [Code School Git Free Course](https://www.codeschool.com/courses/try-git)
