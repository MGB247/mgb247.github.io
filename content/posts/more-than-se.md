+++ 
draft = false
date = 2022-11-12T12:00:00+05:00
title = "More than a Software Engineer"
description = ""
slug = ""
authors = ["Muhammad Ghayas Baig"]
tags = ["Software Engineering", "Ownership", "Improvement"]
categories = []
externalLink = ""
series = []
featuredImage = "/mtse.jpeg"
medium = "https://medium.com/@mgb247/more-than-a-software-engineer-2ee64949c8e4"
+++

For the last couple of months, I’ve been working on a Multi-Tenant Architecture at [Rewaa](https://www.rewaatech.com/en/). And for the last couple of weeks, I’ve been working on some core architectural changes specifically on the Database side. Recently I had to write a solution, where we had to expect a downtime of a few hours. We will have to change that — software engineers always find a way out of anywhere, it’s just a matter of trade-offs.

But this got me thinking,

> _What if we could not change this scenario, and had to go with a downtime?_

The scale at which Rewaa operates today is one that can not be ignored. Rewaa has 10k+ clients, a number that is rapidly growing. A downtime of even a few seconds is felt and reported let alone minutes or hours.  
But even then,

> _What happens if there’s a downtime of an hour?_

Well, a lot will happen, nothing of which is positive. The **10k+** clients will all be blocked from using the service for an hour. The nature of Rewaa’s business dictates that this will have consequences impacting not only the clients but the client’s customers as well. The clients will not be able to make purchases for their customers via the Rewaa POS application (Although that’s not the case for Rewaa since we provide offline support for POS as well). But other services of Rewaa will definitely be impacted, that includes the integration with 3rd Party applications like Salla, [Zid](https://zid.sa/en/), and [Woocommerce](https://woocommerce.com/) as well.

Indirectly this means, clients getting slowed down and consequently implies a lower number of sales made for the day. This also means, more customers getting angry with our clients because their system didn’t work the first time they came to shop at our client’s store.

For larger stores, _it simply means complete chaos._

![](/featcomplex.png)

**_Basically, we cannot expect any downtime, no matter the scale of the problem._**

Software Engineers are really _underappreciated_. A software engineer isn’t a person who follows the cycle — eat, sleep, code, repeat. Although that’s part of their job for sure. But the lines of code that engineers write, all have to be well thought of. The solutions that they carve, have to be scalable and are expected to be infallible for at least a century if not forever. When a **_programmer_** writes some lines to display a button on the UI, it’s not only placing the button on the screen but considering what will happen if the button was left pressed forever. What will happen if one client is using that button a lot, will it impact the other clients? What will happen if someone figures out the API behind the button and tries to abuse the system using that? Who should the button be visible to?

These are very simple examples of what a **_programmer_** would think when writing a solution. But all of these are in the context of programming. Every good **_programmer_** will go over all of such questions and try to answer them as part of the solutions they write.

But Software Engineers are expected to do more. They are expected to know more. Not only are they expected to write good code, again, that is part of their job. But they are also expected to **_own_** the piece of code that they have written. The thing is, that no one will mention this. All of this has to come implicitly.

Here are a few things that I’ve learned throughout my 3 years in the industry that I think contribute to making you do more than software engineering, implicitly.

**Context is not important, it’s necessary**
--------------------------------------------

Most software engineers are very aggressive in terms of trying to ship their code to production. This is especially true in the early stages of the career. They just want to get done with writing the code and flaunt their typing speed to the product team. Honestly speaking — Been there; done that. This is something inherent to all of us and consequently very counterintuitive to consider being changed.

In fact, most of the time, this leads to a product that nobody asked for and everyone is confused why the product didn’t do well in production. Other times, while the code may have worked for a few days, the solution is not very well thought out and is deprecated by some other  engineer as part of a technical debt (causing more resources to be used for no reason).

A good software engineer will always do their homework in terms of what is required. Sometimes we don’t ask questions because we think that they might be stupid, and sometimes they even are. But it’s important to understand that you need to have **_clarity_** regarding what is required. And nothing should stop you from having that clarity before you start to write your code.

![](/context.png)

Ask questions like:

*   _Why are we building this feature?_
*   _Why are we changing this already-implemented feature?_
*   _What’s the benefit that the customers will get from this feature?_
*   _What’s in the feature and what’s not?_
*   _Is it a temporary feature or something with a long-term goal? What’s that goal?_

Questions like these help you carve a solution that would be more in line with what the stakeholders wanted. It helps to provide better estimates. The problem that you thought was too complex, might become simpler. Or one that you thought to be simple might become complex.  
What matters is that you have **_clarity_** and the decisions that you make after having this clarity are going to be the right ones.

**Estimates are estimates**
---------------------------

This relates to the previous point. Again, as software engineers, we always want to make people happy by delivering before the deadline. This is a problem. No, not making the people happy, but delivering before the deadline.

The reality of estimates is that they are, _estimates._ To be more clear, they are not like the past, which cannot be changed. They are like the future, which not only can change but may be _unpredictable_ as well. And the present is where you are asked to provide them.

![](/estimates.png)

Think of it this way; You estimated that you will ship _the feature_ in 2 weeks. Later, you realized that it needed 3 weeks. But being _the good software engineer_ you are, you somehow ship it in 2 weeks. The Product team is super happy. After shipping, they realise that it was not working as expected. It’s too slow. The reason is the 1 week that you skipped in your estimation. The product team is all but happy.

A good software engineer will never provide out-of-the-box estimates. Estimates should be provided after careful analysis of the problem at hand. This problem should be divided as much as possible so that individual components can be estimated. Even with the largest estimate that you estimate, you should add a buffer to that.

Again, this is all related to **_clarity._** The better estimates you provide to the product team, the better you both will be able to achieve the target and the smaller will be the stack of technical debt.

Plagiarising
------------

Not literally.

Many times we encounter situations that we might find difficult to solve. It is natural for software engineers to think of solutions on their own. But in the process of doing so, they forget that they might be _reinventing the wheel._

We are super lucky to have the internet that has tools like git and websites like StackOverflow. These exist for a reason. Essentially all software engineering problems are solved to some extent by some other engineer. And if there’s a good solution available on the internet, it’s there to be used.

![](/sesol.png)

The only thing remaining for a programmer to do is to be able to search for these solutions. This is an ability in itself. But while a good **_programmer_** will be able to find these solutions effectively, a good software engineer will be able to contribute to these solutions just as effectively.

So, once in a while when you write your own solutions, make them open source and available for other engineers to be used.

Process Awareness
-----------------

This is one of the most important things software engineers forget. We all love to expand our stack of languages, learn new data structures, finish the never-ending queue of new _Javascript frameworks_ and clear our road to become that Architect that everyone looks up to (I’m sure that’s not how you become a Software Architect).  
This is good, but never enough.

What we need to understand is that programming is just a tool/skill to achieve an actual product. Your end goal is never actually just writing good code and pushing it to production. Your end users will never review your code, all they will care about is whether the solution you provide works for them in the context of your product. Even if you are contributing to a library that in itself optimizes another piece of software, your end goal should be the impact that it will make when it will be used on someone’s product in production. Your contributions are global and have an impact of the same scope.

![](/process.png)

A good software engineer will therefore acquire complete knowledge of the system and product on which they are working. Making yourself comfortable with the processes involved in the system will always help you create a better product. If you are working on an e-commerce / quick commerce website, you should understand the ins and outs of the retail business. Not only does this make you understand and produce better solutions, but it allows you to make contributions by suggesting alternatives on the product end.

In this regard, I’ve noticed that prioritizing my knowledge of the product over my software engineering skills turned out to be better. This however may be subjective. For example, at the start of your career, it may be better to first get comfortable with more and more software engineering. But eventually, you will reach a state where it’s just a matter of getting acquainted with a new tool and recognizing patterns to get things done in software. Your basics will always remain constant.

Ownership
---------

We all possess things that we love and are passionate about.

All of the things that I have discussed so far are only possible if there’s ownership. And for ownership to be there, it’s imperative that there be a passion for the thing that is to be owned.

It is for this very reason, that you will hear the word _Ownership_ a lot more in startups than in big tech. (That doesn’t mean that there is less ownership among software engineers in big tech). It’s because startups need to induce the idea of truly owning the product within their team members, who don’t necessarily include engineers only. Only by truly owning the product that engineers work on, can they be the most productive in their work.

![](/ownership.png)

So what’s up with ownership? I’m surely not going to explain what it is. I think that is very well done in another article I read [here](https://tsh.io/blog/ownership-in-software-development/). But the reason I brought it up here is that ownership cannot come without passion. A good software engineer may not perform up to their potential simply because they may not feel that they own the product as much. One of the most important reasons for that is the absence of passion for the product or solution that you are working on. So be sure to traverse the path that you are most excited to contribute to.

That is the first step towards _owning your_ solutions.

Is that all required to become _more than a Software Engineer_? _Yes_

**_No_** :)

So that you folks don’t get bored, I figured I’ll make this a series and do more of these as I learn with everyone else.  
Let’s expand this list together.
