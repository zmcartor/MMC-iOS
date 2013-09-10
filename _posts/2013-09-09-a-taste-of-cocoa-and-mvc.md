---
layout: post
title: "A taste of Cocoa and MVC"
description: ""
category: class lectures
tags: []
---
{% include JB/setup %}

Now that we've masterd the syntax of Objective-C and written a few classes,
it's time to finally write a *real* CoacoaTouch program.

This link contains the walkthrough to create <a href="https://developer.apple.com/library/ios/documentation/iphone/conceptual/iphone101/Articles/00_Introduction.html" target="_blank">Your First iOS App </a>

Before starting, let's discuss a key design pattern used all over Cocoa (and
most of the web for that matter ... )

### Model-View-Controller (MVC)
Within Cocoa, "views" are what's shown on the screen. However to keep our
programs organized, responsibilities are segregated into discrete classes to
keep apps from becoming giant classes of code spaghetti.

#### The View
The topmost layer, what's ultimately reflecting the internal state of the
program on the screen. In iOS, a view is actually a single frame of [Core
Animation](https://developer.apple.com/library/ios/DOCUMENTATION/Cocoa/Conceptual/CoreAnimation_guide/Introduction/Introduction.html) However views are fragile and afraid of the large, cold world. That's why views are typically wrapped in a "ViewController" blanket.

![]({{BASEPATH}}images/Lecture3/viewcontroller.png) 

#### The Controller
The ViewController contains logic for interacting with the view. This means
methods for setting label text, button state the view's background color, view position and other view attributes are contained here. A ViewController is the gatekeeper for interacting with a 'view hierarchy.' Views (and view controllers) can be nested inside other views which create a hierarchy. As apps may have several things going on at once on the screen, wrapping views in view controllers allows the logic for updating the UI state to be contained in one class.

#### The Model
While a controller contains the logic for visually displaying information, that
information has to come from somewhere!

![]({{BASEPATH}}images/Lecture3/datamodel.png)

The model controls access to any data the view may need. This could be the
current user's email address, email messages, list of photos, anything. The
data model could be something as simple as an NSArray, or a custom class which
encapsulates reading and writing to a remote HTTP API. Cocoa provides a great
framework called [Core Data](https://developer.apple.com/library/ios/documentation/cocoa/conceptual/CoreData/cdProgrammingGuide.html) which is useful for maintaining relational data graphs, amougst other things.

#### Separation of concerns
The main benefit of MVC is the separation of concerns into separate classes.
Code which only cares about manipulating a view hierarchy can be kept in the
ViewController, and data access responsibilities kept separate within a datasource object. 
The cool part about this design is a Datamodel class or ViewController can be easily
switched out or re-used within the application somewhere else. It's fairly
common to create a general-use ViewController which consumes different model
objects. We'll see an example with TableViewControllers next
lecture. 
