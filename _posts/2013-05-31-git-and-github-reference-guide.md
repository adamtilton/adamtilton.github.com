---
layout: post
title: "Git and Github Reference Guide"
description: ""
category: 
tags: []
---
{% include JB/setup %}
[1]: http://rogerdudler.github.com/git-guide/files/git_cheat_sheet.pdf
[2]: http://try.github.com/levels/
[3]: https://github.com/AlexZeitler/gitcheatsheet/blob/master/gitcheatsheet.pdf?raw=true
[4]: http://www.git-tower.com/files/cheatsheet/Git_Cheat_Sheet_grey.pdf
[5]: https://na1.salesforce.com/help/doc/en/salesforce_git_developer_cheatsheet.pdf
[6]: http://ndpsoftware.com/git-cheatsheet.html
[7]: http://git-scm.com/docs
[8]: http://stackoverflow.com/questions/11816424/understanding-the-basics-of-git-and-github

## Subtle difference between git and github
Git is a version control system; think of it as a series of snapshots (commits)
of your code. You see a path of these snapshots, in which order they were
created. You can make branches to experiment and come back to snapshots you
took.

GitHub [read as a ‘Hub’ for Git repositories], is a web-page on which you can
publish your Git repositories and collaborate with other people.


## Basic Git Use
### Creating a new repo
Initialize a new git repository, then stage all the files in the directory and
finally commit the initial snapshot.

{% highlight %}

$ git init
$ git add .
$ git commit -m 'initial commit'

{% endhighlight %}

### Creating a new branch
Create a new branch named featureA, and check it out so it is the active
branch. Edit and stage some files and finally commit the new snapshot.

{% highlight %}

$ git branch featureA
$ git checkout featureA
$ (edit files)
$ git add (files)
$ git commit -m 'add feature A'

{% endhighlight %}

### Merging changes from branchA to master
Merge the featureA changes into the master branch context. Finally delete the
featureA branch.

{% highlight %}

$ git merge featureA
$ git branch -d featureA

{% endhighlight %}

### Contributing on GitHub
To contribute to a project that is hosted on GitHub you can fork the project on
github.com, which is useful if you do not have access to the original
repository.  If you do have access to the original repo (i.e. repos on
MehtaData) then you may clone the original repository, make a change, and push
back to the original repo on GitHub.

{% highlight %}

$ git clone git@github.com:MehtaData/SnowStorm.git
$ cd SnowStorm
$ (edit files)
$ git add (files)
$ git commit -m 'Explain what I changed'
$ git push origin master

{% endhighlight %}

## Best Practices
### Commit Related Changes Together
A commit should be a wrapper for related changes. For example, fixing two
different bugs should produce two separate commits. Small commits make it
easier for other developers to understand the changes and roll them back if
something went wrong. With tools like the staging area and the ability to stage
only parts of a file, Git makes it easy to create very granular commits

### Commit Often
Committing often keeps your commits small and, again, helps you commit only
related changes. Moreover, it allows you to share your code more frequently
with others. That way it‘s easier for everyone to integrate changes regularly
and avoid having merge conflicts. Having few large commits and sharing them
rarely, in contrast, makes it hard to solve conflicts. 

### Don’t Commit Broken Code
You should only commit code when it‘s completed. This doesn‘t mean you have to
complete a whole, large feature before committing. Quite the contrary: split
the feature‘s implementation into logical chunks and remember to commit early
and often. But don‘t commit just to have something in the repository before
leaving the office at the end of the day. If you‘re tempted to commit just
because you need a clean working copy (to check out a branch, pull in changes,
etc.) consider using Git‘s «Stash» feature instead.

### Write Useful Messages
(see: https://github.com/phonegap/phonegap/wiki/Git-Commit-Message-Format)

Begin your message with a short summary of your changes (up to 50 characters as
a guideline). Separate it from the following body by including a blank line.
The body of your message should provide detailed answers to the following
questions: 
– What was the motivation for the change?
– How does it differ from the previous implementation?
Use the imperative, present tense («change», not «changed» or «changes») to be
consistent with generated messages from commands like git merge

### Use (But Don’t Abuse) Branches
Branching is one of Git‘s most powerful features - and this is not by accident:
quick and easy branching was a central requirement from day one. Branches are
the perfect tool to help you avoid mixing up different lines of development.
You should use branches extensively in your development workflows: for new
features, bug fixes, ideas… 

### Agree to the Common Workflow
Git lets you pick from a lot of different workflows: long-running branches,
topic branches, merge or rebase, git-flow… Which one you choose depends on a
couple of factors: your project, your overall development and deployment
workflows and (maybe most importantly) on your and your teammates‘ personal
preferences. However you choose to work, just make sure to agree on a common
workflow that everyone follows. 


