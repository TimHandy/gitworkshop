forked from https://github.com/CodeHubOrg/gitworkshop
Cafe demo website: https://codehuborg.github.io/gitworkshop/

Notes: maybe do a beginner and intermediate set of scenarios, or give option to start off further down the scenarios.

# Git scenarios

You work for an agency specialising in creating and maintaining hospitality websites. Today you have been tasked with working on a Bristol Cafes and Pubs website build.

##1. Contributing to the cafes and pubs directory
You need to retrieve a copy of the repo for this project from the remote location  https://github.com/CodeHubOrg/gitworkshop and start working.
Below is the file structure of this repo. Let's try and add some cafes and pubs. Check out the branch *additional_pubs* Use the cafes/c_beatroot.html file as a template for a page about your cafe or pub. Also add it to index.html. Then you will somehow need to get the changes into the remote repo.

Answer: 
git clone or fork the above repo
git checkout pub_kensington_arms, 
make your changes, 
git add .
git commit -m "commit message"
if you cloned the repo originally rather than forking you will need to fork the original to your github, add the repo as a remote. 
Add the original as 'upstream', pull from upstream to merge any changes made by others, then push to your remote on github, before making a pull request to get the changes merged with the upstream original repo.
git push remote ??

![Project file structure](file_structure.jpg)

##2. Hotfix
Check out the branch *pub_kensington_arms*. Do some work on it, for example add a new pub file in the pub directory. use the pub template you'll find in the pub folder. While you are working away, you are told by your manager that you need to fix something on the *development* branch: You need to change the colour of the main title heading "Bristol Cafes and Pubs" to orange. How best to do that without losing your current changes? Make sure you stage and then commit your change, before returning back to *pub_kensington_arms to recover where you left off.

Answer: If you just change to the development branch, your changes will follow you, they won't remain on the current branch! WTF? weird hey! The quickest way to remedy this is to git stash -a I think it was??????, to stash all your changes away. Then git checkout development. Make the necessary change to the css file, then come back to the branch you were on. git stash list to show your stashes, and git stash pop to get back your latest stash.
https://git-scm.com/docs/git-stash

##3. I should have branched!
Check out the *development* branch and look at the recent commits. You realise that the last three commits should have rather gone on a new branch *new_header_styles* with the last commit in the *development* branch being "add paragraph under heading on homepage"

Answer: first create a new branch from where you're at right now: git branch new_header_styles. Now, making sure you're still on the development branch, git branch, you want to go back three commits. git reset --hard HEAD~3  ??? pretty sure it was this.

Rename that now latest commit "add paragraph under heading on homepage" to something nicer. git commit --amend

##4. Merging
You have completed the work on the *development* branch, and want to merge it into the pub_kensington_arms branch.

Answer: Make sure you are on the branch you want the changes to come over to: *Pub_kensington_arms*. Merge in the *development* branch. git merge development.

##5. Clear up that mess
Check out the *cafe_btp* branch and check the recent commits. Can this be tidied up a bit? i.e. keep all the changes, but remove some of the minor commits.

Answer: check commits first: git log --oneline.  git rebase -i HEAD~5.   This is *an* option. this will open rebase in interaction mode. You'll see the last 5 commits. change the word *pick* of each of the line to s to squash the commit, while leaving the one you want to squash them into as the letter p. Then save. Do a git log --oneline to see that the last 4 commit messages have gone. They have been squashed.


# Merging conflicts
You will likely come across conflicts. Check the file for the changes, remedy them, git add. and git commit them, then try pushing again.


