---
layout: post
title:  "Vim, A Fast Guide for Newcomers."
date:   2017-05-05 00:20:12 -0500
categories: Text_Editors
---
# Vim

Vim is an advanced text editor that seeks to provide the power of the de-facto Unix editor 'Vi', with a more complete feature set.  
so, install it:

    sudo apt-get install vim

You can open files using:

    vim namefile

![vim_init][vim-init]

## Basics of Moving in Vim

Vim accept interac through shell using keys like:

* '`.' move to the last word edit.

* `h` moves the cursor one character to the left.
* `l` moves the cursor one character to the right.

* `j` moves the cursor down one line.
* `k` moves the cursor up one line.

* `0` moves the cursor to the beginning of the current line.
* `$` moves the cursor to the end of the current line.

* `w` move to the beginning of the next word.
* `b` move to the beginning of the previous word.

* `e` move to next word end.
* `ge` move to previous word end.

* `gg` move to the beginning of the file.
* `G` move to the end of the file.

* `ctrl-u` moves to the previous page of the document.
* `ctrl-d` moves to the next page of the document.

Note: if your press `k`, Vim move the cursor up 1 line, but if you press `10k` Vim move the cursor up 10 lines.

## More movements in Vim

* `W` move to the beginning of the next word like blankspace, `\n` or `\t`.
* `B` move to the beginning of the previous word like blankspace, `\n` or `\t`.

* `E` move to next word end like blankspace, `\n` or `\t`.
* `gE` move to previous word end like blankspace, `\n` or `\t`.

* `(` Go to the beginning of the sentence.
* `)` Goes to the end of the sentence.

* `{` Go to the beginning of the paragraph.
* `}` Go to the end of the paragraph.

* `|` Goes to the first visible column on the screen.

## Modes of Vim

Vim has 6 modes, a normal mode, insertion mode, replace mode, visual mode, selection mode and CLI mode:

* `ESC` activates normal mode, now you can write a command like write (:w) o quit (:q).
* `:` activates CLI mode, now you can write w to save o q to exit.

## Normal Mode

In `/etc/vim/vimrc` file, add:

    "show number line"
    set number

    "tabulation step"
    set tabstop=2 softtabstop=2 shiftwidth=2 expandtab

    "indent at press enter"
    set autoindent

    "show current position"
    set ruler

## CLI Mode

Vim has this mode when you use the `:` and other letters like:

* `! date` shows all the changes did in a file.

* `e namefile` creates a new file named `namefile`.

* `b#` where `#` is a number (1, 2, etc), is like tabs.

## Insertion Mode

Vim has ways to activates insertion mode:

* `i` the cursor is left where it was.
* `I` moves the cursor to the end of the current line.

* `a` The cursor moves one character to the right.
* `A` moves the cursor to the end of the current line.

* `o` inserts a new line below the current line and moves the cursor to the beginning of that new line.
* `O` inserts a new line above the current line and moves the cursor to the beginning of that new line.

## Replace Mode

* `R` activates replace mode.
* `INS` activates normal mode from replace mode and viceverse.

## Visual Mode

* `v` activates visual mode, now you can select by letters.
* `V` activates visual mode, now you can select by lines.
* `ctrl-v` activates visual mode, now you can select by colums.

* `vG` select all document from the current position of the cursor until the end of the file..
* `vgg` select all document from the current position of the cursor until beginning of the file.

* `u` converts the entire selection to lowercase.
* `U` converts the entire selection to uppercase.

* `>` adds a tabulation.
* `<` removes a tabulation. 

## Selection Mode

* `gh` or `gH` activates selection mode.
* `gh` is similar to `v`.
* `gH` is similar to `V`.
* `gctrl-h` is similar to `ctrl-v`.
* `ctrl-home` select all until the beginning of file.
* `ctrl-end` select all until the end of file.

## Deleting text in Vim

* `d` starts the delete operation.
* `dw` will delete a word.
* `d0` will delete until the beginning of a line.
* `d$` or `D` will delete until the end of a line.
* `dgg` will delete until the beginning of the file.
* `dG` will delete until the end of the file.
* `d{` will delete until the beginning of paragraph.
* `10dd` or `d10d` delete 10 lines.
* `d12G` will delete from the current position of cursor to the line number 12.

* `J` will delete `\n` and blank spaces.
* `gJ` will delete `\n` but not blank spaces.

* `c` is identical to `d` but this option activates insertion mode.
* `cc` is identical to `dd` but this option activates insertion mode.

* `x` will delete the first caracter on the right side of the cursor.
* `X` will delete the first caracter on the left side of the cursor.

## Copy and Paste text in Vim

* `p` paste text after the current line.
* `P` paste text on the current line.

* `y` starts the delete operation.
* `yw` will copy a word.
* `y0` will copy until the beginning of a line.
* `y$` will copy until the end of a line.
* `ygg` will delete until the beginning of the file.
* `yG` will delete until the end of the file.
* `10yy` or `y10y` copy 10 lines.
* `y12G` will copy from the current position of cursor to the line number 12.

## Undo and Redo

* `u` will undo the last operation.
* `U` discard all changes in the current line.
* `Ctrl-r` will redo the last undo.

## Searching and replacing

* `/word` search for `word` in the document, going forward.
* `n` move the cursor to the next instance of the text from the last search. This will wrap to the beginning of the document.
* `N` move the cursor to the previous instance of the text from the last search.
* `?word` search for `word` in the document, going backwards.
* `:%s/orginal/new word/g` search through the entire document for text and replace it with replacement text.
* `:%s/orginal/new word/gc` search through the entire document and confirm before replacing text.

## Write and Exit of Vim

Vim accept 2 ways to write (or save) and exit:

* `q` Exits window.

* `:q!` Exits without saving changes.
* `Z!` Exits without saving changes.

* `:wq` Exits and saving changes.
* `ZZ` Exits and saving changes.


[vim-init]:  /assets/textEditor/vim/vim_init.png
