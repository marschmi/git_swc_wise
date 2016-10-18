# Introductory Version Control with Git
Marian L. Schmidt, @micro_marian, marschmi@umich.edu  
October 18th, 2016  

***
> **Warm up discussion:**  
> 1. How do you currently keep track of versions of the same document?  
> 2. When working with a collaborator simultaneously, how do you keep track of versions of the same document?

***

# Before We Start 
The main page for the core lessons from the Software Carpentry Foundation can be found at <a href="http://software-carpentry.org/lessons/" target="_blank">http://software-carpentry.org/lessons/</a>  

The lesson here is based on Software Carpentry's core curriculum on git entitled **"Version Control with Git"** and is maintained by Ivan Gonzalez and Daisie Huang.  

The main lesson link can be found at <a href="http://swcarpentry.github.io//git-novice/" target="_blank">http://swcarpentry.github.io//git-novice/</a>   


  
# The scenario  
You are working on a project with your collaborator and have a deadline for a paper quickly approaching.  To get the paper where it needs to be for publication you and your collaborator must work on the document simultaneously. You're quickly passing documents back and forth and trying to keep up with each other to meet the deadline.  In the midst of all of the changes to the document, something is lost.  Which version of the document was it in?  
  
In this moment you are reminded of a time when you attended a Software Carpentry Workshop in January 2016.  It was a busy time during the workshop and getting ready for the semester.  However, there was one thing you remember that you learned **version control is better than mailing files back and forth.**

But why?
  
## Some Key Words
  
### Version Control

*Version control* is a tool for managing changes to a set of files. Each set of changes creates a new *commit* of the files; the version control system allows users to recover old *commits* reliably, and helps manage conflicting changes made by different users.

### Commit

A *commit* records the current state of a set of files (a group of changes) in a *version control repository*. As a noun, the result of commiting, i.e. a recorded group of changes in a repository. If a *commit* contains changes to multiple files, all of the changes are recorded together.
 

### Version Control Repository

A *version control repository* is a storage area where a version control system stores the full history of commits of a project and information about who changed what, when.  

### Merge  

Multiple versions of a document can be *merged* into one.  


# Why version control?

1. **Nothing that is committed to version control is ever lost.** Since all old versions of files are saved, it’s always possible to go back in time to see exactly who wrote what on a particular day, or what version of a program was used to generate a particular set of results.  
2. As we have this record of who made what changes when, **we know who to ask if we have questions later on**, and, if needed it, **revert to a previous version,** much like the “undo” feature in an editor.  
3. When several people collaborate in the same project, it’s possible to accidentally overlook or overwrite someone’s changes: **the version control system automatically notifies users whenever there’s a conflict between one person’s work and another’s.**

Teams are not the only ones to benefit from version control: lone researchers can benefit immensely. Keeping a record of what was changed, when, and why is extremely useful for all researchers if they ever need to come back to the project later on (e.g., a year later, when memory has faded).  

**Do you want to be your own friend in a year?**

Version control is the lab notebook of the digital world: it’s what professionals use to keep track of what they’ve done and to collaborate with other people. Every large software development project relies on it, and most programmers use it for their small jobs as well. And it isn’t just for software: books, papers, small data sets, and anything that changes over time or needs to be shared can and should be stored in a version control system


Examples from my own research: <a href="https://github.com/marschmi" target="_blank">https://github.com/marschmi</a>  

- A <a href="https://twitter.com/micro_marian/status/674294091300134912" target="_blank">victory tweet</a> from my first dissertation chapter. 


> Go to the original Software Carpentry lesson on **automated version control**: <a href="http://swcarpentry.github.io/git-novice/01-basics/" target="_blank">http://swcarpentry.github.io/git-novice/01-basics/</a>  


# Remembering the Unix Shell

**A note on the shell and why it is important:**  It's like the air traffic control tower - allowing airlines from all over the globe to work together to get people around.  In this case, bash is directly talking to your computer through unix shell commands to run many programs.  If you need to run multiple programs at once an efficient way to do it automatically is to use the shell.  Here we will the shell to simultaneously run nano, git, unix, and R!  

# Configuring Git  

> **Open up your bash shell, what happens when you run:**  
> 1. `git config --list`  
> 2. `git config`

> Now, let's set up Git by going to <a href="http://swcarpentry.github.io/git-novice/02-setup/" target="_blank">http://swcarpentry.github.io/git-novice/02-setup/</a>



# Create a Local Repository

**Learning Goals**  

- What is a **local** repository?  
- Create a local Git repository.  
- Check the status of a repository.


A **local** repository means that we are creating respository on our own computer.  Our computer is local - It especially likes attending the weekly farmers market and supporting local businesses.  

> 1. In bash, navigate to **`Desktop -> SWC -> SWC_R`** folder from the morning's R lesson.  
> 2. In the **`SWC_R`** folder, type `ls -a`.  Remeber, the `-a` flag shows us the hidden items within the directory.  
> 3. What files do you see?
> 4. Now, **initialize the repository** by typing `git init`.  
> 5. What files do you see now that **`SWC_R`** is now a repository under version control?  
> 6. To check that everything is set up correctly by asking Git to tell us the status of our project, type `git status`.


# Tracking Changes  

**Learning Goals**  

- Go through the modify-add-commit cycle for single and multiple files.  
- Explain where information is stored at each stage of Git commit workflow.


> Let's look at `variables.R` by typing `cat variables.R` into the shell.  What happens?  What command does this remind your of?  
> `git status`


> 1. Open up the `variables.R` file with nano or notepad.  
> 2. Make a commented header to the file.  For example, `# This is the document where I learn introductory R.`  
> 3. Save the changes.  
> 4. `git status`  
> 5. So far the changes are "untracked" with git.  Now we need to tell git to keep track of the changes we have made - in other words, it's time for the first commit!  
> 6. `git add variables.R`  
> 7. `git status`  
> 8. What happened?  

Git now knows that it’s supposed to keep track of `variables.R`, but it hasn’t recorded these changes as a commit yet. To get it to do that, we need to run one more command:

> 9. `git commit -m "Adding commented header"`  


When we run `git commit`, Git takes everything we have told it to save by using `git add` and stores a copy permanently inside the special **.git** directory. This permanent copy is called a commit (or revision) and its short identifier is `f22b25e` (Your commit may have another unique identifier.)

We use the `-m` flag (for “message”) to record a short, descriptive, and specific comment that will help us remember later on what we did and why. If we just run git commit without the `-m` option, Git will launch nano (or whatever other editor we configured as core.editor) so that we can write a longer message.

Good commit messages start with a brief (<50 characters) summary of changes made in the commit. If you want to go into more detail, add a blank line between the summary line and your additional notes.

If we run git status now:

> 10. `git status`  

it tells us everything is up to date. If we want to know what we’ve done recently, we can ask Git to show us the project’s history using `git log`:  

> 11. `git log`  

`git log` lists all commits made to a repository in reverse chronological order. The listing for each commit includes the commit’s full identifier (which starts with the same characters as the short identifier printed by the git commit command earlier), the commit’s author, when it was created, and the log message Git was given when the commit was created.


**Where Are My Changes?**  If we run `ls` at this point, we will still see just one file called `variables.R`. That’s because Git saves information about files’ history in the special `.git` directory mentioned earlier so that our filesystem doesn’t become cluttered (and so that we can’t accidentally edit or delete an old version).

Now let's adds more information to the file. (Again, we’ll edit with nano and then cat the file to show its contents; you may use a different editor, and don’t need to cat.)  

> 12. Using nano/notepad, comment some more of the code in `variables.R` and save the file.  
> 13. `cat variables.R` to see the changes.  
> 14. Now run `git status`.  

The last line is the key phrase: `“no changes added to commit”.` We have changed this file, but we haven’t told Git we will want to save those changes (which we do with git add) nor have we saved them (which we do with git commit). So let’s do that now. It is good practice to always review our changes before saving them. We do this using `git diff`. This shows us the differences between the current state of the file and the most recently saved version:

> 15. `git diff`  

The output is cryptic because it is actually a series of commands for tools like editors and patch telling them how to reconstruct one file given the other. If we break it down into pieces:

1. The first line tells us that Git is producing output similar to the Unix diff command comparing the old and new versions of the file.  

2. The second line tells exactly which versions of the file Git is comparing; df0654a and 315bf3a are unique computer-generated labels for those versions.  

3. The third and fourth lines once again show the name of the file being changed.  

4. The remaining lines are the most interesting, they show us the actual differences and the lines on which they occur. In particular, the + markers in the first column show where we have added lines.  

After reviewing our change, it’s time to commit it:  

> 16. `git commit -m "Added comment on ______"`  
> 17. `git status`  

Whoops: Git won’t commit because we didn’t use `git add first`. Let’s fix that:

> 18. `git add variables.R`  
> 19. `git commit -m "Added comment on ______"`  
> 20. `git status`  

Git insists that we add files to the set we want to commit before actually committing anything because we may not want to commit everything at once. For example, suppose we’re adding a few citations to our supervisor’s work to our thesis. We might want to commit those additions, and the corresponding addition to the bibliography, but not commit the work we’re doing on the conclusion (which we haven’t finished yet).

To allow for this, Git has a special **staging area** where it keeps track of things that have been added to the current change set but not yet committed.

## **The Staging area**  
If you think of Git as taking snapshots of changes over the life of a project:  

- `git add` specifies what will go in a snapshot (putting things in the staging area), and  
- `git commit` then actually takes the snapshot, and makes a permanent record of it (as a commit).  

If you don’t have anything staged when you type `git commit`, Git will prompt you to use `git commit -a` or `git commit --all`, which is kind of like gathering everyone for the picture! However, it’s almost always better to explicitly add things to the staging area, because you might commit changes you forgot you made. (Going back to snapshots, you might get the extra with incomplete makeup walking on the stage for the snapshot because you used `-a`!) Try to stage things manually, or you might find yourself searching for `git undo commit` more than you would like!

![](Images/staging_area.png)


Let’s watch as our changes to a file move from our editor to the staging area and into long-term storage.

> 21.  Add `dist10 <- rnorm(10)` for a random normal distribution of 10 numbers at the bottom of the `variables.R` file.  
> 22. `git diff`

So far, so good: we’ve added one line to the end of the file (shown with a + in the first column). Now let’s put that change in the staging area and see what `git diff` reports:

> 23. `git add variables.R`  
> 24. `git diff`  

There is no output: as far as Git can tell, there’s no difference between what it’s been asked to save permanently and what’s currently in the directory. However, if we do this:

> 25. `git diff --staged`

it shows us the difference between the last committed change and what’s in the staging area. Let’s save our changes:

> 26. `git commit -m "Created dist10, a random normal distribution of 10 numbers."`  

Check the status: 

> 27. `git status`

and look at the history of what we’ve done so far:  

> 28. `git log`  

To recap, when we want to add changes to our repository, we first need to add the changed files to the staging area (git add) and then commit the staged changes to the repository (git commit):  

![](Images/git_workflow.png)


> **Challege Question 1:  Choosing a Commit Message**  
Which of the following commit messages would be most appropriate for the last commit made to mars.txt?

```
1. “Changes”
2. “Added line ‘But the Mummy will appreciate the lack of humidity’ to mars.txt”
3. “Discuss effects of Mars’ climate on the Mummy”
```


> **Challege Question 2:  Committing Changes to Git**  
> Which command(s) below would save the changes of myfile.txt to my local Git repository?

```
1.  $ git commit -m "my recent changes"
2.  $ git init myfile.txt
    $ git commit -m "my recent changes"

3.  $ git add myfile.txt
    $ git commit -m "my recent changes"

4.  $ git commit -m myfile.txt "my recent changes"
```

> **Challenge 3:  Create a project description**  
> Create a new file called README.txt. Write a three-line description of the swc_r repository, commit your changes, then:

> - modify one line
> - add a line
> - and display the differences between its updated state and its original state.


# Remote Repositories on GitHub  

**Learning Goals**  

- Explain what **remote** repositories are and why they are useful.  
- Clone a remote repository.  
- Push to or pull from a remote repository.  


Version control really comes into its own when we begin to collaborate with other people. We already have most of the machinery we need to do this; the only thing missing is to copy changes from one repository to another.

Systems like Git allow us to move work between any two repositories. In practice, though, it’s easiest to use one copy as a central hub, and to keep it on the web rather than on someone’s laptop. Most programmers use hosting services like GitHub, BitBucket or GitLab.

Let’s start by sharing the changes we’ve made to our current project with the world.  

> 1. Log in to GitHub.  
> 2. Click on "Repositories", and then click on the ![](Images/new.png) icon in the top right corner to create a new repository called `SWC_R`:  

![](Images/remote_repo.png)

As soon as the repository is created, GitHub displays a page with a URL and some information on how to configure your local repository:

![](Images/remote_created.png)

This effectively does the following on GitHub’s servers:

`mkdir SWC_R`  
`cd SWC_R`  
`git init`


Our local repository still contains our earlier work on variables.R, but the remote repository on GitHub doesn’t contain any files yet:

![](Images/local_vs_remote.png)


The next step is to connect the two repositories. We do this by making the GitHub repository a remote for the local repository. The home page of the repository on GitHub includes the string we need to identify it:

![](Images/mergeSSH.png)  

> 4. Click on the ‘HTTPS’ link to change the protocol from SSH to HTTPS.



> **HTTPS vs SSH**  
> We use HTTPS here because it does not require additional configuration. After the workshop you may want to set up SSH access, which is a bit more secure, by following the great tutorial from <a href="https://help.github.com/articles/generating-ssh-keys/" target="_blank">GitHub</a>.


![](Images/mergeHTML.png)  


> 5. Copy that **HTTPS** URL from the browser, go into the local `SWC_R` repository.  
> 6. Run this command: `git remote add origin https://github.com/marschmi/SWC_R.git`  

Make sure to use the URL for your repository rather than marschmi’s.

We can check that the command has worked by running `git remote -v:`

> 7. `git remote -v`  

The name `origin` is a local nickname for your remote repository: we could use something else if we wanted to, but `origin` is by far the most common choice.

Once the nickname `origin` is set up, this command will push the changes from our local repository to the repository on GitHub:

> 8. `git push origin master`

***  

**Proxy**  
If the network you are connected to uses a proxy there is an chance that your last command failed with “Could not resolve hostname” as the error message. To solve this issue you need to tell Git about the proxy:

`git config --global http.proxy http://user:password@proxy.url`  
`git config --global https.proxy http://user:password@proxy.url`  

When you connect to another network that doesn’t use a proxy you will need to tell Git to disable the proxy using:

`git config --global --unset http.proxy`  
`git config --global --unset https.proxy`  

**Password Managers**  
If your operating system has a password manager configured, git push will try to use it when it needs your username and password. If you want to type your username and password at the terminal instead of using a password manager, type:

`unset SSH_ASKPASS`  

You may want to add this command at the end of your ~/.bashrc to make it the default behavior.

***

Our local and remote repositories are now in this state:

![](Images/current_repo.png) 


We can pull changes from the remote repository to the local one as well:

> 9. `git pull origin master`

Pulling has no effect in this case because the two repositories are already synchronized. If someone else had pushed some changes to the repository on GitHub, though, this command would download them to our local repository.


> **Challenge 1:  Remote vs Local Repositories**  
> 1. Define **remote** repository.  
> 2. Define **local** repository.  
> 3. What is the difference between remote and local repositories*?  


> **Challenge 2:  `git push` vs `git pull`**  
> 1. What happened when you performed `git push`?  
> 2. What happened when you ran `git pull`?  
> 3. How are `git push` and `git pull` different?

> **Challenge 3:  Github Timestamp**  
> Create a repository on GitHub, clone it, add a file, push those changes to GitHub, and then look at the <a href="http://swcarpentry.github.io//git-novice/reference.html#timestamp" target="_blank">timestamp</a> of the change on GitHub. How does GitHub record times, and why?



# Remember 2 things:  
> 1. **Version control is better than mailing files back and forth!  (It is also better than dropbox.)**  
> 2. **Do you want to be your (or advisor's/collaborator's) friend in 6 months?  A year? 2 years?**

# Key Words
A helpful resource describing version control with git basics from Software Carpentry <a href="http://swcarpentry.github.io//git-novice/reference.html#version-control" target="_blank">can be found here.</a>  

- **Version Control**  
- **Repository**  
  - **Local** vs **Remote**
- **Commit**  
- **Merge**  
- `git config`  
- `git status`  
- `git add`  
- `git commit`  
- `git log`  
- `git diff`  
- `git push`  
- `git pull`  









