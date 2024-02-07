---
date: '2023-09-22'
title: 'Emacs Keybindings'
description: 'Reference Guide for Emacs Keybindings'
categories: ["Emacs"]
tags: ["Emacs"]
---

**Last Update Date: 09/24/2023**

Emacs keybindings  can be complicated. This list of Emacs keybindings consists of most used Emacs commands in my opinion. This list is in no way a comprehensive list and further additions and deletions should be expected in the future. 


(1) Opening Document

      - C-x C-f for find file
      - You can type full path to a file or create a new document.
      - You could also just open the path to a directory and find the file.

(2) For Zoom In/Out 

      - C-x C-+ to zoom in
      - C-x C-- to zoom out
    
(3) Basic Navigation

      - C-n, C-p move up/down line
      - C-f, C-b move forward/back a charcter
      - M-f, M-b forward/back by words
      - C-a, C-e beginning/end of line
      - M-a, M-e backwards/forwards by sentence
      - M-{, M-} backwards/forwards by paragraph
      - M-LESS THAN M-GREATER THAN beginning/end of file
      - M-g g goto line number
      - ESC-number C-n/p/f/b perform motion that number of times
      
(4) Text Manipulation

      - C-space to select text to copy/cut
      - C-w cut highlighted
      - M-w copy highlighted
      - C-y paste
      - C-k cut to end of line?
      - C-x backspace, M-k (backwards/forwards delete the current line)
      - M-z character cuts to that character
      - C-x u undo (alternate to this is C-/)
      - C-h v kill-ring
      - C-x 0 to close the kill-ring window
      - C-y Esc-y to cycle through kill-ring for paste
      - C-x C-; to comment/uncomment block of text
      - ESC-number ESC-d deletes that number of words
      - C-D/ M-D Deletes a  word forwards and backwards
      
(4) Buffers

      - C-x b select another buffer
      - C-x C-b list all buffers
      - C-x k kill a buffer
      
(5) Case change

      - M-c capitalizes a word
      - M-u uppercase word
      - M-l lowercase word
      
(6) Spell Check

      - M-$ check current word
      
(7) Query replace M-% (shift-5)

      - Will only look forward in the file!
      - RET exits the query replace
      
(8) Search (C-s to search)

      - C-s to search forward
      - C-r to search backward
      
(9) Splits

      - C-x 2 Horizontal Split
      - C-x 3 Vertical Split
      - C-x 0 Close window
      - C-x 4f Opens file in other window
      - C-x o moves cursor to next frame
      
(10) Save and Exit

      - C-x C-s Save
      - C-x C-c Quit

