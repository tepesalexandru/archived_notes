#vim

Vim is a `modal text editor` based on the `vi` editor written by Bill Joy in the 1970s for a version of UNIX.

It inherits the key bindings of `vi`, but also adds a great deal of `functionality` and `extensibility` that are missing from the original vi.

### What does `modal` mean?
When you're using most word processors and text editors, the alphanumeric keys a-z 1-9 are only used to input those characters unless they're modified by a control key.

In Vim, the `mode` that the editor is in determines whether the alohbanumeric keys will input those characters or move the cursor through the document.

Therefore, `modal` means that vim has `multiple modes` that you can use.

Many text editors and word processors require you to `use the mouse` to click a menu item or icon, or use the CTRL + S hotkey combination, to save a file. 

In Vim, you can save a file without your hands leaving the keyboard. 

The command for saving is `:w`.

### Why learn Vim?
Vim is a complex tool, and for that reason is not for everyone. You need to be prepared to learn the ins and outs of vim in order to fully master it, and is only useful if you're constantly doing heavy editing of text in your day to day life, such as `programming` or `system administration`.

Even though Vim isn't as easy to use initially compared to other text editors, you will become more `productive` in the `long term` compared to the alternatives.

Most of that speed will come from you not having to use the mouse anymore, as you can do anything you usually would've done with the mouse or touch pad, with a command in Vim.

System administrators need to know the fundamentals of Vim because it's the editor of choice on any Unix system that you need to work on (such as Ubuntu Server).

For programmers, Vim is a great tool as it offers vast amount of features that will cover all of your needs when writing software.

### The Modes
Vim has three core modes:
- `Insert Mode` - used to type or make changes to the document at hand
- `Command Mode` - the default mode
- `Last-Line Mode` - used to execute commands starting with `:`

### Basic Movement in Vim
The principal thing you need to master when learning Vim is how to move around in a file.

"WASD" Movements:
- `h` - moves the cursor one character to the left
- `j` - moves the cursor down one line
- `k` - moves the cursor up one line
- `l` - moves the cursor one character to the right

Exercise these for at least one day, and tomorrow I'll see you in the next article with another 4 commands.

Word Movements:
- `b` - move backward one word
- `w` - move forward one word

You can also combine the 6 commands we've learned so far with a number. For example:

```vim
5l // moves you 5 characters to the right
2b // moves you 2 words backward
3k // moves you 3 lines up
```

### Editing in Vim
Now that you know how to move around a bit, let's try editing.

Here are fundamental commands for editing:
- d - starts the **delete** operation
- dw - deletes a word
- d0 - deletes everything between the start of the line and the current cursor position
- d$ - same as d0, just for the cursor -> end of line
- dgg - deletes everything from the cursor to the beginning of the file
- dG - deletes everything from the cursor to the end of the file
- u - undo the last operation
- CTRL + r - redo the last undo

### Searching and Replacing
It's time to learn how to use search and replace in Vim. If you want to search through the document from command mode, use `/` followed by the text you want to search for.

If you need the next instance of the word, press `n`. If you want the previous instance of the text, press capital `N`.

In order to replace text in your document, start your command with `:%s` and then `/<text>/<replacement>/g` to replace every instance of it with. 

So, for example the following command will replace every occurence of "bunny" with "cat":

`:%s/bunny/cat/g`

---

References:
https://www.linuxfoundation.org/blog/blog/classic-sysadmin-vim-101-a-beginners-guide-to-vim
