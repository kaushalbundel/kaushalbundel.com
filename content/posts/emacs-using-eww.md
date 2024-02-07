---
date: '2024-01-16'
title: 'Web Browsing in Emacs - EWW'
description: 'Reference Guide for EWW'
categories: ["Emacs"]
tags: ["Emacs"]
---

In the past few days I have taken a liking to reading article or just browsing web using EWW. EWW is a browser built into Emacs. 

My intention to browse web using EWW is derived from the fact that:
- EWW is text based: Being text based is actually a good thing. It means that I am focused on the content only and I can channel my energies onto the task at hand.
- EWW is built in Emacs: This means that I can minimize context switching. If I need to create a note as I am reading an article *org-capture* is nearby. If I find some website that I like to re-visit and it offers rss services then Elfeed is available just at the tap of fingers.
- EWW offers some very useful builtin variables and functions that makes web-browsing quite enjoyable. 

Here is a collection of my frequently used commands and tricks to use EWW.

(1) Using EWW

      - Open Eww: M-x Eww 
      - Open a new Eww buffer: C-u M-x Eww
      - Quit Eww: q
      - To make the page readable by focusing on the content: R

(2) Copy links 

      - Copy a link inside Eww buffer: w
      - Copy the link of Eww buffer: w
    
(3) Basic Navigation

      - Move to Previous url: l
      - Move to Forward url: r
      - Check Browsing History: H
      - Basic Emacs keybindings work inside EWW buffers
      
(4) Bookmarks

      - Adding a Bookmark: b
      - View Stored Bookmarks: B
      
(5) Misc Config Changes

      - By default the name of the buffer is EWW with a number, this function changes the default to a more sensible buffer name: (setq! eww-auto-rename-buffer 'title')
        
  
