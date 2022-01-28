

# GIT BASH COMMANDS
## Git is a Distributed graph theory tree model.

To save your password with github permanently, make a file ```.netrc``` in ```home/<username>```, add the following and then save. 

```
machine github.com
login <login_github>
password <password_github>
```

or better use SSH key method, it's difficult to get it set for the first time but that's worth it. 

<hr>

1. To open a file (eg .js or .html file in Windows)
 ```
 notepad fileName.fileExtension
 ``` 

2. CLONE
```
git clone <url> <folder where to clone it>
```

```
git clone --shallow
->  if the repository is very big, this command avoids to download commits made earlier in that project.
```



3. CONFIGURATION
to setup name and email,
```
git config
-> to show all things which can be done using this command
-> configure .gitconfig file to make it behave your way, search internet

git config --global user.name "Priyansh Khodiyar"

git config --global user.email "khodiyarprouansh@gmail.com"

git config --gloabl --list
-> shows our name and email.
-> now, a text file is created that contain these details

cat ~/.gitconfig
-> here it will show the name and email
```



4. BASIC COMMANDS
```
ls -a 
-> shows all the hidden folders

git init 
-> cd into the project folder and type this

git init git-demo
-> git initialized only in git-demo folder

clear
-> to clear the console/terminal.
```


5. ADD AND COMMIT AT THE SAME TIME
```
git add <fileName.fileExtension>
-> to add single files to git

git add .
-> to add every file and folder to git

git commit -m "type your git msg"
-> every git commit must have a message to provide a little detail of what was changed, emojis can also be used

git commit -am "type your commit message here"
-> a for ADD and m for MSG
-> add and commmit in one single step can be done for MODIFIED files only, not for the newly created files.

git status
-> to check which all files that you added or commited are ready to be pushed to github or other project hosting sites.

-> suppose you made 2 changes to a file and you want to add only one of them
git add -p <filename>
-> this will show [ y/n ] to add/ not add the changes made for every single changes

git diff --catched
-> shows which changes are staged for commit

git checkout <filename >
-> to throw out the unwanted changes which should not be added in a file.  
```


6. REVERT BACK 
after we modified a file and added it to commit stage, if we want to revert back, 
```
git reset HEAD <fileName>.
-> now it's again in the modified stage, if we further want to revert those changes that we did in a file, do 

git checkout -- <fileName.ext> 
-> this is make the file like how it was before modifying it.
```

7. LOGS 
```
git log
-> all commits shown here, but this much info may be too much, so type 

git help log 
-> to get options to log 

git log --oneline --graph --decorate --color --oneline
-> gives a compact and beautiful view of logs.
```

8. REMOVING FILES
```
git rm <fileName>
-> to remove a file, but still removal needs to be commited, so do a final commit to remove files. 
```
ANOTHER WAY (OS Level) : 
```
rm <fileName.ext>
-> removes file without gits info and it's there in the commit zone, but can't be commited as it can't be added back.

git add -u 
-> to stage it for commit and then commit.
```


9. MOVING FILES (between folders)
```
git mv <fileName.ext> <folderName>
-> moving from a file in master to a folder in master. Commit these at last
```


10. IGNORING FILES
like we dont want to push .log files so ignore them, make a .gitignore file using 
```
notepad .gitignore

*.log
-> and inside this file type this, this prevents any .log extension files to get added or commited.
```

11. SSH key Authentication 
```
cd ~ 
-> to get back to home/ root directory now type 

cd .ssh 
-> to see if the .ssh key exist or not, if not then

mkdir .ssh 
cd .ssh/
ssh-keygen -t rsa -C "<yourRegisteredEmail>"

-> then it will generate id_rsa and id_rsa.pub, we'll use .pub file with github.
-> SSH keys are tied to the computer. Copy the contents of .pub file and paste it in github settings at SSH settings.

After successful authentication, type
ssh -T git@github.com
-> to get a success msg.
-> return to home directory cd ~
```


12. COLLABORATE WITH OTHERS (PULL REQUESTS)
create a new repository in github, set everything as default. 

NOTE : remote means making a channel for other people to have connections with our files. 
It can be connected to other folders of our system as well, 
e.g.
```
git remote add origin ../<folder name where the remote will be setup for this repository>
```

NOTE: you must be inside the git initiated folder to perform the following code below.

```
git remote add origin git@github.com <username>/<repoName.git>
OR
git remote add origin <Repository URL>
-> to add the URL of your github repository so that you can push and pull changes

git remote -v
-> to check which remote URL was added

then 

git push -u origin main
-> -u is done for the first time use to make a "uplink"
-> now our local folder repo is pushed to github
```
NOTE: Always first pull the changes from Github repository before making a push. 

Now locally we can modify the files, add and commit and then if we check the status then it will show which branch is ahead by commits as we re in sync with github(using SSH)  


```
git remote remove origin 
-> to remove set remotes
``` 

NOTE :  While creating a new repo we add/create any file in the repository (like a readme.md file) then it will cause problem and we'll have to perform some extra commands to push your changes to Github. We'll need to first pull from our repository then push.


and in order to make sure none has contributed/made changes to my remote repo on github, first do
```
git pull origin main
OR simply
git pull 
-> if there is only 1 branch
-> to make sure its the same as before (best practices) and then push the changes that you did to the files of the project, to github by 

git push origin master
```

ANOTHER WAY :
intead of writing 
```
git push origin master
```
to push from out local machine to github everytime. 

do

```
git branch --set-upstream-to=origin/main

git branch -vv
-> to see which all branches i have access to

now 
git push 
-> will push the changes you made, to github

git fetch <Repo URL>
-> to make your local repo uptodate. 

git fetch upstream
-> if you already have set the upstream

git merge upstream/master
-> to get you local repo uptodate with their repo. 
```


13. Connecting your project folder with already created emptry Github repository
```
echo "# New_Repository" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin <URL>
git push -u origin master

Note: Here URL means your Github repository link where your project will be uploaded/pushed to
```

14.  UPDATES AND GIT DIRECTORY PATH 
```
which git 
-> to get the path of git used
```


15. HOW TO GO TO THE CONTENTS OF A FILE FROM ONLY THE HASH CODE
which was provided after commit.(7 digit shorterened code)
take that 7 digit hash code and
```
git cat-file -p 7G7DF61
```
and then take the long code that generated and again copy that and do
```
git cat-file -p XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```
again a long hash will be created again repeate till you get the code inside the commited file. 



16. TIME TRAVEL IN GIT
```
git checkout XXXXXXXX 
-> it will take you to that state of commit
-> XXXXXXXX is the commit hashcode, kind of an ID of that commit

git checkout master
-> to go back again to latest position of working, if you went back in time to see initial state of your git project

git checkout <filename.ext>
-> to discard the changes made recently which are not added and revert the state to HEAD position
```


17. SHOW CHANGES
```
git diff index.txt
-> shows the changes occured in file

git diff <hash code(8 digit)> <filename.ext>
-> to show the additions occured right from that commit


git diff <hash code(8 digit)> HEAD <filename.ext>
-> to show the additions occured right from that commit to the position where head is present (not master)
```

18. BRANCHES (or references)

NOTE: Master is equal to Main, after Github changed it's notation due to BLM. (To remove Master-Slave references)
```
git branch 
-> to show  the number of branches currently

git branch --v
-> to also show some extra info.

git branch cat
-> makes a new branch 'cat'

git checkout cat
-> switched  to branch cat
-> now HEAD points to cat and main points to whearever it was pointing earlier,
-> now if we commit something then master will be behind our 'cat' branch and HEAD will be the 'cat'.
```


19. MORE BRANCHES

now that we have a 'cat' branch, let's create a dog branch
```
git branch dog; git checkout dog    
-> commands to go to dog from main branch  
-> ';' is shortcut that runs 2 commands at a time

git checkout -b dog
-> now HEAD ->  dog, main  Also HEAD is no longer at 'cat'. 

               					 cat.
BY doing this we have 2 branches from -->  main / 
				               \ 
				                 dog.

EXAMPLE :-initially: only index file with "hello word" text
cat branch :- append "added cat functionality" to text file
dog branch :- append "added dog functionality" to text file

-> now checkout master
git checkout master
```

Now we want to merge one by one or both at a time with the main branch.

```
git merge  cat
-> what this does is it makes HEAD to move to 'cat' along with main to incorporate 'cat' functionality text. 
-> and now HEAD ->  cat, main.

git merge dog
-> now there may be merge conflicts, so we have to manually resolve this. 

git mergetool 
-> this tool helps to resolve issues but you need to config that first in your git project

git merge --abort
-> to abort making changes
```

Suppose merge conflict occurs then open the index file,
```
>>>>> means here you were

===== means this is what you are trying to add. 

now resolve the issue, save the file (delete these >>>>> and ===== symbols before saving the file)


git merge --continue
-> add the file and give a commit message
```
now cat dog branch are merged with main and HEAD->  main


20. BLAME
```
git blame <filename>
-> to checkout who made changes to particular lines and the commit associated with it
-> To the right, the contents of the file will be present
-> To the left, the name and date of commits and commit id XXXXXXX

git show XXXXXXXX
-> to see what all was changed and what was replaced. 

git stash
-> reverts back me to the time when the last commit was made and ignore all the changes that I recently made, commited changes are not deleted. 

git stash pop
-> to view them

and then 
git diff <filename>
-> shows the changes that were made

git bisect
-> now you're long into the project and now some unit test is no longere passing which used to pass a few weeks back, this command will check going back one - one commit to see where in point of time was this test case passing, it does a binary search into your history
-> We can even give it a string of test case to look for when this case was passed in the code in which point of time. Advanced stuff. 
```



Books
1. proGit. 
