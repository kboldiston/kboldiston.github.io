---
layout: post
title:  "Break Everything"
date:   "2020-10-04 01:55:26"
categories: jekyll update
---

Breaking things is fun, even sometimes in programming. The real pain comes when the problem is hidden under webs of complex code.

Most of us would have been there at some point, blindly hacking away, making so much progress through our shiny new feature. 
Piles of code written, but none of it executed yet. Then, when it all "should" run, we hit compile and....

Boom, it won't compile.

>It's broken, I don't know what's wrong! That code "should" work!!

I hear this way too many times.

One of the harder things for a new dev to learn is how to avoid this. How to break the code into managable chunks, 
make it testable and run it often. The best practices in software development are always around feedback, find bugs earlier, 
find out what the client *actually* wants as soon as possible. Do the same with your code even before it leaves your hands.

Take this code for example

{% highlight csharp %}
public static void DoesTooManyThings() 
{
    // TODO: write code that does too many things
}
{% endhighlight %}

In the above code...


{% highlight csharp %}
public void DoesOneThing() 
{
    // TODO: write code that does one thing 
}
{% endhighlight %}

However when...