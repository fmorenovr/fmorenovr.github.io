---
layout: page
subtitle: "New Features for developers in Fedora 26"
description: "new packages and new compilers for Fedora 26 for us !!"
permalink: /pages/fedora_newfeatures
---
### Fedora Workstation 26

Here I comment about new compilers, packages, languages, etc for developers who could download and configure a latest environment.

You can get Fedora 26 Workstation pressing [here](https://getfedora.org/es/workstation/download/).  In my case, I try on a Virtual Machine using virt-manager.

Here is a little view of Fedora 26:

![Fedora](/pages/fedora/fedora_26.png)

## GCC7
Is the compiler for C language.  
Switch GCC in Fedora 26 to 7.x.y. you can rebuild all packages with it, or optionally rebuild just some packages with it.

![GCC](/pages/fedora/gcc_7.png)

## Parallel Installable Debuginfo
Fedora 26 presente a debuginfo packages that can be installed in parallel to make it easier to trace, profile and observe what programs are doing or to debug when they have an error.

## Golang 1.8
The Go Programming language develop and released by Google, Fedora 26 now have a rebase of Golang package to upcoming version 1.8, including rebuild of all dependent packages.  
How install:

    sudo dnf install go

![Go](/pages/fedora/gcc_7.png)

## Ruby 2.4
Fedora 26 have the latest stable version of Ruby. Ruby 2.4 have many new features, thie version include improvements for the increasingly diverse and expanding demands for Ruby.  
Ruby was updated from 2.3 in Fedora 24 to Ruby 2.4 in Fedora 26.  
How install:

    sudo dnf group install "C Development Tools and Libraries"
    sudo dnf install ruby-devel zlib-devel

![Ruby](/pages/fedora/ruby_24.png)

## Fedora 26 C/C++ Compilation Flags Updates
Fedora 26 updates his own default C/C++ compilation flags.

## Python 3.6
The system Python 3 stack has been upgraded to Python 3.6.1, and includes a backport of Python 3.7's C locale coercion feature (where the ASCII-based C locale is replaced with C.UTF-8 at interpreter startup, which is expected to significantly reduce the occurrence of unwanted Unicode encoding and decoding errors).

![python](/pages/fedora/python_36.png)
