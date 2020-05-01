---
layout: post
title:  "Object Initialization in Java"
date:   2014-10-24 00:44:00
tags: [java]
---

I stumbled upon [this](http://www.artima.com/designtechniques/initializationP.html) Artima article about "Object initialization in Java" today. This is a detailer about Java's object initialization and here are some important points directly taken from the article. I am keeping them here so that I can refer to them later or someone else who thinks that article is TL;TR can quickly skim through these points. 

* The Java language has three mechanisms dedicated to ensuring proper initialization of objects: *instance initializers* (also called *instance initialization blocks*), *instance variable initializers*, and *constructors*.

* Like methods, you can give access specifiers to constructors, but unlike methods, constructors with public, protected, or package access are not inherited by subclasses. Also, instead of determining the ability to invoke a method, the access level of a constructor determines the ability to instantiate an object.

* You can have methods in a Java class with the same name as the class itself.

* When you compile a class, the Java compiler creates an instance initialization method for each constructor you declare in the source code of the class. Although the constructor is not a method, the instance initialization method is. It has a name, `\<init\>`, a return type, void, and a set of parameters that match the parameters of the constructor from which it was generated.

* Into each `\<init\>` method, the compiler can place three kinds of code:
    1. An invocation of another constructor
    2. Instance variable initializers
    3. The constructor body

* For every class except Object, the first thing each `\<init\>` method will do is invoke another constructor.

* Often, the code of an instance initialization method does more than the code defined in the body of its corresponding constructor. The compiler also potentially adds code for any initializers and an invocation of the superclass's constructor.

* Instance initializers can't make *forward references*.

* When an object is created, the Java virtual machine allocates enough space for all the object's instance variables, which include all fields defined in the object's class and in all its superclasses.

* Every Java virtual machine must have the capability to determine information about its class, given only a reference to an object. This is needed for many reasons, including type-safe casting and the instanceof operator.

* You can't have both `this()` and `super()` in the same constructor. You can only have one or the other (or neither, if the direct superclass includes a no-arg constructor). If a constructor includes a `this()` or `super()` invocation, it must be the first statement in the constructor.

* Although `\<init\>` methods are called in an order starting from the object's class and proceeding up the inheritance path to class Object, instance variables are initialized in the reverse order. Instance variables are initialized in an order starting from class Object and proceeding down the inheritance path to the object's class.

* You should be careful when you invoke methods from initializers or constructors, because you can end up using instance variables before they've been properly initialized.

