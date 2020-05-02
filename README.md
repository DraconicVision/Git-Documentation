# Git Notes
**Note**:   Before using git ensure you have it installed. Install from *https://git-scm.com/*

***
## Git Init
**Source**: *https://youtu.be/fBNz5xF-Kx4?t=5217*

Before initialising any project first create a **README.md** file and a **.gitignore** file in the root directory of the project. 
You can put all the folder and file names in the .gitignore to ignore them when committing. Remember, you must also create a repo
on the GitHub website if you wish to have it stored in the GitHub cloud.

To initialse a directory which **should be done every time you start a new project** you can do 
> git init

***
## Git Remote
**Source**: *https://help.github.com/en/github/using-git/adding-a-remote*

To check which remote URL you are using you can do 
> git remote -v

-v Stands for verbose, essentially it elaborates on the detail of the command. To add the remote origin you wish for you can do 
> git remote add origin <!--SSH URL to the repo here-->

***
## Git log

If you wish to check all the recent commits and merges simply do 
> git log

This will display your logs in terminal.
***
## Git Branching
**Source**: *https://www.youtube.com/watch?v=QG44fDn_PMc&list=PLnTRniWXnjf_abqo7qnrPsqo148VRYxjv&index=4*
            *https://www.educative.io/edpresso/how-to-delete-remote-branches-in-git*
            *http://www.codeblocq.com/2016/01/Untrack-files-already-added-to-git-repository-based-on-gitignore/*
**Note**:   Remember, **all code in the master branch should be functioning** and ready for production. Use other branches for
            developmental code.
            **Branch names are case sensitive**. I recommend you keep all your branches names lowercase.

Start by doing
> git branch

This displays the branches available locally in terminal. To create a new branch do 
> git branch <!--Git branch name here-->

Note if you are on the master branch it will create a copy of all the files in the master branch to the new branch you create by
entering the command above.

To switch branches do 
> git checkout <!--Desired branch name here-->

To both create a new branch and switch to that branch in one command do 
> git checkout -b <!--Git branch name here-->

To delete a branch you can do 
> git branch -d <!--Branch name you wish to delete here-->
***
## Git SSH
**Source**: *https://help.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh*
            *https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent*
            *https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account*
            *https://www.youtube.com/watch?v=hQ1W8wAoeZc&list=PLnTRniWXnjf_abqo7qnrPsqo148VRYxjv&index=2*

Ensure when on the help.github webpages you are getting instructions for the correct OS.

### Generating an SSH key
**Source**:  *https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent*

> ssh-keygen -t rsa -b 4096 -C "46660232+DraconicVision@users.noreply.github.com"
This generates a public and private SSH key in your users/[YourUserName]/.ssh directory on windows or your home directory on linux.
In this case I have used a private email but you can sub in the email you use for Github if you wish.

You will be asked for a passphrase next, I recommend you do not give a passphrase. Just hit enter.

### Adding an SSH key to GitHub
**Source**: *https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account*

**Note**:   When on linux ~ in a file path means its home which is a shortcut for /home/YourUserName
            When on linux / in a file path means its root
            Ensure your private SSH key is kept safe, only ever give out the public key.

If you are using the WSL terminal paste this into the terminal
> cat ~/.ssh/id_rsa.pub

This will display the public key in your terminal, from there you can copy and paste it to a throwaway notepad. From there you can 
go to your github webpage, go to settings > SSH and GPG keys > add new key and give your SSH key a title. I recommend using the name
of your PC (Ex: Work PC, Home desktop, etc.) and the OS you are using on it. If you are using multiple VMs on a PC the SSH key will 
differ from OS to OS. After you have given it a title paste the key into the input and add the key.

***
## Git clone

This will download the repo you wish to your local PC.
> git clone <!--Paste the SSH of the repo here, no quotes or syntax-->

***
## Git Commit, Add & Push
**Source**: *https://www.youtube.com/watch?v=nquxBcx929o&list=PLnTRniWXnjf_abqo7qnrPsqo148VRYxjv&index=3*

### Git Staging & Status
**Source**: *http://www.codeblocq.com/2016/01/Untrack-files-already-added-to-git-repository-based-on-gitignore/*

Before committing anything I recommend you do
> git status 

This will tell you the branch you are on, which files are staged and which are untracked. **Ensure before committing anything that you**
**have only the files you wish to commit staged**, use .gitignore to ignore any files you do not wish to commit. 

To stage all files in the local repo do 
> git add .

To stage a particular file you can do 
> git add <!--FileName-->.<!--FileExtension-->

To unstage or remove a file from a stage you can do 
> git rm --cached <!--FileName-->.<!--FileExtension-->

To unstage or remove all files from the stage you can do 
> git rm -r cached .

The RM means remove, -r allows the recursive model and . means all. 

After staging anything through the **add** command I recommend you check the status by doing
> git status

This will allow you to check for all the staged files and ensure nothing you don't want to be committed is staged.

### Git Commit

To commit any changes after **carefully checking there are no unwanted files staged** you can do 
> git commit -m "<!--Enter Message Here-->"

-m Stands for message, in my opinion there is a better way of doing this by doing 
> git config --global core.editor "code --wait"

This will open the message file in VSCode in which you can type a message describing changes in a concise but descriptive manner. 
After changing the git global config all that's needed is 

> git commit

Which will open up the message in VSCode and you can enter the message. When you are done entering your message save with CTRL + S 
and close the tab with CTRL + F4. Once the tab is closed the changes will be committed locally.

### Git Push

To upload your committed changes to Github you can do
> git push origin <!--Branch name here-->

To reduce the amount of writing you have to do per every time you git push I recommend you do
> git push --set-upstream origin <!--Branch name here-->

From then on all you will have to do is 
> git push

To push to the upstream branch you have chosen.

***
## Git Merging
**Source**: *https://nvie.com/posts/a-successful-git-branching-model/*
            *https://www.atlassian.com/git/tutorials/using-branches/git-merge*
            *https://www.youtube.com/watch?v=icUggPL4qpY&list=PLnTRniWXnjf_abqo7qnrPsqo148VRYxjv&index=5*

Merging two branches is combining the commit history of both branches into one unified branch. To merge one branch with another do
> git merge --no-ff <!--Branch name here-->

A merge message will come up, you can enter a descriptive merge message if you wish. I highly recommend you use --no-ff (no fast
forward) as that allows much more structure in version history.

It's possible to get a conflict while merging, ensure that any conflicts are carefully looked over and decide which versions of the code
you do and do not want. You can have both, none or just one.

***
## Undoing Changes & Reverting Commits

### Git Reset
**Source**: *https://www.youtube.com/watch?v=g8UgXgqEJXs&list=PLnTRniWXnjf_abqo7qnrPsqo148VRYxjv&index=6*

If for some reason you want to delete all the code you have modified since your last commit it is possible to do that using
> git reset --hard

This will actually delete all of the code made since the last commit, I do not recommend doing this. You have been warned.

More likely you may want to revert a commit but not actually delete all of the code, this can be done by doing
> git reset --soft HEAD~1

What this does is it reverts the last commit to the staging phase and does not remove any code. The HEAD bit of the command means that it
reverts from the current head which is the branch you are on currently. If you do 
> git status

You should see the files you modified are staged but not yet committed.

### Removing a Pushed Commit from your Repository
**Source** *https://www.youtube.com/watch?v=g8UgXgqEJXs&list=PLnTRniWXnjf_abqo7qnrPsqo148VRYxjv&index=6*

Right, you messed up. Bad. It happens, generally if you push some buggy code to the master there is no need to remove it you can just add another commit
which removes the buggy code and that's fine. The issue with this though is that there is still evidence of the previous buggy commit and people can view that 
buggy code. Worse again if there is sensitive information in the pushed commit people can still view that no matter how many more commits you add to the branch.
First off, you're an idiot. **Be very careful about pushing anything**. Second, don't freak out. This can be fixed providing you catch yourself before you make 
another commit.

After you push a commit you wish to revert do
> git reset --soft HEAD~1

This will take you back one commit but it will still keep your changes. You can then delete (or add to the .gitignore list) the files you do not want or delete the
lines of code you don't want on your remote repository. You can then do 

> git status

Check the files in which you have modified, ensure you have removed any sensitive information you don't want pushed. Then do 
> git add .
> git status

You will then see that in the terminal there have been no perceived changes. This is because you are sort of one commit behind, at least locally. After the sensitive
information has been removed you can do 
> git push -f origin <!--Branch Name-->

-f Stands for force, this is forcing the origin to get rid of the previous commit (the one you wanted removed.)

**Note**, you can also do this with git reset --hard HEAD~1 in place of git reset --soft HEAD~1 if you want, this will auto delete all the code since the last commit so it
can be a bit quicker but can also lead to losing code. I recommend using git reset --soft HEAD~1 . 

### Git Checkout
**Source**: *https://www.youtube.com/watch?v=g8UgXgqEJXs&list=PLnTRniWXnjf_abqo7qnrPsqo148VRYxjv&index=6*

If you have modified a file since your last commit and you only want to undo the modifications to that file rather than resetting the entire
branch you can first do 
> git status

Check that you have not committed or staged the file you want to revert to the state it was in at the last commit and do 
> git checkout <!--FileName-->.<!--FileExtension-->

For example you could do 
> git checkout index.html

To just revert index.html and nothing else. I recommend this over git reset --hard in almost all situations.

***
## Git Stash
**Source**: *https://www.youtube.com/watch?v=-QKlyw_Q2uw&list=PLnTRniWXnjf_abqo7qnrPsqo148VRYxjv&index=7*
**Note**:   Your stash is stored within .git/refs/ with a file simply titled "stash." Since it is stored within your .git folder on your local repository it will not be pushed
            to your remote repository.

            I generally do not recommend git stash as if you are using multiple branches correctly (see Nvie article linked aside Git branching) it's generally not needed in most
            cases although some users seem to love it, I'll leave its usage up to you.

In the event you are working on something and you have to direct your attention to another part of the project before you could finish the work you are already working on git
stash can be useful. To stash your changes since your last commit do 
> git add .
> git status
> git stash

Remember to check that you haven't staged anything you don't want to stash. Once you have stashed the desired modifications you can do
> git stash list

To check what's in your stash. It will display the branch the stash is in and at which commit it was stashed at. When you are ready to reapply the changes in your stash you can do
> git stash apply stash@{0}

This will reapply the changes which are stored inside that stash. This will not delete the saved changes within the stash but if you want to reapply the changes within the stash 
and delete the last changes in the stash you can simply do 
> git stash pop

To clear your stash you can simply do 
> git stash clear

***
## .gitignore
**Source**: *https://www.youtube.com/watch?v=h-1EBRYBUwA&list=PLnTRniWXnjf_abqo7qnrPsqo148VRYxjv&index=8*
            *https://github.com/github/gitignore*

There is a lot that you can do with .gitignore and you can ignore all manner of particulars with it but for this documentation I'm going to keep it simple. Ensure when creating a 
.gitignore file it is called **simply .gitignore with no file extension**. When creating a .gitignore file I highly recommend you make one and only the one in the root of your
repository directory. You can make more .gitignore files in folders within the directory which will only affect those folders but for the sake of your sanity and the sanity of
anyone collaborating with you I highly recommend you stick to my initial suggestion. All rules within .gitignore must be separated with a line. Ex:
> *.example
> example.js
> ExampleFolder/

**Not**:
> *.example example.js ExampleFolder/

To create a comment in a .gitignore file add a # at the start of the line.
To ignore a file within .gitignore simply add the file name and extension into a line in the .gitignore file such as 
> example.js

To ignore all files with a particular file extension simply add 
> *.ExampleFileExtension

To ignore all files within a folder thats in the root directory simply add
> ExampleFolder/

To exempt an item or items from your .gitignore pattern you can add a ! in front of the the line, Ex:
> !example.html
> !*.ExampleFileExtension
> !ExampleFolder/

To start ignoring a file you have already committed you must remove the file from your local repo, commit that you have removed the file, add the rule in .gitignore to ignore the 
desired file and then add the file back, once you have added the file back it should be ignored in accordance with your .gitignore rules.
***