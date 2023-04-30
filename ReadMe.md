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
* Problems start occurring when the commit is already pushed to GitHub and 
I want to amend a commit that I already pushed up.

``push — force-with-lease`` or ``git push -f origin``
One way to handle this is to use git push --force-with-lease to overwrite the last commit.
Bu sekilde pushed edilmis bir commit tekrar düzenlenebilir 
ama conflict olusma durumlari göz önünde bulundurulmali

# undo and revert
"Commit undo" ve "commit revert", yazılım geliştirme sürecinde yapılan değişikliklerin geri alınması için kullanılan iki farklı terimdir.

"Commit undo", son yapılan commit işlemini geri alır ve bu değişiklikleri siler. Bu işlem, son commit işlemi üzerindeki değişiklikleri tamamen geri alır ve projede kaydedilmiş en son versiyona geri döner.

Öte yandan, "commit revert" değişiklikleri geri almak için bir yöntemdir, ancak burada değişikliklerin tamamı silinmez. Bunun yerine, geri alınan değişiklikler, yeni bir commit olarak kaydedilir ve projenin geçmişinde bir değişiklik kaydı olarak kalır. Bu yöntem, bir hata yapılırsa veya bir değişiklik hatalıysa geri alınması gerektiğinde kullanışlıdır.

Özetle, "commit undo" son commit işlemi üzerindeki değişiklikleri tamamen silerken, "commit revert" ise geri alınan değişiklikleri yeni bir commit olarak kaydederek geçmişte bir kayıt olarak tutar.

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
q

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

![8341g68g1v7y](https://user-images.githubusercontent.com/96315214/224517960-6e12f36a-42bf-4be2-a455-5e15dbf6e65c.png)
![XwVzT](https://user-images.githubusercontent.com/96315214/224517983-c8cf3061-d05f-47d6-9efe-01bbd5df043d.png)



 # Stashing your work
The ``git stash`` command takes your uncommitted changes (both staged and unstaged), 
saves them away for later use, and then reverts them from your working copy.

# Re-applying your stashed changes
You can reapply previously stashed changes with ``git stash pop``:
Popping your stash removes the changes from your stash and reapplies them to your working copy.

Alternatively, you can reapply the changes to your working copy 
and keep them in your stash with ``git stash apply``:
This is useful if you want to apply the same stashed changes to multiple branches.

# Managing multiple stashes
You aren't limited to a single stash. You can run git stash several times to create multiple stashes, 
and then use git stash list to view them. 
By default, stashes are identified simply as a "WIP" – work in progress – on top of the branch and 
commit that you created the stash from. After a while it can be difficult to remember what each stash contains:

$ ``git stash list``
``stash@{0}``: WIP on main: 5002d47 our new homepage
``stash@{1}``: WIP on main: 5002d47 our new homepage
``stash@{2}``: WIP on main: 5002d47 our new homepage

### To provide a bit more context, it's good practice to annotate your stashes with a description,
using git ``stash save "message"``:

$ ``git stash save "add style to our site"``
Saved working directory and index state On main: add style to our site
HEAD is now at 5002d47 our new homepage

``$ git stash list``
``stash@{0}``: On main: add style to our site
stash@{1}: WIP on main: 5002d47 our new homepage
stash@{2}: WIP on main: 5002d47 our new homepage
By default, git stash pop will re-apply the most recently created stash: stash@{0}

### You can choose which stash to re-apply by passing its identifier as the last argument, for example:

``$ git stash pop stash@{2}
``

## To create a remote repo on terminal

Firstly i have to install hub-scoop or hub-chocolatey 
i install scoop with this command (scoop install hub)

after that on powershell run these code
> Set-ExecutionPolicy RemoteSigned -Scope CurrentUser

 Optional: Needed to run a remote script the first time

> irm get.scoop.sh | iex

After all of that run on your terminal (hub create)
enter your github username and enter your access token instead of password
and the magic.....

# Generate new Token on github

![Screenshot 2023-04-25 121114](https://user-images.githubusercontent.com/96315214/234247009-c086162f-3f42-472a-9067-20cf9a81c6d3.png)

![Screenshot 2023-04-25 121128](https://user-images.githubusercontent.com/96315214/234247072-4d311e4f-9fa8-451e-9d35-d0546984d0d6.png)

![Screenshot 2023-04-25 121134](https://user-images.githubusercontent.com/96315214/234247105-44a3f460-6564-4578-b173-cef8d434e554.png)


![Screenshot 2023-04-25 121150](https://user-images.githubusercontent.com/96315214/234247168-3fdbec52-ecdf-4f95-80b0-d79fdba0b156.png)


