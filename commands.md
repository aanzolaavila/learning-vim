# Opening files
`:r file.txt`
Insert the file file.txt below the cursor in current buffer

`:0r file.txt`
Insert the file file.txt before the first line

`:r!sed -n 2,8p file.txt`
Insert lines 2 to 8 from file file.txt below the cursor

`:r !ls`
Insert a directory listing below the cursor

---

# Closing files
`:x`
Exit Vim but write only when changes have been made

`ZZ`
Equivalent to :x. Notice there's no `:`. This is a key press.

`:qa`
Exit all open files in current Vim session

---

# Saving files
`:w! file.txt`
Save file as file.txt with overwrite option

`:sav[!] file.txt`
Save current buffer as a new file file.txt [! forces write if it exists]

`:up[date] file.txt`
Like :w but only save when the buffer has been modified

---

# Navigation
`w`
Go to the start of the next `word`

`W`
Go to the start of the next `WORD`

`e`
Go to the end of the current `word`

`E`
Go to the end of the current `WORD`

`b`
Go to the previous (before) `word`

`B`
Go to the previous (before) `WORD`

> `WORD` consists of a sequence of non-blank characters. It's always delimited by white space.
> `word` is delimited by non-key`word` characters, which are configurable.

> When navigating, if you're going through source code, then use `w`. Otherwise, if going through text, then `W`.

## Scrolling pages
Ctrl-d
Scroll down half page

Ctrl-u
Scroll up half page

Ctrl-f
Scroll down full page

Ctrl-b
Scroll down full page

## Jumping around the file
`gg`
Go to the top of the file

`G`
Go to the bottom of the file

`{`
Go to the beginning of current paragraph 

`}`
Go to the end of current paragraph

`%`
Go to the matching pair of (), [], {}

`50%`
Go to line at the 50% of the file

`:NUM`
Go to line NUM. :28 jumps to line 28 

## Navigating inside the window
`H`
Move cursor to first (highest) line in current window

`L`
Move cursor to lowest line in current window

`M`
Move cursor to the middle of the current window

> While in Insert mode, you can press Ctrl-o to get back to Normal mode and execute one command, after which you'll be automatically returned to Insert mode

# Basic search 

## Searching for the current word
> Vim can search for words under your cursor. In Normal mode, place your cursor to any word.
> Press * and Vim will search forwards for the next occurrence of that word.
> Press # and Vim will search backwards for the word under your cursor.
> These two commands are searching for exact words. For that reason, when searching for 'master' it will not find 'mastering'.

> If you don't want exact word matching, use commands `g*` and `g#` accordingly. 

## Search history
> If you have the cursor in a word, and you want to search for a similar word, instead of typing the entire word, you can:
> Press /, and then press Ctrl-r and then Ctrl-w

> Once you're done with searching, you can hit Ctrl-o to jump back to your previous position (or Ctrl-i which will jump forwards)

> To jump to the 5-th occurrence of a patten, simply type 5/pattern
> 6\* will search for the 6th occurrence of the current word under the cursor

---

# File Manager (netrw) in Vim
`:Ex`
Open current directory in current Vim window (remember it as a shortcut for **Ex**plore)

`:Ex <dir>`
Open specified directory <dir>

`:Sex`
Open current directory in horizontal split window

`:Vex`
Open current directory in a new tab

`:Tex`
Open current directory in a new tab

`:Lexplore`
Open current directory in vertical split on the left. Default setting opens files in the window to the right of the netrw window

`:40vs +Ex`
Open current directory in vertical split window with width of 40 columns

## Changing how files are opened
> You can perform some of the basic file manager operations using netrw:

`<Enter>`
Opens the file under the cursor, or enters the directory under the cursor

`D`
Deletes the file under the cursor. You can visually select multiple files and use this command to delete all of them

`R`
Renames the file under the cursor

`X`
Executes the file under the cursor

`%`
Creates a new file in the current directory. Vim will ask you for a file name and open a buffer.

---

# Editing files via SSH
> Vim has the ability to edit file remotely through SSH. Here is how to do it:
> $ vim scp://user@myserver[:port]//path/to/file.txt

> Besides SSH, there are other protocols such as:
> - sftp
> - ftp
> - dav
> - etc...

> To use any of them, like ftp, you can use
> $ vim ftp://hostname/path/to/file

> More info on :help scp

---

# Personalizing Vim
> If you want to enable spell checking for default, you should :set spell
> If you want multiple languages, you can `:set spelllang=en,de,it`

`:set nospell`
Disable spelling

---

# Undo and Redo
`u or :u`
Call undo command

`U`
Undo all recent changes on the current line

Ctrl-r or :red[o]
Call the redo command

`:earlier 2d`
Undo changes in last two days

`:ea 3h`
Undo changes in last three hours

`:ea 1m`
Undo changes in last one minute

`:later 5m`
Redo all changes in last 5 minutes

`:lat 15s`
Redo all changes in last 15 seconds

`:earlier 3f`
Undo last three file states (last three buffer writes)

## Undo branches
> Vim has undo branches like a tree
> To explore every possible text state, you can do it by repeating `g-` and `g+`

## Persistent Undo
> Vim can have persistent undo between sessions, it is enabled with `set undofile`
> It is recommended that a location for the undo cache is specified, it can be done with `set undodir=<dir>`

---

# Do you speak Vim?

## Vim Language Elements

### Verbs
`x`
Delete character under the cursor to the right

`X`
Delete character under the cursor to the left

`r`
Replace character under the cursor with another character

`s`
Delete character under the cursor and enter the Insert mode

`y`
Yank (copy)

`c`
Change

`d`
Delete

`v`
Visually select

### Modifiers
> In Vim, modifiers are used right before nouns, so you can describe how you want to influence the nouns

`i`
Inner (**i**nside)

`a`
Around

`NUM`
Number (e.g.: 1,2,10)

`t`
Searches for something and stops before ir (search un**t**il)

`f`
Searches for that thing and lands on it (**f**ind)

`/`
Find a string (literal or regular expression)

### Nouns
> In English, nouns can be objects you do something to. It's the same in Vim.

`w,W`
Start of next word or WORD

`b,B`
Start of previous word or WORD (start of word **b**efore)

`e,E`
End of word or WORD

`s`
Sentence

`p`
Paragraph

`t`
Tag (in context of HTML/XML)

`b`
Block (in context of programming)

`h,j.k,l`
Left, down, up, right

`$`
End of line

`^,0`
Start of line

> These can be expanded and give you even more power

`aw`
**a** (complete) **w**ord

`as`
**a** (complete) **s**entence 

`ap`
**a** (complete) **p**aragraph

`iw`
**I**nner **w**ord

`is`
**I**nner **s**entence

`ip`
**I**nner **p**aragraph

### Learn to talk to Vim

`dw`
Delete word under cursor

`cis`
Change current sentence

`ci"`
Change a string inside quotes

`c/hello`
Change until next occurrence of 'hello'

`ctY`
Change everything from here to the letter Y (**c**hange un**t**il Y)

`vap`
Visually select this paragraph (**v**isual **a**round **p**aragraph)

## The "dot" command
> The `.` command lets you repeat the last **change** command executed, this means that movement command are never taken by this command

---

# Substitution
> `s` stands for `substitution`

## Ranges
> For most Vim commands, the default range is the current line

`:s/bad/good/g`
Changes all words `bad` to `good` in the current line

`:6,11s/bad/good/g`
Makes the same change, but in lines 6 to 11, including 6 and 11

`:%s/bad/good/g`
Makes the same change in entire file

`:'<,'>/helo/hello/g`
Replacement inside visual selection

## Search and replace
> The command for text substitution in Vim can be defined like:
> :[range] s[substitute]/patter/string/[flags] [count]
> Everything enclosed in [] is optional

Substitution flags can be:
- c: to **c**onfirm each substitution
- g: to replace all occurrences in the line
- i: ignore case for the pattern
- I: don't ignore case for the pattern

### Replace only the whole words
> For a sentences such as `This sentence is short`, if we execute `:s/is/was/g` we would get `Thwas sentence was short`.
>  Instead, to replace whole words we would do `:s/\<is\>/was/g`, this way we would get `This sentence was short`

### Replace either `string1` or `string2` with a new word
> Doing `:s/\(pretty\|good\)/awesome/g` for `That pretty girl did good on the test` would yield: `That awesome girl did awesome on the test`
> `|` is "logical OR"

## Search through multiple files
`:vimgrep warning \*.md`
Will search for the string `warning` in all markdown files in the current directory

`:cn`
Jump to the next match

`:cN`
Jump to the previous match

`:clist`
View all the files that contain the matched string

`:cc number`
Jump to specific match number, which you get from :clist output

> To search recursively you can do `:vimgrep error **/*.log`

## Match that string
> If you want to highlight all matches of a string in your current buffer, you can use the `:match` command.

`:match ErrorMsg /Error/`
Highlights all occurrences of string `Error` in a red color (depends on the color scheme)

> Predefined colors you can use:
> - ErrorMsg
> - WarningMsg
> - ModeMsg
> - MoreMsg

## The power of the global command
`:[range]g/pattern/cmd`
> `cmd` is the Ex command to be executed for each line matching the `pattern`

`:g/error/d`
Deletes all lines in a current file which contains the string `error`

`:g!/important/d`
Deletes all lines BUT the ones with the string `important`

`:g/^\s*$/d`
Deletes all blank lines
> The delete command copies anything that it deletes into a register, therefore to speedup the deletion you can use the 'blackhole' register `_`
> `:g/pattern/d_`

## Execute macros with the global command
> Supposing you have a macro recorded on register `a`, you can do
> `:g/vim/normal @a`
> Executes macro `a` in normal mode for lines that match `vim`

## Copy and Move lines using :g
You can copy/move a *range* to any position in the file
- Copy `:[range]t20` - copies the range to line 20 of the file
- Move `:[range]m20` - moves the range to line 20 of the file

> Example:
> `:m$`
> Moves the current line to the end of the file

`:g/good/s/bad/ugly/g`
For every line containing "good" substitute all "bad" with "ugly"

`:g/^/m0`
Reverse all the lines

---

# Registers
There are 9 types of registers
- The unnamed register ""
- "0 to "9
- The small delete register "-
- "a to "z or "A to "Z
- Four read-only registers ":, "., "%, and "#
- The expression register "=
- The selection and drop registers `"*`, "+, and "~
- The black hole register "_
- Last search pattern register "/

> Vim saves your last yank in the 0 register automatically

---

# Buffers

`:ls`
:buffers
List the buffers

`:5b`
:buffer 5
Select buffer 5 (based on list from :ls)

`:ball`
To open all of the buffers in windows

`:bd`
Delete current buffer

`:bprevious `
`:bnext `
Iterate over each buffer

---

# Windows, Tabs and Sessions

## Split Windows
`:sp[lit] [second_file.txt]`
Opens file as a horizontal split

`:vs[plit] [second_file.txt]`
Opens file as a vertical split

`:20sp third_file.txt`
The numerical value for vertical splits represents the character width of the column

### Switching windows
Ctrl-w h - Switch to the window to the left
Ctrl-w j - Switch to the window below
Ctrl-w k - Switch to the window above
Ctrl-w l - Switch to the window to the right

> This can be changed with this configuration
> nnoremap `<C-H> <C-W><C-H>`
> nnoremap `<C-J> <C-W><C-J>`
> nnoremap `<C-K> <C-W><C-K>`
> nnoremap `<C-L> <C-W><C-L>`

### Moving windows
Ctrl-w r - Rotate the windows from left to right (only if they are split vertically)
Ctrl-w R - Rotate the windows from right to left (only if they are split vertically)
Ctrl-w H - Move current window to the far left and use the full height of the screen
Ctrl-w J - Move current window to the far bottom and use the full width of the screen

### Resizing windows
Ctrl-w = - Resize the windows equally
Ctrl-w > - Incrementally increase the window to the right (takes a parameter: Ctrl-w 10 >)
Ctrl-w < - Incrementally increase the window to the left (or Ctrl-w 10 <)
Ctrl-w - - Incrementally decrease the window's height (or Ctrl-w 5 -)
Ctrl-w + - Incrementally increase the window's height (or Ctrl-w 5 +)

> If you have a few splits open, but only want one window in focus, you can use the Ex command `:on[ly]`

## Sessions
If you use split windows and tabs a lot in your workflow, sessions are a great way to save the position of your windows and tabs once you're done with work. When you come back to work and start up Vim, it's a very fast and easy way to restore the previous session.

`:mksession ~/mysession.vim`
Saves session into file

`:source ~/mysession.vim`
Loads session from file

---

# Macros
To save and use a macro:
1. Start recording actions into register `a`: `qa`
2. Press `q` to stop recording
3. Execute recording by `@a`
4. To repeat last executed macro, run `@@`

## Editing a macro
1. Insert macro on an empty line with `"<register>p` e.g. `"mp`
2. Edit macro
3. Copy macro into the correct register. Move to the beginning of line and run `"my$`

## Recursive macros
Example "Put quotes from current line to last line":
`qaI" <Esc> A" <Esc> j@aq`

> To empty a register, execute `q<register>q` e.g. `qaq`

**Exercise: Execute with this example**

mastering
vim
quickly
wtf
omg
.
in
.
no time

## More examples
`:6,16norm @v`
Execute the macro stored in register `v` on lines 6 through 16

`:10,$norm @i`
Execute the macro stored in register `i` on lines 10 through the end of the file

`:%norm @m`
Execute the macro stored in register `m` on all lines

`:g/pattern/norm @o`
Execute the macro stored in register `o` on all lines matching pattern

`:'<,'>norm @a`
Execute the macro on visually selected lines

`100@a`
Execute the macro in register `a` to the next 100 lines, if macro itself moves to the next line

`.,+99norm @a`
Execute the macro in register `a` to the next 100 lines, if macro itself **doesn't** move to the next line

---

# The power of Visual Modes

> Running command `gv` in Normal mode will re-select the previous visual selection. This is handy when you're performing a search and replace on a visual selection and don't match the substitution quite right on the first try

## Extend a current visual selection
> If you have selected from lines 10 to 20, but want to select 8 to 22, you can go down 2 lines more and then hit `o` to invert the direction of the selection, and then select the 2 lines before line 10.

## Run commands across selection
Example:

`
my $a
my $b
my $c
`

> You can visually select all 3 lines using Shift-v and then run command:
> `:normal A;` and it will yield

`
my $a;
my $b;
my $c;
`

## The dot command in Visual mode
The dot command can repeat the last executed command, it can be done also to execute in each line of the current selection
e.g.
1. `A; <Esc>`
2. Select lines
3. `:normal .`

> This can be done faster by adding into .vimrc:
> `vnoremap . :normal.<CR>`

## Move visual selection
> You made a selection, and you want to move it by a couple of lines up or down, instead of copy-paste, you can add this into your .vimrc:

> " Move visual selection
> vnoremap J :m '>+1<CR>gv=gv
> vnoremap K :m '<-2<CR>gv=gv

## Visual mode possibilities
> You can check `:help visual-operators` for more information

---

# Mappings
For normal mode:
`:nmap v :version<cr>`
Will open version info every time you hit `v`

`:nunmap v`
Will remove the mapping that was assigned

> **Important**: The `nmap` command is recursive. Meaning that it will call itself if it is calling the shortcut from the mapping definition.

|Recursive	|Non-recursive	|Unmap	    |Modes      |
|-----------|---------------|-----------|-----------|
|:map	    |:noremap	    |:unmap	    |normal, visual, operator-pending|
|:nmap	    |:nnoremap	    |:nunmap    |normal     |
|:xmap	    |:xnoremap	    |:xunmap    |visual     |
|:imap	    |:inoremap	    |:iunmap    |insert     |
|:cmap	    |:cnoremap	    |:cunmap    |command-line|
|:omap	    |:onoremap	    |:ounmap    |operator-pending|

> If you want to preview your current mappings for Normal mode, just run `:nmap` command.
> Example: `:nmap n`
> Will show mapping for letter `n`

In order to disable a standard mapping, you need to map it to the special `<nop>` character like: `:noremap <left> <nop>`. This command disables left arrow key.

---

# Folding
