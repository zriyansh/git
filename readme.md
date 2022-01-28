# git


==================================================================================
			            	'GIT BASH COMMANDS '
			Git is a Distributed graph theory tree model.
==================================================================================

*. To save your password with github permanently
make a file .netrc in home/<username>
add the following and then save. 

machine github.com
login <login_github>
password <password_github>
______________________________________________________________


1. notepad file.ext - to open that file(eg .js or .html file)
__________________________________________________________________________________________________________________________________________


2. Rename file In GIT
>git mv iphone.css mobile.css
change contents from iphone.css to mobile.css
>git commit -m 'Rename folder.' 
__________________________________________________________________________________________________________________________________


3. CLONE
>git clone <url> <folder where to clone it>

>git clone --shallow
if the repository is very big, this command avoids to download commits made earlier in that project.
________________________________________________________________________________________________________________________________________


4. CONFIGURATION
to setup name and email,

>git config
to show all things which can be done using this command
{ config .gitconfig file to make it behave your way, search internet}  

>git config --global user.name "Priyansh Khodiyar"

>git config --global user.email "<email here>"

>git config --gloabl --list
shows our name and email.
a text file is created which has these then type

> cat ~/.gitconfig
here it will show the name and email
_____________________________________________________________________


5. BASIC COMMANDS
>ls -a 
shows all the hidden folders
 
>git init git-demo
git initialized only in git-demo folder

README.md - md stands for mark down. 
>clear
to clear the console.
_____________________________________________________________________


9. ADD AND COMMIT AT THE SAME TIME
>git commit -am 
(a for ADD and m for MSG)
add and commmit in one step of only the MODIFIED file not the newly created files.  

{There must be an interface to work with these}
suppose you made 2 changes to a file and you want to add only one of them
>git add -p <filename>
this will show [ y/n ] to add/ not add the changes made for every single changes,

>git diff --catched
shows which changes are staged for commit

>git checkout <filename >
to throw out the unwanted changes which should not be added.  
_____________________________________________________________________


10. REVERT BACK 
after we modified a file and added it to commit stage, if we
want to revert back, do 

>git reset HEAD <fileName>.
now its again in the modified stage, if we further want to revert those changes 
that we did in a file, do 

>git checkout -- <fileName.ext> 
this is make it like how it was before modifying.
_____________________________________________________________________


11. LOGS 
>git log - all commits shown here. 
but this much info may be too much so type 

>git help log 
to get options to log 

>git log --oneline --graph --decorate --color --oneline
gives a compact view of logs.
_____________________________________________________________________


12. REMOVING FILES
>git rm <fileName>
to remove a file, but still removal needs to be
commited, so a final commit to remove files. 

ANOTHER WAY : 
>rm <fileName.ext>
removes file without gits info and its there in the commit zone 
but can't be commited as it can't be added the do.

>git add -u 
to stage it for commit and then commit.
_____________________________________________________________________


13. MOVING FILES
(between folders)
>git mv <fileName.ext> <folderName>
moving from a file in master to a folder in master.
the commit these rename changes.
_____________________________________________________________________


14. IGNORING FILES
like we dont want to push .log files so ignore them
make a .gitignore file using 

>notepad .gitignore
and inside this file type 
*.log
this prevents any .log extension files to get added or commited.
_____________________________________________________________________


 15. SSH key Authentication 
>cd ~ 
to get back to home/ root directory now type 

>cd .ssh ->to see if the .ssh key exist or not, if not then

>mkdir .ssh 
>cd .ssh/
>ssh-keygen -t rsa -C "<email>"

then it will generate id_rsa and id_rsa.pub, we'll use .pub file with github.
SSH keys are tied to the computer. Copy the contents of .pub file and paste it in github settings.

After successful authentication, type
>ssh -T git@github.com
to get a success msg.
return to home dir cd ~
_____________________________________________________________________


16. COLLABORATE WITH OTHERS(PULL REQUESTS)
create a new repository in github.
set everything as default and create. 

then click on "SSH" where [ HTTP | SSH ] option is present. 
then do push from existing repo cmd line i.e

NOTE : remote means making a channel for other people to have connections with our files. 
can be connected to other folders of our system as well, 
eg
>git remote add origin ../<folder name where the remote will be setup for this repository>


note: you must be inside the git initiated folder to perform the following code below.
>git remote add origin git@github.com <username>/<repoName.git>
>git remote -v

then 
SYNTAX : 
>git push <remote> <local branch> : <remote branch> *(where it will be added)

>git push -u origin master  
-u is done for the first time use to make a "uplink"
now our local folder repo is pushed to github

(now locally we can modify the files, add and commit and then if we check
the status then it will show which branch is ahead by commits as we re in sync with github(using SSH))  

now do 
>git status 
to see which all braches have a remote refernce to my brances

>git remote remove origin 
to remove set remotes

_____________________________________________________________________
NOTE :  If during creating a new repo we add any file there then it will cause problem 
and we'll have to perform some extra commands to push back. we'll need to first pull from github then push.
_____________________________________________________________________

and in order to make sure noone has contributed/made changes to my remote repo on github, first do

>git pull origin master
to make sure its the same as before(best practices) 
and then push the changes that you did to github by doing. 

>git push origin master
_____________________________________________________________________


ANOTHER WAY :
intead of writing 
>git push origin master
to [ush from out local machine to github everytime

do

>git branch --set-upstream-to=origin/master

>git branch -vv
to see which all branches i have access to

now only 
>git push 
will push the changes made to github

>git fetch URL
to make your local repo uptodate. 

>git fetch upstream
if you already have set the upstream

>git merge upstream/master
to get you local repo uptodate with their REPO. 
________________________________________________________
#)create a new repository on the command line
>echo "# Resume" >> README.md
>git init
>git add README.md
>git commit -m "first commit"
>git remote add origin https://github.com/prik-k/Resume.git
>git push -u origin master
_________________________________________________________________________


17. UPDATES AND GIT DIRECTORY PATH 
>which git 
to get the path of git used
_____________________________________________________________________


18. HOW TO GO TO THE CONTENTS FROM THE HASH CODE 
which was provided after commit.(7 digit shorterened code)
take that 7 digit hasg code and

>git cat-file -p 7G7DF61

and then take the long code that generated and again copy that and do

>git cat-file -p XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

again a long hash will be created again repeate till you get the code inside the commited file. 
___________________________________________________________________________________________________


19. TIME TRAVEL
>git checkout XXXXXXXX 
it will take you to that state of commit

>git checkout master
to go back again to latest position of working

>git checkout <filename.ext>
to discard the changes made recently which are not added and revert the state to HEAD position
______________________________________________________________________________________________


20. SHOW CHANGES
>git diff index.txt
shows the changes occured in file

>git diff <hash code(8 digit)> <filename.ext>
to show the additions ocuured right from that commit


>git diff <hash code(8 digit)> HEAD <filename.ext>
to show the additions occured right from that commit to the position where head is present( not master )
__________________________________________________________________________________________________________________________________________


21. BRANCHES( or references )
>git branch 
to show  the number of branches currently

>git branch --v
to also show some extra info.

>git branch cat
makes a new branch 

>git checkout cat
switched  to branch cat
now HEAD points to cat and master points to whearever it was pointing,
now if we commit something then master will be behind our 'cat' branch and HEAD will be the 'cat'.
__________________________________________________________________________________________________________________________________________


22. MORE BRANCHES
>git branch dog; git checkout dog    ->2 commands to go to dog from master branch  
(shortcut for 2  commands )

>git checkout -b dog
now HEAD->dog, master. also HEAD is no longer at 'cat'
. 					cat
BY doing this we have 2 branches from --> master / 
				               \ 
				                dog.

EXAMPLE :-initially: only index file with hello word text
CAT branch :- added cat functionality
DoG branch :- added dog functionality

now checkout master
>git checkout master
____________________________________________________________________


Now we want to merge one by one or both at a time with master .

>git merge  cat
what this does is it makes HEAD to move to cat along with master to incorporate 'cat' functionality 
and now HEAD->cat, master.

>git merge dog
now there may be merge conflicts, so we have to manually resolve this

>git mergetool 
this tool helps to resolve issues but you need to config that first.

>git merge --abort
to abort changes

suppose merge conflict occurs then open the index file,
>>>>> means here you were .
===== means this is what you are trying to add. 
 now resolve the issue, save the file, 

add the file
>git merge --continue
now give a commit message

now cat dog branch are merged with master and HEAD-> master.
__________________________________________________________________________________________________________________________________________


23. BLAME
>git blame <filename>
to checkout who made changes to this line and the commit associated with it
To the right the contents of the file will be 
To the left the name and date of commits and commit id XXXXXXX

>git show XXXXXXXX
to see what all was changed and what was replaced. 
_______________________________________________________________________________________________________________________________


>git stash
reverts back me to the time when the last commit was made ignore all the changes thst i recently dont which was not commited
changes made are not deleted. 

To view them
>git stash pop

and then 
 >git diff <filename>
shows the changes that were made
____________________________________________________________________________________________________________________________


>git bisect
now you're long into the project and now some unit test is no longere passing which  passed few weeks back
this command will check going back one - one commit to see where in point of time was this test case passing

does a binary search into your history
We can even give it a string of test case to look for when this case was passed in the code in which point of time 





####################
*checkout for shell intergration
*Book - proGit
