---
layout: post
title: "ObjC Protocols"
description: "Objective-C protocol introduction and usage in CocoaTouch"
category: class lectures
tags: []
---
{% include JB/setup %}
Cocoa includes many standard components for use within your app. The way your
code interacts with these standard components is typically facilitated through the Objective-C concept of Protocol.

### Conforming to Protocol: A List of Messages
Protocols define a list of methods that an object adopting the
protocol must implement. Optional and required methods are described within the
protocol documentation. If you know Java, protocols are basically what
'interfaces' are in Java. 

#### Ordering coffee or steak ?
Here's a real world example - when getting coffee in the morning, Steve visits
CupOJoe and asks for 'A large, dark coffee to go.' This message is understood
by the barista and Steve gets his coffee. If Steve were to asked for 'a porterhouse steak, rare' the barista would have given him a strange look! Barista's implement and respond to messages from the coffee protocol, not steak protocol!

Protocol declaration occurs with in the header file. The name of the protocol
is within 'pointy' brackets. Remember - protocols are pointy!

{% highlight objective-c %}
@interface InputViewController : NSObject <UITextFieldDelegate>
// ...
@end
{% endhighlight %}

This class declares that it conforms to the UITextFieldDelegate protocol.

#### UITextFieldDelegateProtocol
iOS apps can accept input in a variety of ways. The most basic way is the
simple input box. Fortunately, there's a standard way for view controllers to
interact with UITextfields. Try the following tutorial to get better acquainted
with textFields and all the actions available with the protocol. 

[Mobile Tuts: UITextField](http://mobile.tutsplus.com/tutorials/iphone/ios-sdk-uitextfield-uitextfielddelegate/)

For reference, [Apple docs on UITextFieldDelegate](https://developer.apple.com/library/ios/documentation/uikit/reference/UITextFieldDelegate_Protocol/UITextFieldDelegate/UITextFieldDelegate.html)
