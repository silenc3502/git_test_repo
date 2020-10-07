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

# Second
