# *Dipterygonotus balteatus*

The purpose of the repository is to share code for the analysis of genomic data for a fish species in the family Caesionidae, *Dipterygonotus balteatus*.  This will allow for replication of resuts, collaboration among mentors and lab mates to improve the analysis pipeline, and for use in instruction.

All work done is for the [Philippines PIRE Project](https://sites.wp.odu.edu/PIRE/), [NSF Award #1743711](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1743711).

![](https://github.com/Getterrobog/DipterygonotusBalteatus/blob/main/PPP_logo.png)

All data analysis will be done by interfacing with the Old Dominion University High Performance Computing Wahab cluster, either through a remote connection on MS Remote Desktop or via Terminal on Mac OS.

This README is written in [Markdown](https://www.markdownguide.org/basic-syntax/#links).

`font` indicates a command line command

> Blockquotes indicate input made into the command line on a terminal window.

```sh
This block quote indicates input made into R or Python as specified in the heading.
```

Feel free to use what you can from this repository.  If you do so please give credit to Ivan R. Lopez, Old Dominion University.

***

## GitHub

I understand the importance of version control in a project such as this and appreciate the advantages GitHub offers.  If you are not familiar with GitHub or command line I recommend becoming familiar with this information at [Software Carpentry](https://software-carpentry.org/lessons/).

Because I can never remember the proper order of the git commands I created the following script to automated pushing to this repository.
On command line I typed:

> nano Gitpushinator.sh

(I watch too many cartoons.)
I then typed the following:

>#!/bin/bash -l\
>\
>git add * #* is a variable that will add all tracked files in this directory to the Git repository\
>git commit -m "$1" #the second argument will be your commit\
>git push -u origin main\

I saved this script to my scripts directory and gave it permission to execute.

> chmod u+x Gitpushinator.sh

On terminal I type `cd` into the directory I want to update and run the script as follows:

> Gitpushinator.sh 'A DESCRITION OF MY COMMIT'

***

I tried to make a GitHub webpage for this repository using instructions published by a colaborator.  However, I broke my local repository following that guide to make a git website.  Refusing to learn anything, I deleted the local repository and made the following changes:

> git clone https://github.com/Getterrobog/DipterygonutusBalteatus.git

This seemed to repair the disconnect that occurred. I had to delete and renter the alias for this repository on my .zshrc script.  I used the instructions provided at [GitHub docs](https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll)

I have Ruby and Bundler installed.  If you do not have Ruby, Bundler or Jekyll intalled follow the installation instructions for [Jekyll](https://jekyllrb.com/docs/installation/macos/) 

I then executed the following on the command line:

>cd MY_PATHWAY/DipterygonutusBalteatus

Step 3 of the guide asks to initialize the git repository, but since I'd previously cloned the repository, this step is not necessary.

>mkdir docs
>cd docs
>gem install --user-install jekyll
>git checkout --orphan gh-pages
>jekyll new .

With BBedit, I opened the file named Gemfile (no extension).
I commented out line 10 which read: gem "jekyll", "\~\> 4.2.0"
I changed line 15 from # gem "github-pages", group: :jekyll_plugins to:
gem "github-pages", "\~> 212", group: :jekyll_plugins
I looked up the latest version per the GitHub instructions
I saved and closed Gemfile

>bundle update
> cd ../

I took a break at this point.  After pushing changes git declared there was nothing to commit.  I did not understand what I had done.

***

Still working on Jekyll.  I noticed my main was not accepting commits or pushes from the local repository.  After searching the web for solutions and reinitializing the repository, nothing worked.  I will preserve this file, delete the local and web repositories and start over.

>cd Desktop/Daily_Work
>mkdir DipterygonotusBalteatus
> cd DipterygonotusBalteatus
>git init
>Initialized empty Git repository in /Users/ivanlopez/Desktop/Daily_Work/.git/
>git add README.MD
>git add PPP_logo.png
>git status
>On branch master
>
>No commits yet
>
>Changes to be committed:
>  (use "git rm --cached <file>..." to unstage)
>
>	new file:   PPP_logo.png
>	new file:   README.MD
>git commit -m "Restarting repository"
>git branch -M main
>git remote add origin https://github.com/Getterrobog/DipterygonotusBalteatus.git
>git push -u origin main
>mkdir docs
>cd docs
>gem install --user-install jekyll
>git checkout --orphan gh-pages
>jekyll new .

Again with BBedit, I opened the file named Gemfile (no extension).
I commented out line 10 which read: gem "jekyll", "\~\> 4.2.0"
I changed line 15 from # gem "github-pages", group: :jekyll_plugins to:
gem "github-pages", "\~\> 212", group: :jekyll_plugins
I looked up the latest version per the GitHub instructions
I saved and closed Gemfile.
I skipped step 12

I ran this step and got an error

>gem update github-pages

This log did not get pushed as updated.  Trying again

>git branch -M main

I stopped for the day

***

After running Gitpushinator.sh I received the following error:
On branch main
Your branch and 'origin/main' have diverged,
and have 1 and 1 different commits each, respectively.
  (use "git pull" to merge the remote branch into yours)

>git push -u origin main
>To https://github.com/Getterrobog/DipterygonotusBalteatus.git
> ! [rejected]        main -> main (non-fast-forward)
>error: failed to push some refs to >'https://github.com/Getterrobog/DipterygonotusBalteatus.git'
>hint: Updates were rejected because the tip of your current branch is behind
>hint: its remote counterpart. Integrate the remote changes (e.g.
>hint: 'git pull ...') before pushing again.
>hint: See the 'Note about fast-forwards' in 'git push --help' for details.
>git pull
>fatal: refusing to merge unrelated histories
>git pull --rebase
>git add README.MD 
>git rebase --continue
>Gitpushinator.sh 'rebasing'

That seemed to do it.  Of course I had to do what I refused to do before, which was to research the problem and learn.

 