#nobodyzxc git note

git config --global user.name nobodyzxc
git config --global user.email dici86.chen@gmail.com
git config --global color.ui treu

git init

git add readme.txt
# add a file to current commit queue

git commit -m "wrote a readme file"
# commit files added by you
# [-n] to commit without msg

git status
# see modifiy records(current file compare with .git/file)
# if file modified and wait to commit , it will be green , or it will be red

git diff [ HEAD -- fileName ]
# details about modified content [ compare file in HEAD and file in worksapce ]

git log [--pretty=oneline] [--graph] [--abbrev-commit]
# see main version log

git reflog
# see all log (include removed , backed)

git reset --hard [ id ]
# change version pointer (HEAD)
# [id] = [ HEAD | HEAD^ | HEAD*^ | HEAD~(number) | (number) ]

git reset HEAD fileName
# recover some file form HEAD to worksapce
# remove add record in stage

git checkout -- fileName
# recover file in worksapce to stage or warehouse

git rm
# remove file in warehouse, 
# and if you rm file by accident, you can use checkout to recover

###############################################
# a new repository

git remote add origin [git@github.com:nobodyzxc/gitNote.git]
# build origin

git remote rm origin
# remove origin

git push -u origin master
# push to remote

###############################################

git checkout -b dev
# create a new dev and point on it
# equal to the two commands below
=> git branch dev
=> git checkout dev

git branch
# see the branchs

git checkout master
# add => commit => save dev => switch to master

git merge [--no-ff] dev
# merge [no fast forward mod(possible ignore some info] dev to master

git branch -d dev
# delete merge

git branch -D newFeature
# if a new branch never be merged, you should use -D to force delete it

###############################################

git commit --amend
# revise last commit comment

git rebase -i HAED~[number]
# revise previous commit comment
# change pick to edit
=> git commit --amend
=> git rebase --continue

###############################################

git stash
# save current status , clean workspace

git stash list
# see stash list

git stash apply
# recover previous worksapce

git stash drop
# delete saved worksapce

git stash pop
# recover previous worksapce & delete saved worksapce

###############################################

git push origin ( master | dev )
# push master or dev to remote

# if you want to clone a dev, clone master first
git clone git@github.com:xxxxxxx/xxxxxx.git

git checkout -b dev origin/dev
# take dev on remote to local

# when push a dev failed because the origin/dev has been cheanged
# pull origin/dev and merge them
# first set link between local dev and origin/dev
git branch --set-upstream dev origin/dev
         #(--track | --set-upstream-to) update!!
         # --set-upstream is too old

# then pull
git pull

# start merge... then push

###############################################

# swtich to master
git checkout master

# then paste a tag
git tag v1.0 [ -m some_intro ] [ commit id ]
             [ -d (delete) ]
git tag
# see all tags

git show [tag name]
# tag details

# push tag
git push origin [tag name]

# if you want to delete remote tag, remove local tag first
git tag -d v1.0
# then remove remote's
git push origin :refs/tags/v1.0

# alias
git config --global alias.st status
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

# conf stat => .git/config
