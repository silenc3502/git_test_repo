# First(Local Repository)  
sudo apt-get install git  
git version  

## make local repo  
cd ~  
mkdir -p proj/git_local_test  
cd proj/git_local_test  
vi test.txt  

write anything to test.txt  

## We can get Initialized empty Git Repo  
git init  

## Check .git folder  
ls -al  

## How to make first commit  
git config --global user.email "git-email"  
git config --global user.name "git-account"  

## Check Status  
git status  

## Add or Track file  
git add test.txt  
git status  

## How to commit  
git commit -am "Some Description"  

## How to apply some changes  
vi test.txt  

Change something  

git status  
git commit -am "Some Changes"  
git status  

## Check Log  
git log  

We can see the commit xxxxxxx values  

git checkout xxxxxx  

We can rollback first commit  

cat test.txt 

## Goto Lastest checkout  
git checkout -  
cat test.txt  



# Second(Remote Repository)  
make new git repository name as git_remote_test at github.com  

## How to push local data to remote  
cd ~/proj/git_local_test  
git remote add origin https://github.com/$(git-account)/git_remote_test.git  
git push origin master  

## How to download remote data to local  
cd ~/proj  
mkdir git_remote_down  
ls  
cd git_remote_down  
ls  
git clone https://github.com/$(git-account)/git_remote_test.git  

ls  

## push to remote
vi developer.txt  

Write anything  

git add developer.txt  
git commit -am "Add Developer List"  
git push origin master  

## pull from remote to local  
cd ~/proj/git_local_test  
ls -alR  
git pull origin master  
ls -alR  



# Third(Git CLI Test)  
cd ~/proj/SpringExamples  

## get HEAD Associated commit info  
git log  

## get commit hash & title  
git log --oneline  

## get detailed HEAD Associated commit  
git log --oneline --graph --decorate  

## get all branches an so on  
git log --oneline --graph --all --decorate  

## get 7 info  
git log --oneline -n7  

## Ready to use git-cli  
cd ~/proj  
mkdir git_cli_remote  
cd git_cli_remote  
git init  

echo "hello git cli"  
echo "hello git cli" > echo.txt  
ls  
cat echo.txt  
git status  

git add echo.txt  
git status  

## How to unstage  
git reset echo.txt  
git status  

## Make remote repo at github.com  
name: git_cli_remote_test  

git remote add origin https://github.com/$(git-account)/git_cli_remote_test.git  
git remote -v  

git status  
git add echo.txt  
git status  

git push  

Then we can get some error.  

## How to solve it  
git push -u origin master  
git log --oneline -n1  
git push  

## How to change name when cloning git  
cd ~/proj  
git clone https://github.com/$(git-account)/git_cli_remote_test.git git_cli_local  
ls  

cd git_cli_local  
git remote -v  

echo "second" >> echo.txt  
cat echo.txt  

git commit -am "Add second line at echo.txt"  
git push  
git log --oneline  

## Check allright  
cd ~/proj/git_cli_remote  
cat echo.txt
git log --oneline  
git pull  
git log --oneline  
cat echo.txt



# Fourth(Git Branch Control)  
cd ~/proj/git_cli_remote  
git log --oneline  
git branch  
git branch mybranch  
git branch  
git log --oneline --all  

## Change Branch  
git checkout mybranch  
git log --oneline --all  
echo "Hello Git" > git_test.txt  
cat git_test.txt  
git status  
git add test.txt  
git commit -am "Add Git Test"  
git log --oneline --all  

## Check Master Branch  
echo "Additional Test" > git_test.txt  
cat git_test.txt  
git status  
git commit -am "Additional Test"  
git log --oneline --all --graph  
git checkout master  
cat git_test.txt  

## Merge to master  
git merge mybranch  
git log --oneline --all --graph  
cat git_test.txt  

## Branch Rollback  
git log --oneline --all  
git reset --hard HEAD~2  
git log --oneline --all  

## Rebase, Push, Remove Branch  
git checkout mybranch  
git rebase master  
git log --oneline --all
git checkout master  
git rebase mybranch  
git log --oneline --all  
git push -u origin master  
git branch -d mybranch  
git log --oneline --all -n2  

## Version Tagging  
git log --oneline  
git tag -am "Create Tag" v0.1  
git log --oneline  
git push origin v0.1  

## Create New Branch  
git checkout master  
git checkout -b radar  
echo "add function" >> func.txt  

git add func.txt  
git commit -am "Add Function"  
git log --oneline --graph --all -n2  

## Create Hotfix Branch, Commit, Merge to Master  
git checkout -b hotfix master  
git log --oneline --all -n2  
echo "Something" >> func.txt  

git add func.txt  
git commit -am "Add Something"  
git log --oneline --all -n1  
git checkout master  
git merge hotfix  
git push  

## Solve Conflict  
git checkout radar  
git log --oneline --all  
git merge master  
git status  

cat func.txt  
git add func.txt  
git status  
git commit  
git log --oneline --all --graph -n4  

## Rebase Project  
git checkout radar  
git reset --hard HEAD~  
git log --oneline --graph --all -n3  
git rebase master  
git push  

## Solve Conflict  
git status  
git add func.txt  
git status  
git rebase --continue  
git log --oneline --graph --all -n2  
git checkout master  
git merge radar  

## General Commit  
git "master" > master.txt  
git add master.txt  
git commit -am "master commit 1"  
git push origin master  
git log --oneline -n1  

## Branch Commit  
git reset --hard HEAD~
echo "branch" > master2.txt  
git add master2.txt  
git commit -am "branch commit 2"  
git log --oneline --graph --all -n3  

## Git Pull  
git pull  
git log --oneline --graph --all -n4  

## Delete Branch with Rebase  
git reset --hard HEAD~  
git rebase origin/master  
git log --oneline --all --graph -n3  
git push  

## Temporary Branch  
git branch test radar  
git checkout test  
echo "anything" > any.txt  
git add .  
git commit -am "tmp commit"  
git log --oneline --graph --all -n4  
git checkout master  
git branch -D test  
git log --oneline --graph --all -n4  
