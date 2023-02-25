# git commit --amend
 -- amend komutunu sadece local branch icin kullanmak gerekir. 
 mastter üzerinde --amend komutu conflictlere sebep olur
 
## Temel mantik 

The git commit --amend command is a convenient way to modify the most recent commit.
It lets you combine staged changes with the previous commit instead of creating an entirely new commit.
It can also be used to simply edit the previous commit message without changing its snapshot.

kisaca eski commitleri düzenlemek ve commit mesajini degistirmek icinde kullanilir.
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




