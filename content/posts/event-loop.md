+++ 
draft = false
date = 2021-09-04T19:22:15+05:00
title = "The Single Thread King that is Event Loop"
description = ""
slug = ""
authors = ["Muhammad Ghayas Baig"]
tags = ["NodeJS", "Technology", "Software Engineering", "Javascript", "Event Loop"]
categories = []
externalLink = ""
series = []
featuredImage = "/el.jpg"
medium = "https://medium.com/@mgb247/the-single-thread-king-that-is-event-loop-9cc777dcebe7"
+++

Whenever a new software project is born, on top of the priority list is the environment or framework in which it will be developed. In the software engineering world, there are multitudes of frameworks in which an idea can be engineered. For example, to create a webapp, we have a never ending list of options which may include a few well known frameworks like ASP .NET Framework on the C# side, Laravel on the PHP side and NestJS, ExpressJS, KoaJS, AdonisJS, MeteorJS and *WhatnotJS* on the NodeJS side.

Seriously though, NodeJS has so many frameworks that engineering your idea on one might mean missing out some great features that another framework might be offering. This abundance of frameworks for NodeJS could not have come without it being a Javascript runtime. The JS language is super easy to learn and use. That is one of the reasons that today, JS is being used not only to develop webapps but also desktop and mobile applications. JS removed the dependency to learn new languages to develop different sides of the same idea.

But this doesn't mean that everyone should use JS for everything. As with every other framework, JS frameworks have their downsides as well. And one of the most important that should be considered is that JS is single threaded. Being single threaded means a huge wastage of both time and resources. Today, a single threaded server cannot even be thought of to develop applications. But then you must be wondering how a JS server handles thousands of requests per second. A multi threaded server would simply handle each request in a separate thread. But JS has only one thread.

The short answer is, JS does this via what we call the *Event Loop*. For the long answer, let's dive into the details of how NodeJS manages those thousands of requests without any of them blocking the other.

#### The part handled by JS

Before we get into the event loop, let's distinguish between what's part of JS and what's not. When executing code, the important parts of the Javascript Engine to consider are:

-   #### Memory Heap
    This is the space allocated for all the code that is being executed.
-   #### Call Stack
    This is the stack where synchronous code arrives in order.

It is important to understand that the Event Loop is not part of the Javascript Engine itself. There are some WebAPIs that provide the ability to run code asynchronously. When this JS code is running inside a browser, then the browser provides these APIs. When this code is running in NodeJS runtime, it provides these APIs. Some of these APIs include functions like setInterval and setTimeout.

So, the complete picture of the execution of your code looks like this:

![](/el_js.png)

Let's see how our code is executed by the JS runtime:

1.  Your code is executed in the sequence it appears. This code may include both synchronous and asynchronous tasks.
2.  The synchronous tasks are put into the stack and executed right away. However, for the asynchronous tasks, you either explicitly register a callback to be executed when they are completed or the JS internals do this for you (for example when using async/await). This is done via WebAPIs provided by the runtime which may be a browser or NodeJS.
3.  The WebAPIs register a callback and that is added to the event queue (explained later).
4.  Once the callback is triggered by the event loop, it gets added to the stack so that execution can continue where it was left.

In the meanwhile, JS executes all other synchronous code. Only when the stack gets empty, does the code from the event loop is executed.

Let's see what happens inside the Event Loop when callbacks are registered.

#### Serving everyone with a Single Thread

The event loop is a never ending while loop --- well, until it has something to execute at least. The way NodeJS executes code using the event loop is as follows:

![](/el_el.png)

1.  First, an operation arrives, this can be a call to a function, or a request from the server or anything that triggers execution. This operation resides in the *event queue*. If this operation contained only synchronous code, it would get executed right away in a FIFO manner on the main thread without ever arriving to this event queue. In that case it would be a blocking operation as it would block the main thread.
2.  If this operation contained tasks that are meant to be performed asynchronously, for example getting data from a database or making an API call etc., it would arrive at the event queue.
3.  From here, NodeJS registers a callback that is meant to be called when the asynchronous operation is performed.
4.  These asynchronous operations are performed on multiple background threads so that if another asynchronous operation arrives on the queue, that is processed as well along with all the other existing asynchronous operations.
5.  Once the asynchronous operation is finished, the registered callback is called which again brings the operation to the main thread.
6.  The task is then removed from the event queue.

This process makes sure that the main thread remains free to be used by other synchronous operations and no operations are blocked. This also means no wastage of CPU cycles or time. Every request is served *almost* equally without having multiple threads.

We can see the practicality of this flow by executing a very simple NodeJS script:

1.  console.log('Executed First');
2.  setTimeout(() => {console.log(('Executed Last')}, 2000)
3.  console.log('Executed Second');

The first statement is executed right away as it's synchronous. The second statement uses setTimeout to register a callback which would get triggered after 2 seconds. If we didn't have the event loop, this would block the third statement for 2 seconds. But with the event loop, a callback is registered and the third statement is executed. Only after 2 seconds does the last statement execute.

#### What this means

Most importantly, this means that NodeJS, while being a single threaded runtime, can be used to empower the engineering solutions that your ideas have to offer.

Applications involving tasks that require huge computational power should still be developed in a multi threaded framework. But for most cases of a webapp, a NodeJS server is really sufficient and can serve all the purposes without wasting many resources by creating multiple threads.

The event loop is what makes JS an easy choice to develop literally anything.