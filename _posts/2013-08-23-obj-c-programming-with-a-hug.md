---
layout: post
title: "Obj C: Programming with a hug"
description: "Introduction to the world of Objective-C programming"
category: Class Lectures 
tags: []
---
{% include JB/setup %}

### Hello World and Objective-C!
Welcome to the exciting world of Objective-C programming. Objective-C is a strictly typed, object oriented language used to create
programs for iOS and OS X environments. Cocoa is the name of the application environment for iOS an OS X written in Objective-C. It is possible to write Objective-C programs without Cocoa, but is typically not a practical thing to do. As a language Objective-C is mainly driven and maintained by Apple. Objective-C is to Apple what the .NET frameworks are to Microsoft.


### A brief history

**TL;DR** - Objective-C was inspired by Smalltalk. Steve Job's company NeXT
licensed Objective-C from a company called PPI and began writing awesome software. Apple acquired NeXT
and it's sweet developer tools in 1996. 

(Taken from Wikipedia: http://en.wikipedia.org/wiki/Objective-C)

Objective-C was created primarily by Brad Cox and Tom Love in the early 1980s at their company Stepstone. Both had been introduced to Smalltalk while at ITT Corporation's Programming Technology Center in 1981. The earliest work on Objective-C traces back to around that time.Cox was intrigued by problems of true reusability in software design and programming. He realized that a language like Smalltalk would be invaluable in building development environments for system developers at ITT. However, he and Tom Love also recognized that backward compatibility with C was critically important in ITT's telecom engineering milieu.

Cox began writing a pre-processor for C to add some of the capabilities of Smalltalk. He soon had a working implementation of an object-oriented extension to the C language, which he called "OOPC" for Object-Oriented Pre-Compiler. Love was hired by Schlumberger Research in 1982 and had the opportunity to acquire the first commercial copy of Smalltalk-80, which further influenced the development of their brainchild.

In order to demonstrate that real progress could be made, Cox showed that making interchangeable software components really needed only a few practical changes to existing tools. Specifically, they needed to support objects in a flexible manner, come supplied with a usable set of libraries, and allow for the code (and any resources needed by the code) to be bundled into a single cross-platform format.
Love and Cox eventually formed a new venture, Productivity Products International (PPI), to commercialize their product, which coupled an Objective-C compiler with class libraries. In 1986, Cox published the main description of Objective-C in its original form in the book Object-Oriented Programming, An Evolutionary Approach. Although he was careful to point out that there is more to the problem of reusability than just the language, Objective-C often found itself compared feature for feature with other languages.

##### Popularization through NeXT
After Steve Jobs left Apple Computer Inc., he started the company NeXT. In 1988, NeXT licensed Objective-C from StepStone (the new name of PPI, the owner of the Objective-C trademark) and extended the GCC compiler to support Objective-C, and developed the AppKit and Foundation Kit libraries on which the NeXTstep user interface and interface builder were based. While the NeXT workstations failed to make a great impact in the marketplace, the tools were widely lauded in the industry. This led NeXT to drop hardware production and focus on software tools, selling NeXTstep (and OpenStep) as a platform for custom programming.

The work to extend GCC was led by Steve Naroff, who joined NeXT from StepStone. The compiler changes, but not the runtime libraries, were made available as per GPL license terms rendering the open source contribution unusable to the general public. This led to other parties developing such under open source license. Later, Steve Naroff was also principal contributor to work at Apple to build the Objective-C frontend to Clang.
The GNU project started work on its free software implementation of Cocoa, named GNUstep, based on the OpenStep standard. Dennis Glatting wrote the first GNU Objective-C runtime in 1992. The GNU Objective-C runtime, which has been in use since 1993, is the one developed by Kresten Krab Thorup when he was a university student in Denmark. Thorup also worked at NeXT from 1993 to 1996.

After acquiring NeXT in 1996, Apple Computer used OpenStep in its new operating system, Mac OS X. This included Objective-C and NeXT's Objective-C based developer tool, Project Builder (which had been expanded and is now called Xcode), as well as its interface design tool, Interface Builder. Most of Apple's present-day Cocoa API is based on OpenStep interface objects, and is the most significant Objective-C environment being used for active development.

**Fun Obj-C fact** - The first webserver developed by Tim Berners-lee was written
in Objective-C and ran on a NeXTStep computer at CERN.

### Kind of like C
Objective-C is a superset of the C programming language. This means it's possible to use any C expression alongside Objective-C code. If you've used C or C++ before, Objective-C should look reletively familiar. Concepts like pointers, header files, structs, enums and preprocessor macros are all used in Objective-C.

#### The Objective-C runtime
**TL;DR** - While a strictly typed, compiled language; Objective-C is still
very flexible because of it's dynamic, message dispatch runtime.

*From Apple's Intro to Objective-C runtime*

The Objective-C language defers as many decisions as it can from compile time and link time to runtime. Whenever possible, it does things dynamically. This means that the language requires not just a compiler, but also a runtime system to execute the compiled code. The runtime system acts as a kind of operating system for the Objective-C language; it’s what makes the language work.

Note, that a dynamic runtime is not the same thing as a virtual machine used in
languages such as Java, Go or Erlang. Objective-C programs are complied and
excuted as native machine code.

By defering decisions to the runtime, it's possible to:
- Add new methods to a class while a program is executing
- Dynamically generate code based on program input
- Dispatch program execution to objects determined at runtime
- Handle errors with the grace of a hummingbird.

If you're familiar with Ruby, some of the same metaprogramming magic can be
done in Objective-C.

### Installing Xcode
The first step to developing any Cocoa application is installing our
programming IDE, Xcode, which can be found for free on the Mac Appstore.

![]({{ site.baseurl }}images/Lecture1/xcode-install.png)


### Writing your first Objective-C program
TDB

