---
layout: post
title: "Debugging: things will go awry"
description: ""
category:class lectures
tags: []
---
{% include JB/setup %}

The act of debugging is one of those skills which will serve the programmer for
the life of their career. Apps worth their .99 cents can be complicated, and
things will break for unexpected reasons. While the 'debugging' connotaion is
somewhat negative, debugger tools are extremely useful for exploring Cocoa
framework code or learning the internals of a new library. 

### Enable Breakpoints

Check that breakpoints are enabled in Xcode. This can be done at the top of the
screen between the 'Run' button and status area.
![]({{BASEPATH}}images/Lecture5/enable_breakpoints.png)

Now that breakpoints are enabled, it's time to set some breakpoints in our code
and see what happens.

#### What is a breakpoint?
A breakpoint causes the application to pause execution at a specific point.
Breakpoints are most useful when running your application in the simulator, and
will not be included when your app is in the appstore. (so don't worry) When
the application has paused, we can step through the program line by line and
observe variable values and method calls as they happen. We can also interact
with the running program by changing variables or inspecting the contents of
datastructures.

##### But I debug via print statements ...
While effective, it's a lazy way to find bugs. A print statement will only show
that execution passed a certain point along with whatever data is printed. When
tracing execution flow, many print statements are required which is time 
consuming and tedious. 
##### TL;DR
Stepping through execution in a symbolic debugger is
like using a flashlight in a dark room. All values are illuminated. Debugging
with print statements is fumbling around the edges of furniture in the dark.

#### Setting a breakpoint
Configuring a breakpoint in code is very easy; simply click in the grey area to
the left of a line of code. You should see a little blue pill shape.
![]({{BASEPATH}}images/Lecture5/code_breakpoint.png)
