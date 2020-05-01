---
layout: post
title:  "Handling slash encoded URLs in Glassfish"
date:   2014-06-06 10:11:34
tags: [glassfish rest grizzly apache]
---
Today, I ran into a strange requirement where I needed to make the REST URIs with '%2F' in path part work. However, I realized that the requests were not reaching the sevlet in my Glassfish application server which uses Grizzly for NIO and Apache as servlet container.  When I dig further, this is what I have learnt.

Apache denies all URLs with %2F in the path part, for security reasons. So is Grizzly library when it receives a HTTP request.

Apache provides AllowEncodedSlashes directive to turn on the slash encoded URLs which handles URLs containing '%2F' ('/' character) and '%5C' ('\' character). Alternatively, slash encoded URLs can also be enabled by passing the following property to Apache sever.

{% highlight java %}
-Dorg.apache.tomcat.util.buf.UDecoder.ALLOW_ENCODED_SLASH=true
{% endhighlight %}

Similary, the following asadmin command can be run to enable slash encoded URLs on Glassfish.
{% highlight bash %}
asadmin set
 configs.config.server-config.network-config.protocols.protocol.http-listener-1.http.encoded-slash-enabled=true
{% endhighlight %}

Alternatively, pass the following property as jvm option to Glassfish.
{% highlight java %}
-Dcom.sun.grizzly.util.buf.UDecoder.ALLOW_ENCODED_SLASH=true
{% endhighlight %}

So, if you have a Glassfish server using Apache servlet container with Grizzly NIO library, you have to enable slash encoded URLs at both the Apache and Grizzly level, for the request on slash encoded URI to make all the way upto servlet.

For more info, check [Apache AllowEncodedSlashes directive] [allow-slashes] and [Encoded slashes for Glassfish] [gf-slashes]

[allow-slashes]: http://httpd.apache.org/docs/2.2/mod/core.html#allowencodedslashes
[gf-slashes]: https://java.net/jira/browse/JERSEY-1456
