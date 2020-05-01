---
layout: post
title: Strong and Weak references in Java
date: 2014-10-25 01:40:00 
tags: [java]
---

## Different degrees of weakness

[Here](http://weblogs.java.net/blog/enicholas/archive/2006/05/understanding_w.html) is a very good article about different degrees of weakness of Java reference types. As the author says, many people doesn't even know about these but I think `WeakReference` is pretty useful in many of the applications so it is really important to understand these.

Again, I made some notes from the above mentioned article:

There are actually four different degrees of reference strength in Java: strong, soft, weak, and phantom, in order from strongest to weakest.

### Strong reference
If an object is reachable via a chain of strong references (strongly reachable), it is not eligible for garbage collection.

### Weak reference

A weak reference is a reference that isn't strong enough to force an object to remain in memory.

### Soft reference

A soft reference is exactly like a weak reference, except that it is less eager to throw away the object to which it refers. An object which is only weakly reachable (the strongest references to it are WeakReferences) will be discarded at the next garbage collection cycle, but an object which is softly reachable will generally stick around for a while.

### Reference queues

The `ReferenceQueue` class makes it easy to keep track of dead references. If you pass a `ReferenceQueue` into a weak reference's constructor, the reference object will be automatically inserted into the reference queue when the object to which it pointed becomes garbage.

### Phantom references
A phantom reference is quite different than either `SoftReference` or `WeakReference`. Its grip on its object is so tenuous that you can't even retrieve the object -- its get() method always returns null. They allow you to determine exactly when an object was removed from memory. They are in fact the only way to determine that.

PhantomReferences avoid a fundamental problem with finalization: finalize() methods can "resurrect" objects by creating new strong references to them. With PhantomReference, this situation is impossible -- when a PhantomReference is enqueued, there is absolutely no way to get a pointer to the now-dead object. Because PhantomReference cannot be used to resurrect an object, the object can be instantly cleaned up during the first garbage collection cycle in which it is found to be phantomly reachable.
