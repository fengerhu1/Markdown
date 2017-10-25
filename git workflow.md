# Git Workflows

![](https://github.com/fengerhu1/Markdown/blob/master/headline.png?raw=true)

- A Git Workflow is a recipe or recommendation for how to use Git to accomplish work in a consistent and productive manner. Git workflows encourage users to leverage Git effectively and consistently. 




## process of git workflow

![img](http://img.blog.csdn.net/20150616220653092?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveWVhc3k=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)





## What is a successful Git workflow?

When evaluating a workflow for your team, it's most important that you consider your team’s culture. You want the workflow to enhance the effectiveness of your team and not be a burden that limits productivity. Some things to consider when evaluating a Git workflow are:

- Does this workflow scale with team size?


- Is it easy to undo mistakes and errors with this workflow?
- Does this workflow impose any new unnecessary cognitive overhead to the team?

## four different workflows



- centralized workflow
- feature branch workflow
- Gitflow workflow
- forking Workflow

### Centralized Workflow

![git workflow | Central and local repositories](https://wac-cdn.atlassian.com/dam/jcr:0869c664-5bc1-4bf2-bef0-12f3814b3187/01.svg?cdnVersion=ht)

The Centralized Workflow is a great Git workflow for teams transitioning from SVN. Like Subversion, the Centralized Workflow uses a central repository to serve as the single point-of-entry for all changes to the project. Instead of `trunk`, the default development branch is called `master` and all changes are committed into this branch. This workflow doesn’t require any other branches besides `master`.



### Git Feature Branch Workflow

![img](http://nvie.com/img/git-model@2x.png)



The core idea behind the Feature Branch Workflow is that all feature development should take place in a dedicated branch instead of the `master` branch. This encapsulation makes it easy for multiple developers to work on a particular feature without disturbing the main codebase. It also means the `master` branch will never contain broken code, which is a huge advantage for continuous integration environments.



### Gitflow Workflow

![Git flow workflow - Historical Branches](https://www.atlassian.com/dam/jcr:2bef0bef-22bc-4485-94b9-a9422f70f11c/02%20(2).svg)



Gitflow Workflow is a Git workflow design that was first published and made popular by [Vincent Driessen at nvie](http://nvie.com/posts/a-successful-git-branching-model/). The Gitflow Workflow defines a strict branching model designed around the project release. This provides a robust framework for managing larger projects.

### Forking Workflow

![Git Fork Workflow - Making a pull request](https://www.atlassian.com/dam/jcr:0de71551-5c08-4fc4-ab6d-dc8a51bfcc5a/05.svg)



The Forking Workflow is fundamentally different than other popular Git workflows. Instead of using a single server-side repository to act as the “central” codebase, it gives every developer their own server-side repository. This means that each contributor has not one, but two Git repositories: a private local one and a public server-side one. The Forking Workflow is most often seen in public open source projects.



## How it work

Developers start by cloning the central repository. In their own local copies of the project, they edit files and commit changes as they would with SVN; however, these new commits are stored locally - they’re completely isolated from the central repository. This lets developers defer synchronizing upstream until they’re at a convenient break point.



### Workflow one



- Initialize the central repository

  ![Git Workflow: Initialize Central Bare Repository](https://www.atlassian.com/dam/jcr:f03a0fbd-a880-477f-aa32-33340383ce07/02%20(3).svg)

  `ssh user@host git init --bare /path/to/repo.git`

- Hosted central repositories

- Clone the central repository

  `git clone ssh://user@host/path/to/repo.git`

- Make changes and commit

  `git status # View the state of the repo
  git add <some-file> # Stage a file
  git commit # Commit a file</some-file>`

- Push new commits to central repository

  `git push origin master`

- Managing conflicts

  ![Git Workflows: Managing conflicts](https://www.atlassian.com/dam/jcr:d06191e3-994e-453a-8ea9-a2e93374e53e/03%20(4).svg)

  Before the developer can publish their feature, they need to fetch the updated central commits and rebase their changes on top of them. This is like saying, “I want to add my changes to what everyone else has already done.” The result is a perfectly linear history, just like in traditional SVN workflows.



### Workflow two

- Used to record the history of the branch

  ![img](http://img.blog.csdn.net/20131227204709984?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaGFwcHlkZWVy/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  ![img](http://img.blog.csdn.net/20131227204656906?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaGFwcHlkZWVy/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  ​

- Used for functional development of the branch

  ![img](http://img.blog.csdn.net/20131227204656906?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaGFwcHlkZWVy/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

- **Used to distribute the branch**

  ![img](http://img.blog.csdn.net/20131227204749484?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaGFwcHlkZWVy/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

- **The branch used for maintenance**

  ![img](http://img.blog.csdn.net/20131227204826703?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaGFwcHlkZWVy/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  ​

## Example 

- John works on his feature

  ![Git Workflows: Edit Stage Commit Feature Process](https://www.atlassian.com/dam/jcr:76bfc199-100a-4ef7-b9cf-86179ea5507c/06%20(2).svg)

  In his local repository, John can develop features using the standard Git commit process: edit, stage, and commit.

- Mary works on her feature

  ![Git Workflows: Edit Stage Commit Feature](https://www.atlassian.com/dam/jcr:a0aa8d1b-11a4-4aa4-a3a9-4f83f9be9a67/07.svg)

  Meanwhile, Mary is working on her own feature in her own local repository using the same edit/stage/commit process. Like John, she doesn’t care what’s going on in the central repository, and she *really* doesn’t care what John is doing in his local repository, since all local repositories are *private*.

- John publishes his feature

  ![Git Workflows: Publish Feature](https://www.atlassian.com/dam/jcr:6e5dc66d-b041-4013-b321-b1908fecfdbd/08.svg)

  Once John finishes his feature, he should publish his local commits to the central repository so other team members can access it. He can do this with the `git push` command, like so:

  `git push origin master`

- Mary tries to publish her feature

  ![Git Workflows: Push Command Error](https://www.atlassian.com/dam/jcr:52e2347e-b8e0-49ab-9530-5d1e9129198e/09.svg)

  Let’s see what happens if Mary tries to push her feature after John has successfully published his changes to the central repository. She can use the exact same push command:

  `git push origin master`

  `error: failed to push some refs to '/path/to/repo.git'hint: Updates were rejected because the tip of your current branch is behindhint: its remote counterpart. Merge the remote changes (e.g. 'git pull')hint: before pushing again.hint: See the 'Note about fast-forwards' in 'git push --help' for details.`

  ​

- Mary rebases on top of John’s commit(s)

  ![Git Workflows: Git Pull Rebase](https://www.atlassian.com/dam/jcr:25edd772-a30a-475a-a6ca-d1055ae61737/10.svg)

  Mary can use `git pull` to incorporate upstream changes into her repository. This command is sort of like `svn update`—it pulls the entire upstream commit history into Mary’s local repository and tries to integrate it with her local commits:

  `git pull --rebase origin master`

  ![Git workflows: Rebasing to Master](https://www.atlassian.com/dam/jcr:5165668f-b62d-4417-95e6-fde8ed97ec60/11.svg)

- Mary resolves a merge conflict

  ![Git Workflows: Rebasing on Commits](https://www.atlassian.com/dam/jcr:eaad29a3-6d94-4916-8a2c-3dea71aea4c2/12.svg)

  `CONFLICT (content): Merge conflict in <some-file>`

  ![Git workflows: Conflict Resolution](https://www.atlassian.com/dam/jcr:adf8c8e3-4287-4ec1-acf7-2a052d61d03f/13.svg)

  `git add <some-file>`

  `git rebase --continue`

  `git rebase --abort`

- Mary successfully publishes her feature

  ![Git Workflows: Synchronize Central Repo](https://www.atlassian.com/dam/jcr:de2dabdd-542f-4f64-9be4-870abff06f60/14.svg)

  ​

  After she’s done synchronizing with the central repository, Mary will be able to publish her changes successfully:

  `git push origin master`

- Where to go from here

  As you can see, it’s possible to replicate a traditional Subversion development environment using only a handful of Git commands. This is great for transitioning teams off of SVN, but it doesn’t leverage the distributed nature of Git.

## A simple process for us

Na generally open a new project, the beginning of the company's Organization is to build a repository, the program monkeys each fork to their own account under the fork after the end of it, it is necessary to terminal clone

- Take my own chestnut

  `git clone https://github.com/Franktian/ProjectName`

- This time you can check the remote

  `git remote -v`

- upstream

  `git add remote upstream https://github.com/OrganizationName/ProjectName`

- Update the develop branch

  `git pull upstream develop`

- Checkout a feature branch

  `git checkout -b feature-name`

- check which files are changed

  `git status`

- To see in the end changed a little Han

  `git diff`

- Visual are good, commit it

  `git commit -am "Hello Git"`

- Quickly put it on Github

  `git push origin feature-name`

- Update the code again to confirm the operation

  `git pull --rebase upstream develop`

- After being finished

  `git rebase continue`

- No problem, and then push again

  `git push orgin feature-name`

  ​