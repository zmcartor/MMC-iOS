---
layout: post
title: "Objective C Classes"
description: ""
category: class lectures 
tags: []
---
{% include JB/setup %}

Let's create our first Objective-C class! Like before, we'll be using Xcode to
setup the basic class template for us. 

Open up the first HelloWorld project in Xcode, and then select File->New->File . In the dialog, select
Objective-C class like the image below:
<br>
![]({{BASEPATH}}images/Lecture2/new-class.png)  

<br>
This new class will be called 'Drink' and will be a subclass of NSObject.
![]({{BASEPATH}}images/Lecture2/name-new-class.png)  

<br>
Click 'next' and two new files will appear: Drink.h and Drink.m

####NSObject : The base class of reality
Within Cocoa, NSObject is the baseclass of all objects. It contains all base
methods related to interacting with objects in Objective-C such as init ,
alloc, copy and other basic object methods.

###Create the public interface
Select Drink.h and we'll take a walkthrough what all this gibberish means.


{% highlight objective-c %}
  #import <Foundation/Foundation.h>

  @interface Drink : NSObject

  @end
{% endhighlight %}

* The first line which begins with #import simply includes the Foundation
  framework. It's possible to use #include from C, however #import is much more
  friendly as it will not include a header more than once.

* The second line simply declares our new class and specifies that it should
  inherit from NSObject. Other classes we create later on may inherit from
  NSViewController, NSManagedObject, or your own classes. Objective-C is
  a single-class inheritance language. This actually turns out to not be a
  problem at all for advanced behavior. Because of the nature of it's dynamic runtime, 
  the [software pattern of composition](http://en.wikipedia.org/wiki/Composite_pattern) is
  easy. (and much better than multiple inheritance!)

* after we're done declaring everything in this object, we close it with a @end
  to be polite to the compiler.

  Let's add two fields to this class:

  {% highlight objective-c %}
  #import <Foundation/Foundation.h>

  @interface Drink : NSObject

  @property(strong, nonatomic) NSArray *ingredients;
  @property(strong, nonatomic) NSString *name;

  @end
{% endhighlight %}


The '@property' directive is how we add instance variables to a class. (Don't worry about
'strong' and 'nonatomic' for now.) The first field has a type of NSArray and is
called ingredients. The second field is an NSString and is called name.
Declaring instance fields with the @property compiler directive also means
getter and setter methods are generated automatically for us by the runtime.
Great!

A class is boring without some methods. Let's create a couple.

  {% highlight objective-c %}
  #import <Foundation/Foundation.h>

  @interface Drink : NSObject

  @property(strong, nonatomic) NSArray *ingredients;
  @property(strong, nonatomic) NSString *name;

  - (NSString *)drinkOrderReadyFor:(NSString *)name cost:(NSNumber *)money;
  + (NSArray*)drinkMenu;

  @end
{% endhighlight %}

#### Functions
Functions in Objective-C can take a little bit to get used to. They may look
strange because all parameters are 'named' parameters. This means every
parameter will be prefixed by a name like 'param:value'. This is different than
most other languages which simply use the position of the parameters in the
function list to determine what they mean. For example fireMissles(10, 34.5, 56.7,'big').  

Let's break down these function definitions:
{% highlight objective-c %}
  - (NSString *)drinkOrderReadyFor:(NSString *)name cost:(NSNumber *)money;
  + (NSArray)drinkMenu;

{% endhighlight %}

* The minus sign - in front of the function means it is a instance
  method. It's meant to be called by instances of the Drink class. 
  A plus + sign means it is a class method. Here, drinkOrderReadyFor is an
  instance method and drinkMenu is a class method.

* drinkOrderReady is the name of this function

* After the name of the function, a color denotes the first parameter to this
  function. It's type is NSString and is called name within the function
  implementation.

* The second parameter is called 'cost' and of type NSSNumber. It's called
  'money' within the function implementation.

  Great, now we know howto declare both instance and class functions!

  Now comes the fun part of implementing; open up Drink.m and type in the
  function skeletons. Xcode should autocomplete the function signatures because
  they are declared in your header. How handy is that!!?

Drink.m should look like this:

{% highlight objective-c %}

#import "Drink.h"

@implementation Drink

- (NSString *)drinkOrderReadyFor:(NSString *)name cost:(NSNumber *)money {
    
};

+ (NSArray *)drinkMenu {
    
};

@end
{% endhighlight %}

Next, let's fill in some guts so these methods will do something other than
take up valuable whitespace. drinkOrderReadyFor will print out the name of the
person whos drink is ready along with the cost:

{% highlight objective-c %}

- (NSString *)drinkOrderReadyFor:(NSString *)name cost:(NSNumber *)money {
    return [NSString stringWithFormat:@"ORDER UP for %@! That will be $ %@ dollars", name, money];
};
{% endhighlight %}

And the class method 'drinkMenu' will merely return the menu of drinks at our fine establishment.
We're so high class that prices aren't listed. [If you have to ask to price, you
can't afford it.](http://mouton954.com) 

{% highlight objective-c %}

+ (NSArray *)drinkMenu {
  return @[@"coffee", @"scotch" , @"iced tea" , @"artisan ice cubes"];
};
@end
{% endhighlight %}

Recall in the HelloWorld app where we used the function ArrayWithObjects: A
much easier way to declare and fill an NSArray with objects is to use the
shorthand way of "@\[ \]". NSHipsters call this an 'array literal.'

### Hello Drinks!

Open up main.m within the hello world project and include our new class using
an import statement. We are now free to use all our new class in this file.
Let's order up some drinks! Change main.m so it now looks like below. 
{% highlight objective-c %}

#import <Foundation/Foundation.h>
#import "Drink.h"

int main(int argc, const char * argv[])
{

    @autoreleasepool {
        NSArray *menuToday = [Drink drinkMenu];
        NSLog(@"Oh hello, here are our drinks for today %@", menuToday);
        
        Drink *order = [[Drink alloc] init];
        NSString *announcement = [order drinkOrderReadyFor:@"Zach" cost:@11];
        NSLog(@"%@", announcement);
        
        Drink *otherOrder = [[Drink alloc] init];
        NSString *otherannouncement = [otherOrder drinkOrderReadyFor:@"Graham" cost:@8];
        NSLog(@"%@", otherannouncement);

    }
    return 0;
}
{% endhighlight %}

Compile and run the program. The output produced should look like:
{% highlight objective-c %}
Oh hello, here are our drinks for today (
    coffee,
    scotch,
    "iced tea",
    "artisan ice cubes"
)
ORDER UP for Zach! That will be $ 11 dollars
ORDER UP for Graham! That will be $ 8 dollars
{% endhighlight %}

### Recap:

Declaring and using methods in Objective-C will take some practice. The odd
message passing syntax of \[ \] borrowed from Smalltalk is unlike most C based
languages. In the final program, creating a new object is accomplished by using
'alloc' followed by 'init' like in the line:

{% highlight objective-c %}
Drink *otherOrder = [[Drink alloc] init];
{% endhighlight %}

These methods are inherited from NSObject and allocate memory and initialize
the new object.

### TODO
* Add a new property to the class called 'caffeine' which is of type NSNumber.
* Create a custom initializer which takes caffeine as an argument.
[Apple docs: object initialization](https://developer.apple.com/library/ios/documentation/general/conceptual/CocoaEncyclopedia/Initialization/Initialization.html)
