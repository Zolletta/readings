# The programmer’s brain

## by Felienne Hermans, published by Manning

I found [The programmer’s brain, by Felienne Hermans](https://www.manning.com/books/the-programmers-brain) very interesting. The only drawback, in my opinion, was the organization of contents: I would have rearranged in a different manner because in the way I read them I felt some low cohesion.
Below I won’t cite too many researchers and professors, but keep in mind that the book has all the names and the bibliographic information needed!

## Activities in programming

According to the [Cognitive dimension of notation framework](https://en.wikipedia.org/wiki/Cognitive_dimensions_of_notations), the act of programming comprises five activities:

1. **searching** for a specific information
2. **comprehension**
3. **transcription** - just coding (you are transcribing your understanding, that is “your mind”, into the code)
4. **incrementation**: a mix of searching, comprehension and transcription
5. **exploration**: when you have a vague idea of where you want to go, so you need to “play with code” in order to get insight and gain clarity about further directions

Debugging is not listed because it is seen as a mix of all five activities.

## Enhancing our comprehension with easy-to-read code

Research shows that 60% of a programmer's time is spent understanding rather than writing code. But we are not so good at reading code and this sometimes leads us to reinvent the wheel because it’s simpler than to invest time learning how to be efficient on reading code.

When we read, we leverage our short term memory whose size is limited. [Several psychological experiments](https://en.wikipedia.org/wiki/The_Magical_Number_Seven,_Plus_or_Minus_Two) have found its size to be 5/7 items or even smaller.
What is precious here is the concept of “item”. That’s because its size can be changed from smaller to bigger with training and the powerful technique of **chunking**.
That’s why expert developers are better at reading code.

But there’s also the **iconic memory**: the sight’s sensory memory, just before it becomes conscious information: of course not all you see can enter your short term memory. But you can also leverage the things that do not emerge from this (unconscious) level.

So, how to write chunkable code that can leverage iconic memory? The author reminds us the importance of using design patterns, writing high-level comments and leaving beacons in the code. Beacons?

Beacons provide triggers to confirm or refuse hypotheses about the source.

- **Simple beacons** are syntactic code elements, such meaningful variable names.They are simple enough to unlock the functionality of the code by themselves.
- **Compound beacons** are larger structures comprised of simple beacons providing semantic meaning for functions that simple beacons execute together.

## Forgetting Curve

It takes 15 minutes to get back to work after an interruption. If you think about that, that’s a good reason not to rely on the internet (and instead invest on studying syntax) when dealing with new programming languages.
The author describes a method involving flash cards and then illustrates Herman Ebbinghaus’s **Forgetting Curve**.
One trick to try to overcome this forgetfulness is repetition, but not at regular intervals: those intervals should last longer, because as the memory settles in our long term memory the kind of training it needs will be different: from continuous and numerous repetitions needed to establish the memories to repetitions needed to avoid the links to memory networks to disappear: this kind of training will improve the storage and retrieval strength.

One key to counter the forgetting curve is the **elaboration**.

This article you are reading is an elaboration, which means, by the words of the author,   
>thinking what you want to remember, relating it to existing memories, and making the memories fit into schemata already stored into your LTM (p. 44). 
An elaboration is a way to restructure your understanding and to sculpt it into a long term network of memories.

## Cognitive load

Joan Sweller identified three types of cognitive load:

- **intrinsic cognitive load**: how complex is it the problem?
- **extraneous cognitive load**: what outside distractions add to the problem
- **germane cognitive load**: cognitive load due to the handling of finite cognitive resources (= brain). For instance, when we are so deep in the calculation that, when finished, we forgot the problem at hand.

We should train ourselves to distinguish these three types of cognitive loads because to address them we need different strategies: for instance, we may have and an extremely convoluted code (suffering from extraneous cognitive load) that would benefit from a major refactoring: in that way the intrinsic complexity of the problem would surface while all the other ancillary problems would be encapsulated in other libraries/classes and thus out of sight.

## Mental models in a developer’s world

Mental models can help you solve problems and help you ease your cognitive load. They are like
>an abstraction [of the world] that help you reason about the problem at hand (p. 95)

Mental models are by nature incomplete and can change over the course of time. Besides, several mental models (regarding related issues) can coexist, each with its local coherence, even if - taken as a whole, it would appear as totally incoherent.
Finally, we should remember that sometimes we could fall back to old, falsy mental models, because once new ones are established the older are not  simply wiped out, but kept in our mental storage (long term storage) until oblivion or recall.

All that said it becomes evident that data structures, design patterns, architectural patterns, diagrams, modeling tools… all can serve as mental models.
Double check the metaphors you will be using, though. They might create confusion.

## How to onboard new developers

>One of the reasons more-senior people often struggle with effectively teaching and explaining is the "curse of expertise”. Once you have mastered a certain skill sufficiently, you will inevitably forget how hard it was to learn that skill or knowledge. You will, therefore, overestimate how many new things a newcomer can process at the same time. (p. 206).

Experts are not the same as junior developers, only faster. Instead, their gained experience made their long term memory different from junior developers and so their approach to problem solving is a lot different from them.

There are three kind of confusions at play when dealing with all the cognitive activities related to software development:

- lack of knowledge, related to **long term memory (LTM)**: for instance, when you gain experience of a programming language structures and its idioms, long term memory plays a role because it cements the knowledge (you don’t have to think about i.e. its loop structures). It’s kind of hard drive.
- lack of information, concerning **short term memory (STM)**:  the short term memory is activated for instance when keeping note of variable names. It’s called RAM.
- lack of processing power, regarding the **working memory**. The working memory is triggered for instance when you are mentally tracing the working of a code. If you feel the urgence to take notes it may be a sign that your working memory is overloaded. That’s CPU.

This is particularly true for new hires, and that’s why it would be a very good outcome if we could introduce this psychological outcome in our lingo: saying things like “my working memory is overloaded” would communicate much more information then that “I’m confused”!

Besides that, what’s most certainly true is that new hires are asked to do too much at the same time. The simple tasks they are assigned will probably deal with all but exploration phases all the same time learning other important stuff like the company organization, the team way of working, and so on.

In order to ease the life of the new hires (and, If I may add, to better evaluate their specific skills) the author suggests preparing specific smaller tasks - each one that can be built on top of the previous - that focus only on one aspect of the programming, as defined in the cognitive dimension of notation framework.

And remember:

>understanding is a better welcome task than building. (p. 216)

## Automatization

In our long term memory resides two kind of memories:

- the **procedural (implicit) memory** which is the memory that describes how to do the things: for example how to tie your shoelaces, how to ride a bike. Remember how you learned? At first by paying attention to every single aspect of the task, until, repetition after repetition, it became second nature and the thinking became … implicit.
- the **declarative (explicit) memory** concerns episodic memories, things that happened in the past.

Researchers demonstrated that experts rely heavily on episodic memory when trying to solve problems: in a sense, they recreate familiar settings and apply the same reasoning that worked that time.
But what about a solution in which we depended a great part on the procedural memory instead? One of the great aspects of the book is that is it full of exercises to help improve our cognitive fitness. In this case the author call it **automatization**:
>this automatic performance of the task is quick and effortless because retrieval from memory i s faster than actively thinking of the task at hand can be done with little or no conscious attention. (p. 170).
