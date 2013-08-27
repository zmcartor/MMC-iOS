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

**TL;DR** - Objective-C was inspired by Smalltalk. Steve Job's company NeXTStep
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

![]({{BASEPATH}}images/Lecture1/xcode-install.png)


### Writing your first Objective-C program

Great, now that Xcode is installed, let's take it for a spin!

Open Xcode and select 'new project'
![]({{BASEPATH}}images/Lecture1/new-xcode-proj.png)  
<br><br>

Select the template under OS X , Application , Commandline utility like the
picture shown below:  
<br>
![]({{BASEPATH}}images/Lecture1/xcode-choose-template.png)

Now the fun part, name your new project whatever the heck you'd like. I've
chosen HelloWorld, but it could have called HelloDolly, or HelloKitty.

The organization name can be whatever you'd like.

Company identifier is somewhat important, as all the classes you create will be
prefixed by this identifier. Apple reserves all two character prefixes, and the
convention is to use three letters for 3rd party prefixes. If you have no idea
what to use, just use MMC.

Make sure 'Foundation' is chosen for 'type', and 'Use automatic reference
counting' is checked.  
<br>

![]({{BASEPATH}}images/Lecture1/name-project.png)  
<br>

Click 'next' and BAM your new project has been created! On the left hand side of the screen, select main.m like the picture below:
<br>
![]({{BASEPATH}}images/Lecture1/xcode-code-start.png)
<br>
<br>

Try clicking around on some of the other files in Xcode and see what happens.
Xcode can look like the cockpit of a fighter jet, but don't worry! We'll soon
understand what most of this stuff means. 
<br>
<br>
![]({{BASEPATH}}images/Lecture1/jet.png)<br>
*Welcome to Xcode, fire ze missles!*

Click the "Run" button at the top left of the screen to build and run the
application. A debug window will open up at the bottom of the screen showing
the output. Congrats on your first Objective-C app!

![]({{BASEPATH}}images/Lecture1/hello.png)<br>

### That was boring...
Ok, granted no one is going to pay for a 'hello world' app on the Appstore. If
you really want to make money, [you'll need to add glowing pictures and some
text at least.](http://en.wikipedia.org/wiki/I_Am_Rich)

In the area where it says "insert code here" , paste in the following code:

{% highlight objective-c %}
// insert code here...
NSArray *drinks = [NSArray arrayWithObjects:@"coffee", @"espresso" @"tea", nil];

NSDictionary *citiesAndPopulations = [NSDictionary dictionaryWithObjectsAndKeys:@797494, @"Columbus", @2700000, @"Chicago", @13389, @"Circleville", nil];

NSLog(@"These are really great drinks: %@", drinks);
NSLog(@"Here are some nice cities %@", citiesAndPopulations);

{% endhighlight %}

Now, re-run the code and tell me that output isn't worth at least .99 cents?
