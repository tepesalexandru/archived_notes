#linux #LPIC-1 

### Vi & Vim
In most Linux distributions, `vi` - abbreviation for "visual" - is pre-installed and it is the standard editor in the shell environment.

An alternative to `vi`, called `vim` (vi improved), is sometimes used as a modern replacement for `vi`. Among other improvements, `vim` offers support for syntax highlighting, multilevel undo/redo and multi-document editing.

Although more resourceful, `vim` is fully backwards compatible with `vi`, making both indistinguishable for most tasks.

In order to start `vi`, simply give it a line number and the name of the file:

```bash
vi +9 /etc/fstab
```
This command will open the `/etc/fstab` file on line 9. If the line number is not provided, the cursor will be placed on the last line.

There are different execution modes for `vi` where program behavior changes. The most common are: `insert` and `normal mode`.

#### Registers
`vi` allows the creation of `registers` by starting a command with `"`.

#### Macros
In `vim`, `macros` are saved in the `~./vimrc` file, such as the following:

```lua
let @d = 'xi""P'
```

#### The default shell editor
The Linux shell makes use of the session variable `VISUAL` or `EDITOR` in order to find out the default editor for the shell. For instance, the following command changes the shell editor:

```bash
# Changes the default editor to nano
export EDITOR=nano
```

To make the change persist across sessions, the command should be included in the `~/.bash_profile` file.

--- 
Concepts in this lesson:
- ✅ vi
- ✅ /, ?
- ✅ h, j, k, l
- ✅ i, o, a
- ✅ d, p, y, dd, yy
- ✅ ZZ, :w!, :q!
- ✅ EDITOR