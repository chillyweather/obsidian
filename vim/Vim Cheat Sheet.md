[

Sponsor ![Warp logo](/images/svg/warp-logo.svg)

A new terminal focused on developer productivity

](https://www.warp.dev/)[](https://www.warp.dev/)

# [Vim Cheat Sheet](https://vim.rtorr.com/)

## Global

- <kbd>:h[elp] keyword</kbd> - open help for keyword
- <kbd>:sav[eas] file</kbd> - save file as
- <kbd>:clo[se]</kbd> - close current pane
- <kbd>:ter[minal]</kbd> - open a terminal window
- <kbd>K</kbd> - open man page for word under the cursor

**Tip** Run <kbd>vimtutor</kbd> in a terminal to learn the first Vim commands.

## Cursor movement

- <kbd>h</kbd> - move cursor left
- <kbd>j</kbd> - move cursor down
- <kbd>k</kbd> - move cursor up
- <kbd>l</kbd> - move cursor right
- <kbd>gj</kbd> - move cursor down (multi-line text)
- <kbd>gk</kbd> - move cursor up (multi-line text)
- <kbd>H</kbd> - move to top of screen
- <kbd>M</kbd> - move to middle of screen
- <kbd>L</kbd> - move to bottom of screen
- <kbd>w</kbd> - jump forwards to the start of a word
- <kbd>W</kbd> - jump forwards to the start of a word (words can contain punctuation)
- <kbd>e</kbd> - jump forwards to the end of a word
- <kbd>E</kbd> - jump forwards to the end of a word (words can contain punctuation)
- <kbd>b</kbd> - jump backwards to the start of a word
- <kbd>B</kbd> - jump backwards to the start of a word (words can contain punctuation)
- <kbd>ge</kbd> - jump backwards to the end of a word
- <kbd>gE</kbd> - jump backwards to the end of a word (words can contain punctuation)
- <kbd>%</kbd> - move cursor to matching character (default supported pairs: '()', '{}', '\[\]' - use `:h matchpairs` in vim for more info)
- <kbd>0</kbd> - jump to the start of the line
- <kbd>^</kbd> - jump to the first non-blank character of the line
- <kbd>$</kbd> - jump to the end of the line
- <kbd>g_</kbd> - jump to the last non-blank character of the line
- <kbd>gg</kbd> - go to the first line of the document
- <kbd>G</kbd> - go to the last line of the document
- <kbd>5gg</kbd> or <kbd>5G</kbd> - go to line 5
- <kbd>gd</kbd> - move to local declaration
- <kbd>gD</kbd> - move to global declaration
- <kbd>fx</kbd> - jump to next occurrence of character x
- <kbd>tx</kbd> - jump to before next occurrence of character x
- <kbd>Fx</kbd> - jump to the previous occurrence of character x
- <kbd>Tx</kbd> - jump to after previous occurrence of character x
- <kbd>;</kbd> - repeat previous f, t, F or T movement
- <kbd>,</kbd> - repeat previous f, t, F or T movement, backwards
- <kbd>}</kbd> - jump to next paragraph (or function/block, when editing code)
- <kbd>{</kbd> - jump to previous paragraph (or function/block, when editing code)
- <kbd>zz</kbd> - center cursor on screen
- <kbd>zt</kbd> - position cursor on top of the screen
- <kbd>zb</kbd> - position cursor on bottom of the screen
- <kbd>Ctrl</kbd> + <kbd>e</kbd> - move screen down one line (without moving cursor)
- <kbd>Ctrl</kbd> + <kbd>y</kbd> - move screen up one line (without moving cursor)
- <kbd>Ctrl</kbd> + <kbd>b</kbd> - move screen up one page (cursor to last line)
- <kbd>Ctrl</kbd> + <kbd>f</kbd> - move screen down one page (cursor to first line)
- <kbd>Ctrl</kbd> + <kbd>d</kbd> - move cursor and screen down 1/2 page
- <kbd>Ctrl</kbd> + <kbd>u</kbd> - move cursor and screen up 1/2 page

**Tip** Prefix a cursor movement command with a number to repeat it. For example, <kbd>4j</kbd> moves down 4 lines.

## Insert mode - inserting/appending text

- <kbd>i</kbd> - insert before the cursor
- <kbd>I</kbd> - insert at the beginning of the line
- <kbd>a</kbd> - insert (append) after the cursor
- <kbd>A</kbd> - insert (append) at the end of the line
- <kbd>o</kbd> - append (open) a new line below the current line
- <kbd>O</kbd> - append (open) a new line above the current line
- <kbd>ea</kbd> - insert (append) at the end of the word
- <kbd>Ctrl</kbd> + <kbd>h</kbd> - delete the character before the cursor during insert mode
- <kbd>Ctrl</kbd> + <kbd>w</kbd> - delete word before the cursor during insert mode
- <kbd>Ctrl</kbd> + <kbd>j</kbd> - add a line break at the cursor position during insert mode
- <kbd>Ctrl</kbd> + <kbd>t</kbd> - indent (move right) line one shiftwidth during insert mode
- <kbd>Ctrl</kbd> + <kbd>d</kbd> - de-indent (move left) line one shiftwidth during insert mode
- <kbd>Ctrl</kbd> + <kbd>n</kbd> - insert (auto-complete) next match before the cursor during insert mode
- <kbd>Ctrl</kbd> + <kbd>p</kbd> - insert (auto-complete) previous match before the cursor during insert mode
- <kbd>Ctrl</kbd> + <kbd>rx</kbd> - insert the contents of register x
- <kbd>Ctrl</kbd> + <kbd>ox</kbd> - Temporarily enter normal mode to issue one normal-mode command x.
- <kbd>Esc</kbd> or <kbd>Ctrl</kbd> + <kbd>c</kbd> - exit insert mode

## Editing

- <kbd>r</kbd> - replace a single character.
- <kbd>R</kbd> - replace more than one character, until <kbd>ESC</kbd> is pressed.
- <kbd>J</kbd> - join line below to the current one with one space in between
- <kbd>gJ</kbd> - join line below to the current one without space in between
- <kbd>gwip</kbd> - reflow paragraph
- <kbd>g~</kbd> - switch case up to motion
- <kbd>gu</kbd> - change to lowercase up to motion
- <kbd>gU</kbd> - change to uppercase up to motion
- <kbd>cc</kbd> - change (replace) entire line
- <kbd>c$</kbd> or <kbd>C</kbd> - change (replace) to the end of the line
- <kbd>ciw</kbd> - change (replace) entire word
- <kbd>cw</kbd> or <kbd>ce</kbd> - change (replace) to the end of the word
- <kbd>s</kbd> - delete character and substitute text (same as cl)
- <kbd>S</kbd> - delete line and substitute text (same as cc)
- <kbd>xp</kbd> - transpose two letters (delete and paste)
- <kbd>u</kbd> - undo
- <kbd>U</kbd> - restore (undo) last changed line
- <kbd>Ctrl</kbd> + <kbd>r</kbd> - redo
- <kbd>.</kbd> - repeat last command

## Marking text (visual mode)

- <kbd>v</kbd> - start visual mode, mark lines, then do a command (like y-yank)
- <kbd>V</kbd> - start linewise visual mode
- <kbd>o</kbd> - move to other end of marked area
- <kbd>Ctrl</kbd> + <kbd>v</kbd> - start visual block mode
- <kbd>O</kbd> - move to other corner of block
- <kbd>aw</kbd> - mark a word
- <kbd>ab</kbd> - a block with ()
- <kbd>aB</kbd> - a block with {}
- <kbd>at</kbd> - a block with <> tags
- <kbd>ib</kbd> - inner block with ()
- <kbd>iB</kbd> - inner block with {}
- <kbd>it</kbd> - inner block with <> tags
- <kbd>Esc</kbd> or <kbd>Ctrl</kbd> + <kbd>c</kbd> - exit visual mode

**Tip** Instead of <kbd>b</kbd> or <kbd>B</kbd> one can also use <kbd>(</kbd> or <kbd>{</kbd> respectively.

## Visual commands

- <kbd>&gt;</kbd> - shift text right
- <kbd>&lt;</kbd> - shift text left
- <kbd>y</kbd> - yank (copy) marked text
- <kbd>d</kbd> - delete marked text
- <kbd>~</kbd> - switch case
- <kbd>u</kbd> - change marked text to lowercase
- <kbd>U</kbd> - change marked text to uppercase

## Registers

- <kbd>:reg[isters]</kbd> - show registers content
- <kbd>"xy</kbd> - yank into register x
- <kbd>"xp</kbd> - paste contents of register x
- <kbd>"+y</kbd> - yank into the system clipboard register
- <kbd>"+p</kbd> - paste from the system clipboard register

**Tip** Registers are being stored in ~/.viminfo, and will be loaded again on next restart of vim.

**Tip** Special registers:

 <kbd>0</kbd> - last yank  
 <kbd>"</kbd> - unnamed register, last delete or yank  
 <kbd>%</kbd> - current file name  
 <kbd>#</kbd> - alternate file name  
 <kbd>*</kbd> - clipboard contents (X11 primary)  
 <kbd>+</kbd> - clipboard contents (X11 clipboard)  
 <kbd>/</kbd> - last search pattern  
 <kbd>:</kbd> - last command-line  
 <kbd>.</kbd> - last inserted text  
 <kbd>-</kbd> - last small (less than a line) delete  
 <kbd>=</kbd> - expression register  
 <kbd>_</kbd> - black hole register  

## Marks and positions

- <kbd>:marks</kbd> - list of marks
- <kbd>ma</kbd> - set current position for mark A
- <kbd>`a</kbd> - jump to position of mark A
- <kbd>y`a</kbd> - yank text to position of mark A
- <kbd>`0</kbd> - go to the position where Vim was previously exited
- <kbd>`"</kbd> - go to the position when last editing this file
- <kbd>`.</kbd> - go to the position of the last change in this file
- <kbd>``</kbd> - go to the position before the last jump
- <kbd>:ju[mps]</kbd> - list of jumps
- <kbd>Ctrl</kbd> + <kbd>i</kbd> - go to newer position in jump list
- <kbd>Ctrl</kbd> + <kbd>o</kbd> - go to older position in jump list
- <kbd>:changes</kbd> - list of changes
- <kbd>g,</kbd> - go to newer position in change list
- <kbd>g;</kbd> - go to older position in change list
- <kbd>Ctrl</kbd> + <kbd>]</kbd> - jump to the tag under cursor

**Tip** To jump to a mark you can either use a backtick (<kbd>`</kbd>) or an apostrophe (<kbd>'</kbd>). Using an apostrophe jumps to the beginning (first non-blank) of the line holding the mark.

## Macros

- <kbd>qa</kbd> - record macro a
- <kbd>q</kbd> - stop recording macro
- <kbd>@a</kbd> - run macro a
- <kbd>@@</kbd> - rerun last run macro

## Cut and paste

- <kbd>yy</kbd> - yank (copy) a line
- <kbd>2yy</kbd> - yank (copy) 2 lines
- <kbd>yw</kbd> - yank (copy) the characters of the word from the cursor position to the start of the next word
- <kbd>yiw</kbd> - yank (copy) word under the cursor
- <kbd>yaw</kbd> - yank (copy) word under the cursor and the space after or before it
- <kbd>y$</kbd> or <kbd>Y</kbd> - yank (copy) to end of line
- <kbd>p</kbd> - put (paste) the clipboard after cursor
- <kbd>P</kbd> - put (paste) before cursor
- <kbd>gp</kbd> - put (paste) the clipboard after cursor and leave cursor after the new text
- <kbd>gP</kbd> - put (paste) before cursor and leave cursor after the new text
- <kbd>dd</kbd> - delete (cut) a line
- <kbd>2dd</kbd> - delete (cut) 2 lines
- <kbd>dw</kbd> - delete (cut) the characters of the word from the cursor position to the start of the next word
- <kbd>diw</kbd> - delete (cut) word under the cursor
- <kbd>daw</kbd> - delete (cut) word under the cursor and the space after or before it
- <kbd>:3,5d</kbd> - delete lines starting from 3 to 5

**Tip** You can also use the following characters to specify the range:  
e.g.  

<kbd>:.,$d</kbd> - From the current line to the end of the file  
<kbd>:.,1d</kbd> - From the current line to the beginning of the file  
<kbd>:10,$d</kbd> - From the 10th line to the beginning of the file  

- <kbd>:g/{pattern}/d</kbd> - delete all lines containing pattern
- <kbd>:g!/{pattern}/d</kbd> - delete all lines not containing pattern
- <kbd>d$</kbd> or <kbd>D</kbd> - delete (cut) to the end of the line
- <kbd>x</kbd> - delete (cut) character

## Indent text

- <kbd>&gt;&gt;</kbd> - indent (move right) line one shiftwidth
- <kbd>&lt;&lt;</kbd> - de-indent (move left) line one shiftwidth
- <kbd>&gt;%</kbd> - indent a block with () or {} (cursor on brace)
- <kbd>&lt;%</kbd> - de-indent a block with () or {} (cursor on brace)
- <kbd>&gt;ib</kbd> - indent inner block with ()
- <kbd>&gt;at</kbd> - indent a block with <> tags
- <kbd>3==</kbd> - re-indent 3 lines
- <kbd>=%</kbd> - re-indent a block with () or {} (cursor on brace)
- <kbd>=iB</kbd> - re-indent inner block with {}
- <kbd>gg=G</kbd> - re-indent entire buffer
- <kbd>]p</kbd> - paste and adjust indent to current line

## Exiting

- <kbd>:w</kbd> - write (save) the file, but don't exit
- <kbd>:w !sudo tee %</kbd> - write out the current file using sudo
- <kbd>:wq</kbd> or <kbd>:x</kbd> or <kbd>ZZ</kbd> - write (save) and quit
- <kbd>:q</kbd> - quit (fails if there are unsaved changes)
- <kbd>:q!</kbd> or <kbd>ZQ</kbd> - quit and throw away unsaved changes
- <kbd>:wqa</kbd> - write (save) and quit on all tabs

## Search and replace

- <kbd>/pattern</kbd> - search for pattern
- <kbd>?pattern</kbd> - search backward for pattern
- <kbd>\vpattern</kbd> - 'very magic' pattern: non-alphanumeric characters are interpreted as special regex symbols (no escaping needed)
- <kbd>n</kbd> - repeat search in same direction
- <kbd>N</kbd> - repeat search in opposite direction
- <kbd>:%s/old/new/g</kbd> - replace all old with new throughout file
- <kbd>:%s/old/new/gc</kbd> - replace all old with new throughout file with confirmations
- <kbd>:noh[lsearch]</kbd> - remove highlighting of search matches

## Search in multiple files

- <kbd>:vim[grep] /pattern/ {`{file}`}</kbd> - search for pattern in multiple files

e.g. <kbd>:vim[grep] /foo/ **/*</kbd>

- <kbd>:cn[ext]</kbd> - jump to the next match
- <kbd>:cp[revious]</kbd> - jump to the previous match
- <kbd>:cope[n]</kbd> - open a window containing the list of matches
- <kbd>:ccl[ose]</kbd> - close the quickfix window

## Tabs

- <kbd>:tabnew</kbd> or <kbd>:tabnew {page.words.file}</kbd> - open a file in a new tab
- <kbd>Ctrl</kbd> + <kbd>wT</kbd> - move the current split window into its own tab
- <kbd>gt</kbd> or <kbd>:tabn[ext]</kbd> - move to the next tab
- <kbd>gT</kbd> or <kbd>:tabp[revious]</kbd> - move to the previous tab
- <kbd>#gt</kbd> - move to tab number #
- <kbd>:tabm[ove] #</kbd> - move current tab to the #th position (indexed from 0)
- <kbd>:tabc[lose]</kbd> - close the current tab and all its windows
- <kbd>:tabo[nly]</kbd> - close all tabs except for the current one
- <kbd>:tabdo</kbd> command - run the `command` on all tabs (e.g. `:tabdo q` - closes all opened tabs)

## Working with multiple files

- <kbd>:e[dit] file</kbd> - edit a file in a new buffer
- <kbd>:bn[ext]</kbd> - go to the next buffer
- <kbd>:bp[revious]</kbd> - go to the previous buffer
- <kbd>:bd[elete]</kbd> - delete a buffer (close a file)
- <kbd>:b[uffer]#</kbd> - go to a buffer by index #
- <kbd>:b[uffer] file</kbd> - go to a buffer by file
- <kbd>:ls</kbd> or <kbd>:buffers</kbd> - list all open buffers
- <kbd>:sp[lit] file</kbd> - open a file in a new buffer and split window
- <kbd>:vs[plit] file</kbd> - open a file in a new buffer and vertically split window
- <kbd>:vert[ical] ba[ll]</kbd> - edit all buffers as vertical windows
- <kbd>:tab ba[ll]</kbd> - edit all buffers as tabs
- <kbd>Ctrl</kbd> + <kbd>ws</kbd> - split window
- <kbd>Ctrl</kbd> + <kbd>wv</kbd> - split window vertically
- <kbd>Ctrl</kbd> + <kbd>ww</kbd> - switch windows
- <kbd>Ctrl</kbd> + <kbd>wq</kbd> - quit a window
- <kbd>Ctrl</kbd> + <kbd>wx</kbd> - exchange current window with next one
- <kbd>Ctrl</kbd> + <kbd>w=</kbd> - make all windows equal height & width
- <kbd>Ctrl</kbd> + <kbd>wh</kbd> - move cursor to the left window (vertical split)
- <kbd>Ctrl</kbd> + <kbd>wl</kbd> - move cursor to the right window (vertical split)
- <kbd>Ctrl</kbd> + <kbd>wj</kbd> - move cursor to the window below (horizontal split)
- <kbd>Ctrl</kbd> + <kbd>wk</kbd> - move cursor to the window above (horizontal split)
- <kbd>Ctrl</kbd> + <kbd>wH</kbd> - make current window full height at far left (leftmost vertical window)
- <kbd>Ctrl</kbd> + <kbd>wL</kbd> - make current window full height at far right (rightmost vertical window)
- <kbd>Ctrl</kbd> + <kbd>wJ</kbd> - make current window full width at the very bottom (bottommost horizontal window)
- <kbd>Ctrl</kbd> + <kbd>wK</kbd> - make current window full width at the very top (topmost horizontal window)

## Diff

- <kbd>zf</kbd> - manually define a fold up to motion
- <kbd>zd</kbd> - delete fold under the cursor
- <kbd>za</kbd> - toggle fold under the cursor
- <kbd>zo</kbd> - open fold under the cursor
- <kbd>zc</kbd> - close fold under the cursor
- <kbd>zr</kbd> - reduce (open) all folds by one level
- <kbd>zm</kbd> - fold more (close) all folds by one level
- <kbd>zi</kbd> - toggle folding functionality
- <kbd>]c</kbd> - jump to start of next change
- <kbd>[c</kbd> - jump to start of previous change
- <kbd>do</kbd> or <kbd>:diffg[et]</kbd> - obtain (get) difference (from other buffer)
- <kbd>dp</kbd> or <kbd>:diffpu[t]</kbd> - put difference (to other buffer)
- <kbd>:diffthis</kbd> - make current window part of diff
- <kbd>:dif[fupdate]</kbd> - update differences
- <kbd>:diffo[ff]</kbd> - switch off diff mode for current window

**Tip** The commands for folding (e.g. <kbd>za</kbd>) operate on one level. To operate on all levels, use uppercase letters (e.g. <kbd>zA</kbd>).

**Tip** To view the differences of files, one can directly start Vim in diff mode by running <kbd>vimdiff</kbd> in a terminal. One can even set this as <kbd>git difftool</kbd>.

### More resources

Interactive Vim tutorial: [Open Vim](https://openvim.com/)

Vim quick reference from Vim help pages: [quickref.txt](https://vimhelp.org/quickref.txt.html)

List of all Vim ex (<kbd>:</kbd>) commands: [ex-cmd-index](https://vimhelp.org/index.txt.html#ex-cmd-index)

Checkout the source on [Github](https://github.com/rtorr/vim-cheat-sheet)

version: 3.2.0