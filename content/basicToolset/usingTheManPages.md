---
title: "Finding Help In Linux"
date: 2023-03-15T09:50:48-03:00
draft: false
---

One of the nicest things about Linux is that it is largely self-documented.  If someone is familiar with all the ways to find help within Linux (assuming sufficient patience and time), its very likely that the operating system itself will provide the answers.

## The Manual Pages

The first and best place to begin looking for help within Linux is the `man` pages (short for manual).  For any command, simply type `man <command>` and a a manual page containing lots of useful information will appear!

Running this command:
``` bash
man lvcreate
```

Results in:
![man lvcreate](/images/manLVCreate.png)

The resulting page is searchable using forward slash `/` - similar to `vim`.  To exit a `man` page, simply press `q`.

## The Common Syntax of Man Pages

Manual pages are laid out in a specific and common format.  Here are a few highlights:
- A common convention in Linux, optional items are surrounded by square brackets - `[option]`
- Items that are mutually exclusive (users must choose one or the other) are surrounded by curly braces and separated by "or" pipes - {h|H}
- If multiple options are possible, an elipsis is used - `. . .`
- Some commands will have examples close to the end of their manual page, especially more complex commands

## Manual Page Sections
Manual pages are divided into several different sections:

``` bash
    1   Executable programs or shell commands
    2   System calls (functions provided by the kernel)
    3   Library calls (functions within program libraries)
    4   Special files (usually found in /dev)
    5   File formats and conventions, e.g. /etc/passwd
    6   Games
    7   Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7)
    8   System administration commands (usually only for root)
    9   Kernel routines [Non standard]
```

For those beginning to learn about Linux, the sections that are most important are 1 and 8, and occasionally sections 5 and 7.  Sections such as 2 and 3 are used extensively by kernel programmers.
