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
