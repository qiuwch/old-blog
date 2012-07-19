---
layout: post
title: "Difference between cygwin and mingw"
date: 2012-06-29 10:44
comments: true
categories: 
---
This is not very related to the topic of this blog. But I often came across with problem to distinguish those two, so I left the anwser here for reference.

This answer is from [stackoverflow](http://stackoverflow.com/questions/771756/what-is-the-difference-between-cygwin-and-mingw)

> cygwin is an attempt to create a complete UNIX/POSIX environment on Windows. To do this it uses various DLLs that unfortunately have a user-unfriendly license. MinGW is a C/C++ compiler suite which allows you to create Windows executables without dependancy on such DLLs - you only need the normal MSVC runtimes.
> 
> You can also get a small UNIX/POSIX like environment, compiled with MinGW called MSYS. It doesn't have anywhere near all the features of Cygwin, but is ideal for programmers wanting to use MinGW.

An alternative answer
> Fairly simple:
> 
> Compile something in Cygwin and you are compiling it for Cygwin.
> Compile something in MingW and you are compiling it for Windows.
> Cygwin is good when your app absolutely needs a POSIX environment to run - it is sometimes easier to port something to Cygwin than it is to port it to Windows, because Cygwin is a layer on top of Windows that emulates a POSIX environment. If you compile something for Cygwin then it will need to be run within the Cygwin environment, as provided by cygwin1.dll. For portability, you could distribute this dll with your project, if you were willing to comply with the relevant license.
> 
> MingW is a Windows port of the GNU compiler tools, like GCC, Make, Bash, etc, which run directly in Windows without any emulation layer. By default it will compile to a native Win32 target, complete with .exe and .dll files, though you could also cross-compile with the right settings. It is an alternative to Microsoft Visual C compiler and its associated linking/make tools in a way.


In conclusion:

* cygwin emulates posix system
* mingw compiles linux code in windows


Update
======

After comparsion, I choose cygwin for the posix-like system for server.

Which I needed for server is rsync and git.

cygwin maybe slower than mingw, but it provides a package management system, which is really handy.

This is some usefull link for cygwin

* [apt-cyg](http://fir3net.com/Cygwin/cygwin-package-installation.html)

Basic requirement for apt-cyg to work is  
`setup.exe -q -P  wget,tar,qawk,bzip2,subversion,vim`

plus

* git
* openssh
* rsync

Openssh config
--------------
After installation of openssh, should run `ssh-host-config` to config sshd service. After configuration, run `net start sshd` to start ssh service.

rsync config and tutorial
-------------------------
Rsync is especially useful when I want to keep the three servers be in the same state.

Here is a [tutorial](http://everythinglinux.org/rsync/)
