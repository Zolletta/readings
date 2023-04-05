# A philosophy of software design

## by John Ousterhout, published by Standford University

> Please note: I won't publish a direct link to the page details here since I cound'nt find the publisher's page. Just google the title to find out where to buy the book (highly advised :)

John Ousterhout, as [his Wikipedia page](https://en.wikipedia.org/wiki/John_Ousterhout) states is a professor of Computer Science at Stanford University. He also invented [TCL](https://en.wikipedia.org/wiki/Tcl) in 1988.

John decided to write this book because he found that the most demanding process in computer science was **problem decomposition** (that is how can we split a complex problem into smaller, manageable and developable parts?). Yet nobody teaches this skill: everybody builds on that, taking for granted that anybody can do that, as an innate feature.

The author thinks that designing skills are what separates a great programmer from average ones.

His mantra, emerging throughout his work, is: **reduce complexity**.

Ousterhout is also humble; he knows very well that his book derives from his own opinions and that we might disagree with his view. He invites us then to take his suggestions with a grain of salt.
I found this very refreshing: there are a lot of books out there that provide us the real-truth, in every human field!

## On complexity, dependencies, and obscurity

**Complexity** is everything that makes it hard to understand and modify the software.

Signs of complexity include:

- Change amplification: a supposed simple change requires a lot of updates in many different parts
- Cognitive loads: how much a developer needs to know to complete a task?
- Unknown unknowns: it is not clear what should be done in order to achieve our goal

The causes of complexity are either dependencies or obscurity.

We cannot really create a software system without adding some **dependencies**, but our job is to make it explicit and reduce their number to a minimum.

**Obscurity**, defined as anything that is not obvious or not consistent, is clearly subjective. So we cannot evaluate it by ourselves, we need code reviews.

## On programming approaches

We should understand that **complexity is an emergent quality**. It is something that accumulates by every little thing we skip to the next time. Every little thing that we leave unresolved will settle creating a layer of dust into our system. As the dust grows, our system becomes dirt. But when exactly did it became dirt? You cannot tell the real moment: cleanness, as complexity, is a gradient. And it has no end!

That’s why there’s a chapter called “working code isn’t enough”. Tactical programming (that is ‘get those features as quickly as possible’) won’t work in the long run. This is how systems become complicated.

And this is somehow different from well-established principles as [YAGNI](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it) or [KISS](https://en.wikipedia.org/wiki/KISS_principle) had always told us...

In order to avoid complexity, we always need to keep in mind the long-term structure of the system, an approach the author defines as **strategic programming**.
It’s rare, nowadays, that we create the software from scratch: we almost always update existing code. So we should program in order to ease future code extensions: this will facilitate our future developments.
Ousterhout suggests investing about 10%-20% of the time planned on a task to produce better software design. This will make completing tasks 10%-20% slower, but only in the first runs: since once the complexity is reduced, we can take advantage of that.

And this resembles the boy scout rule...

One advice the author gives us is to try to design every system twice, approaching the problem from different standpoints. No one gets it right at the first try!

## On deep modules

The book then goes on by defining deep modules. A **module** is a unit of code with an interface and an implementation.

**Deep modules are those that provide powerful functionalities with simple interfaces.**

Module’s interface represents the complexity that the module imposes to the others. Simpler is (of course) better!

With this perspective, shallow modules are the ones that expose quite long interfaces (in comparison with their implementation), such as small modules.

Side note: This is somehow original because we are always taught that small modules are good and one of the refactoring goals is to split long class into several smaller ones.
This approach, however, may lead to cognitive load: since every module does not contribute so much in itself we will need a lot of them, each with its own interface to digest.

The author is, instead, not against long methods. They are fine if they have a simple signature and are easy to read. “Methods, in other words, should do one thing and do it completely.”

“The decision to split or join modules should be based on complexity. Pick the structure that results in the best information hiding, the fewest dependencies and the deepest interfaces”.

## On information hiding and leaking

How can we get rid of complexity?
One technique is information hiding. It will simplify the interface and make it easier to make amendments.
The opposite of information hiding is information leakage and could occur in several ways: via explicitly declaring a dependency in an interface or, worst, if a set of modules depends on assumptions about the outside world (say, for instance, we have two modules that both rely on a file format).
Another kind of information leakage is the temporal decomposition: in this case, we have functionalities that should happen in a given order, split into several modules or classes.
Of course, we should hide only that information that is needed only inside the module.
Our job as developers is to minimize the information that needs to be let outside the module.

## On interfaces

The book goes on suggesting several techniques to reduce complexity.
One interesting advice is to create a specific module for the given task but with a generic interface. As the author says, “the interface should be general enough to support multiple uses: the interface should be easy to use for today’s needs without being tied specifically to them”.

## On software layers

A software system is composed of different abstraction layers.
Ideally, methods directly implementing the interface should be at the highest level of abstraction and make use of lower ones in order to achieve their goals.
If we found ourselves up and down this lattice we might have a problem with class decomposition.
We might have a problem, for instance, when facing pass-through methods (from one class to another) if they contribute no new functionality. A dispatcher, for instance, is a pass-through method, but It has a reason to exist.
Decorators (as per the author’s point of view) seldom add new functionalities and usually, we can avoid them with other methodologies.
And how can we evict pass-through variables? Ousterhout suggests using a context object, an object which will contain all the needed pass-through information without recurring to global state (which is, indeed, bad). The author suggests passing that context object only to the constructor and then storing a reference in the class in order to reduce the pass-through of that single object.

Personal note: I would, however, stick to this (that is, I wouldn’t save the context object in the class state) since this will re-instate the problem of object state inside the class and making the class methods less testable. I think that reducing the clutter of pass-through variables from a bunch to one is a good result!

## On Exceptions

Exceptions add complexity because we should decide whether to handle them and where (at the low level or at the outer most?) because writing the handling methods could lead to other exceptions and also because it is difficult to test if such code really works.
One approach is to “**define errors out of existence**”.
For example, instead of throwing an error in case we are trying to unset an unknown variable, we can simply do nothing, in that case.
In the same way, we can make special cases out of existence. The author gives this example: think about a text editor and the text selection mechanism. Instead of cluttering all the code of if statements testing if a selection is available we can make the selection always present by having it at length 0 when the user did not select anything.
In this way, we can let exceptions handle only exceptional things!

## On comments

“Without comments, you can’t hide complexity. … Comments, if done correctly, will actually improve a system’s design”. “If a user must read the code of a method in order to use it, then there is no abstraction”.
Ideally, developers should read only the interfaces. To help them, comments are needed to describe what’s not obvious. Typically, comments will add information at a lower level of the code (adding precision) or at a higher level (adding intuition). Comments at the same level of the code are likely to repeat the code itself and thus be unuseful.
Try to make it easy to find documentation (put comments near the code they describe) but do not repeat comments; instead reference it, if needed.

## On consistency

Consistency means that similar things are done in a similar way. This ease the cognitive burden, because once you have learned how to achieve a goal, you’ll have established a habit to re-use on other occasions.
If a system is not consistent, two situations may seem the same when actually they aren’t, leading to avoidable mistakes.

## On obviousness

A code is obvious only if the current reader is able to read it and comprehend it. You should provide all the needed information to correctly digest your code. You can do this in three ways:
reducing the information needed, eliminating special cases and leveraging abstraction
taking advantage of consistency, you can meet your readers’ expectations
presenting important information right in the code with techniques such as giving good names to methods and variables and in-line comments.

## On Agile

Agile development focuses on features, and once is done, moves to the next. Agile development, in fact, dictates that development should be done incrementally.
Ousterhout suggests that “the increments of development should be abstraction, not features”.

## On test-driven development

“TDD focus attention on getting specific features working, rather than finding the best design: it’s tactical programming pure and simple. … At any given point, it’s tempting to just hack in the next feature to make the next test pass”.
