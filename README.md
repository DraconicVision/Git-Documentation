# Git Notes
**Note**:   Before using git ensure you have it installed. Install from *https://git-scm.com/*

***
## Git Init
**Source**: *https://youtu.be/fBNz5xF-Kx4?t=5217*

Before initialising any project first create a **README.md** file and a **.gitignore** file in the root directory of the project. 
You can put all the folder and file names in the .gitignore to ignore them when commiting. Remember, you must also create a repo
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
## Git Branching
**Source**: *https://www.youtube.com/watch?v=QG44fDn_PMc&list=PLnTRniWXnjf_abqo7qnrPsqo148VRYxjv&index=4*
**Note**:   Remember, **all code in the master branch should be functioning** and ready for production. Use other branches for
            developmental code.

Start by doing
> git branch

This displays the branches available locally in terminal. To create a new branch do 
> git branch <!--Git branch name here-->

Note if you are on the master branch it will create a copy of all the files in the master branch to the new branch you create by
entering the command above.

To switch branches do 
> git checkout <!--Desired branch name here-->

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

Before commiting anything I recommend you do
> git status 

This will tell you the branch you are on, which files are staged and which are untracked. **Ensure before commiting anything that you**
**have only the files you wish to commit staged**, use .gitignore to ignore any files you do not wish to commit. 

To stage all files in the local repo do 
> git add .

To stage a particular file you can do 
> git add <!--FileName-->.<!--FileExtension-->

To unstage or remove a file from a stage you can do 
> git rm --cached <!--FileName-->.<!--FileExtension-->

After staging anything through the **add** command I recommend you check the status by doing
> git status

This will allow you to check for all the staged files and ensure nothing you don't want to be commited is staged.

### Git Commit

To commit any changes after **carefully checking there are no unwanted files staged** you can do 
> git commit -m "<!--Enter Message Here-->"

-m Stands for message, in my opinion there is a better way of doing this by doing 
> git config --global core.editor "code --wait"

This will open the message file in VSCode in which you can type a message describing changes in a concise but descriptive manner. 
After changing the git global config all that's needed is 

> git commit

Which will open up the message in VSCode and you can enter the message. When you are done entering your message save with crtl + s 
and close the tab with ctrl + f4. Once the tab is closed the changes will be commited locally.

### Git Push

To upload your commited changes to Github you can do
> git push origin <!--Branch name here-->

***