---
layout: post
title:  Perl’s DESTROY method
date:   2012-03-08 00:00:00
---
**What is DESTROY for?**

Just like some other programming languages provide automatic garbage collection for the programs, Perl also collects all the garbage from your program automatically. Perl uses a method called ‘DESTROY'\[1\] for this purpose and this method is called by Perl implicitly when an object goes out of scope after reference count is dropped to zero.

**When should I use it?**

In general you do not need to use this method explicitly but you might need to use this if you have recursive data structures that point to themselves. In those cases, Perl will not reclaim that data structure since the reference count for that data structure would be non-zero so you can use ‘`DESTROY' `to break the links manually.

**Is it invoked always?**

There are cases like program being aborted with interrupt signal, under which Perl will not invoke DESTROY method. So, if your program is using some resources which must be released before the program exits, make sure you catch the signals and take care of releasing the resources.

Also, there is no guarantee about the time at which DESTROY will be invoked by Perl so we should not depend on DESTROY assuming that it will be invoked at an expected time. Perl provides no guarantees for when will DESTROY be called.

**Difference between END and DESTROY?**

END block is a piece of code which will be executed by Perl just before the interpreter exits and END is not related to object oriented features. There can be multiple END blocks in which case they are executed in the reverse order of declaration but there will be only one DESTROY for a class. If you override DESTROY in a subclass, you have to explicitly invoke super class’s DESTROY method.

**References:**

Here are some references if you would like to understand more about the DESTROY method in Perl.

[http://perldoc.perl.org/perlobj.html#Destructors](http://perldoc.perl.org/perlobj.html#Destructors)

[http://perldoc.perl.org/perltoot.html#Destructors](http://perldoc.perl.org/perltoot.html#Destructors)

[http://docstore.mik.ua/orelly/perl4/prog/ch12_06.htm](http://docstore.mik.ua/orelly/perl4/prog/ch12_06.htm)

* * *

_\[1\] All the methods which are implicitly called by Perl will be in upper_
