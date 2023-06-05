#linux #LPIC-1 


### The Finder Pattern: grep
One of the most common uses of `grep` is to facilitate the inspection of long files, using regular expressions as a filter applied to each line.

There are two complementary programs to `grep`: `egrep` and `fgrep`. 

The program `egrep` is equivalent to the command `grep -E`, which incorporates extra features other than the basic regular expressions.

The program `fgrep` is equivalent to the command `grep -F`, that is, it does not parse regular expressions.

### The Stream Editor: sed
The purpose of the `sed` program is to modify text-based data in a non-interactive way.

In modern terms, `sed` can be understood as a template parser: given a text as input, it places custom content at predefined positions or when it finds a match for regular expressions.

The basic syntax for this command is:

```bash
sed -f SCRIPT # to edit a file named SCRIPT
sed -e COMMANDS # to execute COMMANDS directly from the command line 
```

By far, the most used `sed` instruction is `s/FIND/REPLACE/`, which is used to replace a match to the regular expression `FIND` with text indicated by `REPLACE`.

For example, the instruction `s/hda/sda/` replaces a substring matching `hda` with `sda`. Only the first match in the line will be replaced, unless the flag `g` is placed after instruction, as in `s/hda/sda/g`.

The file `/var/log/wtmp` records all logins and logouts, whilst the file `/var/log/btmp` records the failed login attemps. They are written in binary format, which can be read by the commands `last` and `lastb`, respectively.

---
Key knowledge areas
• Create simple regular expressions containing several notational elements.
• Understand the differences between basic and extended regular expressions.
• Understand the concepts of special characters, character classes, quantifiers and anchors.
• Use regular expression tools to perform searches through a filesystem or file content.
• Use regular expressions to delete, change and substitute text.
Partial list of the used files, terms and utilities
- ✅ `grep`
- ✅ `egrep`
- ✅ `fgrep`
- ✅ `sed`
- ✅ regex(7)