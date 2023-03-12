# git commit --amend
 -- amend komutunu sadece local branch icin kullanmak gerekir. 
 mastter üzerinde --amend komutu conflictlere sebep olur
 
## Temel mantik 

The git commit --amend command is a convenient way to modify the most recent commit.
It lets you combine staged changes with the previous commit instead of creating an entirely new commit.
It can also be used to simply edit the previous commit message without changing its snapshot.

kisaca son commiti düzenlemek ve commit mesajini degistirmek icinde kullanilir.
## VIM EDITOR 

0. Write your message
1. click esc
2. : type
3. wq save and quit
````
problem cikarsa vim editor ac:
vim editorde iki mod var 
1. command mode 
2. edit/insert mode (click i )

1. Insert mode (Where you can just type like normal text editor. Press i for insert mode)
2. Command mode (Where you give commands to the editor to get things done . Press ESC for command mode)
Most of them below are in command mode

x - to delete the unwanted character
u - to undo the last the command and U to undo the whole line
:wq or :x! - to save and exit
:q! - to trash all changes

````

## Short way to arrange commit message

git commit --amend -m "message"

### I'm going to amend into the previous commit along with this new text.

### Note

Amending a Commit Without Changing Its Message
If you don’t want to change your commit message, you can run the amend command with the no-edit flag, like this:

git commit --amend --no-edit

# Remember: NEVER amend (rewrite) the commit history of public branches(like master).This will truly mess your teammates work.


* Watch out for options like --hard and --force though — they can discard data.
* Also, don't rewrite history on any branches you're collaborating on.




# GIT REFLOG

``git reflog ``

komutu ile unreachable commitleri de görebiliriz.

When i want to reach an unreachable commit 

````
git checkout <commit hash>
git checkout -b Resetting-to-<commithash>-for-rework

````
When i want to delete again 
````

git branch -d (veya) D Resetting-to-<commithash>-for-rework
 -D hart delete
````
# Differencies between git pull and git pull origin master

You could specify what branch you want to pull:

 ``git pull origin master``
``git pull origin branchName``
Or you could set it up so that your local master 
branch tracks github master branch as an upstream:

``  git push --set-upstream origin branchName``
After that can i use 
``git pull``
This branch tracking is set up for you automatically when you 
clone a repository (for the default branch only), but if you add a remote to an existing repository you have to set up the tracking yourself.


# Differencies between git push and git push origin master or branch

``git push``
It pushes changes of all branches to the GitHub repository.
It pushes work implicitly to the GitHub repository.
It can be only utilized with a single repository.

``git push origin <branch>``

It pushes changes to specific remote branches.
It pushes work explicitly to the GitHub repository.
It can be utilized with both single and multiple repositories.



### Conclusion
In the Git terminal, the ``git push`` command uploads all the local branch changes to the GitHub repository. 
Whereas, the ``git push origin <branch>`` command pushes the local changes to the particular remote branch.
This blog differentiated between ``git push origin <branch>`` and ``git push`` commands.

![Screenshot](8341g68g1v7y.png)