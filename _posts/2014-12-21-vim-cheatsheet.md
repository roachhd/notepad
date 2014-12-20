---
layout: post
title: Vim Cheatsheet
---
## Movement

### By "Word"
 * `w` forward to beginning of the next word
 * `W` forward to beginning of the next word (whitespace separates)
 * `e` forward to end of next word
 * `E` forward to end of next word (whitespace separates)
 * `b` back to beginning of the previous word
 * `B` back to beginning of the previous word (whitespace separates)
 * `ge` back to end of the next word
 * `gE` back to end of the next word (whitespace separates)

### Searching

#### On current line

 * `fn` find and move to the next occurrence of `n`.  You can follow this with a `;` to repeat the find/move.  You can also use `,` to go back one match.
 * `tn` find and move to (un<b>t</b>il) the character *preceding* the next occurrence of `n`.  As above, `;` repeats, and `,` goes back one match.
 * `Fn` find and move to the previous occurrence of `n`.  `;` repeats, `,` goes back one match.
 * `Tn` find and move to (un<b>T</b>il) the character *following* the next occurence of `n`.  `;` repeats, `,` goes back one match.

#### In document

 * `/term` search forwards for `term`
 * `?term` search backwards for `term`

### Combining with other commands
 * `cfn` - <b>c</b>hange the text up to where you <b>f</b>ind the next occurrence of `n`
 * `cFn` - <b>c</b>hange the text back to where you <b>F</b>ind the previous occurrence of `n`

### By page/screen

 * `^f` <b>f</b>orward a page/screen
 * `^b` <b>b</b>ack a page/screen
 * `^u` <b>u</b>p half a page/screen
 * `^d` <b>d</b>own half a page/screen

### Positioning within a page/screen

 * `H` go to <b>H</b>ead (top) or "<b>H</b>igh point" of screen
 * `M` go to <b>M</b>iddle of screen
 * `L` go to <b>L</b>ast line or "<b>L</b>ow point" of screen

### Positioning within a document/file

 * `gg` first line of document
 * `G` last line of document
 * `500G` line 500
 * `*` search forwards for word currently under cursor (use with `n` and `N`)
 * `#` search backward for word currently under cursor (use with `N` and `n` - note that direction is reversed)
 * `%` matching bracket, brace, square bracket - *see matchit.vim for extended behavior*

### Marks

 * `ma` set position of (book)mark `a`
 * `:marks` list currently defined marks
 * `'a` jump to rot for mark `a`
 * ```a` jump to row/column for mark `a`

## Editing

 * `i` insert at cursor
 * `I` insert at beginning of line
 * `a` append after cursor
 * `A` append at end of line
 * `r` replace a single character
 * `R` replace any number of characters
 * `c<motion>` change, e.g. `cw` is change word
 * `x` delete character under cursor
 * `X` delete character before cursor
 * `d<motion>` delete, e.g. `dw` is delete word, `dd` is delete line

## Copy/Cut & Paste

See http://vim.wikia.com/wiki/VimTip386 for more detailed info.

1. press `v` (for visual mode) to start the selection (or `V` to select whole lines, or `Ctrl-v` for a vertical block)
2. move the cursor to where you want the selection to end
3. press `d` for delete (cut) or `y` for yank (copy)
4. position the cursor where you want to paste
5. press `P` or `p` for paste before or after cursor, respectively

## Buffers

For an excellent tutorial, see http://reefpoints.dockyard.com/2013/10/22/vim-buffers.html

* add a buffer: `:badd`
* list open buffers: `:ls`
* switch to alternate (`#`) buffer: `CTRL+6`
* switch to previous buffer: `:bp`
* switch to next buffer: `:bn`
* switch to buffer *x* (where *x* is an integer): `:bx`
* delete (close) current buffer: `:bd`
* delete (close) buffers *x* and *y*: `:bd x y`

## Windows

For another excellent tutorial, see http://reefpoints.dockyard.com/2013/11/27/vim-windows.html

* split current window: `CTRL+w s`
* split current window vertically: `CTRL+w v`
* switch to window to left: `CTRL+w h`
* switch to window to right: `CTRL+w l`
* switch to window above: `CTRL+w k`
* switch to window below: `CTRL+w j`
* rotate windows: `CTRL+w r`
* rotate windows (opposite direction): `CTRL+w R`
* move current window the far left and use the full height of the screen: `CTRL-w H`
* move current window the far bottom and use the full width of the screen: `CTRL-w J`
* move current window the far top and full width of the screen: `CTRL-w K`
* move current window the far right and full height of the screen: `CTRL-w L`
* resize the windows equally : `CTRL-w =`
* incrementally increase the window to the right: `CTRL-w >`
 * takes a parameter, e.g. `CTRL-w 20 >`
* incrementally increase the window to the left: `CTRL-w <`
 * takes a parameter, e.g. `CTRL-w 20 <`
* incrementally decrease the window's height: `CTRL-w -`
 * takes a parameter, e.g. `CTRL-w 10 -`
* incrementally increase the window's height: `CTRL-w +`
 * takes a parameter, e.g. `CTRL-w 10 +`

