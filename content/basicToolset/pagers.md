---
title: "File Pagers"
date: 2023-03-09T09:38:29-04:00
draft: false 
---

There are several command-line utilities to review the contents of a file in Enterprise Linux.  These include:

1. `more`
   - The most traditional pager in Linux. The user presses "Space" to move through a file using `more`.  Standard search functionality (`/`) works similar to how it does in `man` pages or `vim`
   - Typical Usage:
     - `more myFile.txt`
     - `cat myFile.txt | more` - less efficient but commonly used
     
2. `less`
   - Built to address the shortcomings of `more`, `less` has additional features such as scrolling via arrow keys (as well as "Space") and the same search functionality (`/`).  Generally preferred by most users.
   - Typical Usage:
     - `less myFile.txt`
     - `cat myFile.txt | less` - less efficient but common used

3. `view`
   - A "read-only" mode for the `vim` editor.
   - Has all the same functionality as `vi` or `vim` - users can search the doucment, move the cursor to the beginning/end of lines or the document itself.
   - User can even modify the document, but cannot save it without the `!` flag (and appropriate file permissions of course)
   - Typical Usage:
     - `view myFile.txt`

4. `cat`
   - Most basic way to view a file in CLI
   - Not really a file pager, but used to view short files effectively.  Returns the entire contents of the file to the terminal - so less useful for larger files.
   - Often used in conjunction with pipes - helps to get the entire contents of a file passed to the next command
   - Typical usage:
     - `cat myFile.txt`
     - `cat myFile.txt | grep -v 'notLinesWithThisText'`
 
