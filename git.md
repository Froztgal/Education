# GIT

https://www.w3schools.com/git/git_new_files.asp?remote=github

VCS - 

Repository - Data base of linked states  
Working copy  
Stage - prepare state  

Commit = State != Changes  
History - linked states

Branch - 

## Commands
git init  
git status  
git add  
git commit  
git log  
git show  
git branch  
git checkout  
git merge  
git reset  
git hist ```https://skazkin.su/sozdanie-komandy-git-hist-krasivyj-log-kommitov/```  
git revert  
git remote  
git fetch  
git push  
git pull  

## Configure git
Для настройки имени пользователя и почты нужно использовать следующие команды в консоли.  
Флаг ```--global``` настраивает эти данные глобально (для всех репозиториев).  
Если же необходимо настроить имя и почту только для одного репозитория, то необходимо зайти в директорию локальной копии и выполнить данные команды без фалага ```-global```.
```console
git config --global user.name "{name}"
git config --global user.email "{email}"
```
