---
title:  "Test your code"
date:   "2020-10-04 01:55:26"
categories: code
published: true
---

Breaking things is fun, even sometimes in programming. The real pain comes when the problem is hidden under webs of complex code.

Most of us would have been there at some point, blindly hacking away, making so much progress through our shiny new feature. 
Piles of code written, but none of it executed yet. Then, when it all "should" run, we hit compile and....

It just doesn't.

>It's broken, I don't know what's wrong! That code "should" work!!

The compiler is rarely wrong.

One of the harder things for a new dev to learn is how to avoid this. How to make code more manageable, make it easier to test 
and get it running as often as possible.

The best practices in software development are always around faster feedback. From finding bugs earlier to
finding out what the client *actually* wants by getting their input well before the end of a project. 

You can apply this concept during development through unit tests, but to see the best value you need to consider 
how your code could be tested as you go along writing it.

Take this code for example:

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
test individual components. Then, before any of it can be run, we have to write all the code and 
hope that it works right.

This takes too long.

If instead we break down the components into reusable methods, we can make it easier to see if 
the code we are writing will work without having to wait for the whole feature to be written.

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

In the above example, the broken down code now becomes much clearer to read and easier to test.

Each component can be run individually, making feedback faster because now, you can test each component
as you complete them. These tasks are now a lot smaller and it will be easier to find where that bug lies.

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

In the above test, it's much easier to robustly test that single component and
we don't need to worry about the wider feature yet. 

1. Add Drive() method
2. Prove that Drive() does what it should

When writing software, it's important not to think of our madly scribbled down code as a finished product. 
Much like in school we would review drafts of our essays before finally turning them in.

Do the same with code. Once the process and logic are discovered, go back and think about what could be simplified and 
where it could add value. If you're lucky enough to work with others, ask for a code review. 

Its these extra moments spent early on, that early feedback from the compiler or tests that help prevent those
painful surprises later on.