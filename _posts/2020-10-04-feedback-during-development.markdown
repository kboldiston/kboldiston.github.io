---
title:  "Feedback during development"
date:   "2020-10-04 01:55:26"
categories: code
published: true
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
static void Main() 
{
    bool engineOn = true;
    int gas = 15;
    
    double speed = 10;
    int x = 5;
    int y = 20;

    Console.WriteLine("My top speed is {0}", speed);
}
{% endhighlight %}

In the above code we have a method that does multiple things and offers no real way to 
test individual components of the and parts of this code cannot easily be reused elsewhere.

If instead we break down the components into reusable parts they become much easier to test.
{% highlight csharp %}
static void Main()
{
    Vehicle car = new Vehicle();

    car.StartEngine();

    car.Speed(10);
    car.Drive(5, 20);

    car.DisplaySpeed();
}
{% endhighlight %}

In the above example the broken down code now becomes much clearer to read and easier to test. As can bee seen below

{% highlight csharp %}
[TestMethod]
public void TestDrive()
{
    Vehicle testCar = new Vehicle();

    testCar.Drive(1, 10);

    Assert.Equals(1, testCar.XPosition);
    Assert.Equals(10, testCar.YPosition);
}
{% endhighlight %}