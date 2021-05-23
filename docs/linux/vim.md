---
layout: default
title: vim crash course
nav_order: 4
parent: Linux
---
# Beginning of Vim
[Youtube tutorial](https://www.youtube.com/watch?v=ggSyF1SVFr4)

[Retrospect](https://danielmiessler.com/study/vim/)

## How to exit Vim
1. Press **Esc** to exit the edit mode
2. commands
  - `:q!` - quit without saving
  - `:wq` - save and exit Vim		 

## Copy, cut and paste
[Yank(`y`), cut(`d`) paste(`p`)](https://linuxize.com/post/how-to-copy-cut-paste-in-vim/)

## Frequently used 
1. Vim modes: command mode(esc); insert mode(i)
2. Undo changes from command mode: `u`
3. Redo changes from command mode: `ctrl+r`

## Line operation
  - Delete a single line from command mode: dd
   variations - delete num lines: num dd
  - Jump to certain line from command mode: :line number
  - `gg`: go to the top
  - `G`: go to the bottom 
  - `G o`: go to bottom and type below the last line
  - `G O`: Move within the line
  - `0`: move to the beginning of the line
  - `$`: move to the end of the line
  - `^`: move to the first non-blank character in the line	

## Word operation
  - `w`: move forward one word
  - `b`: move back one word
  - `e`: move to the end of your word
  - Search words: /word. `n`(next) -> search next; `shift+n` -> search previous

## Deleting words in Vim
1. `dw`: delete word from the cursor position to the end of word
2. `diw`: delete inside the word     
3. `dt<char>`: delete from cursor to the specified character 

## Search and replace
`:%s/previous/current/g(greedy)c(confirm)`

