---
layout: post
title:  "UNIX SIGNAL '0'"
date:   2014-04-30 14:54:34
categories: UNIX SIGNAL kill 
---

In UNIX, signal `0` can be used with `kill` command to check if a process exists and accepts signals from the current user. However, no signal is sent to the process when `kill -0` is run. This command could be used as an alternative to parsing `ps` output for checking the process existence. Since it’s not shown in most of the help pages or signal list via `kill -l`, it may not be known to some users.

{% highlight bash %}
kill -l
HUP INT QUIT ILL TRAP ABRT EMT FPE KILL BUS SEGV SYS PIPE ALRM TERM URG STOP TSTP CONT CHLD TTIN TTOU IO XCPU XFSZ VTALRM PROF WINCH INFO USR1 USR2 
{% endhighlight %}

Examples:
You can use the following code to check if a process exists.

{% highlight bash %}
# Check if a process with given PID exists.
kill -0 $pid; echo "Exit status: $?”
{% endhighlight %}

The exit status of this command will be ‘0’ if the process with given pid exists, ‘1’ otherwise. `errno` will be set appropriately if the command fails.

If you are unsure if a process is still running but you want to kill it if it runs, then you can use the below command.

{% highlight bash %}
# Kill if the process with given PID exists.
kill -0 $pid && kill $pid
{% endhighlight %}

For more info, check [kill(2)] [kill2-man]

[kill2-man]: http://linux.die.net/man/2/kill
