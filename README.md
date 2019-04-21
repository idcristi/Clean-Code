# Clean Code Notes

## Contents
1. [Chapter 3 - Functions](#functions)
2. [Chapter 4 - Comments](#comments)
3. [Chapter 5 - Formatting](#formmating)
4. [Chapter 9 - Unit Testing](#unit-testing)
5. [Chapter 10 – Classes](#classes)
6. [Chapter 11 – Systems](#systems)
7. [Chapter 12 – Emergence](#emergence)
8. [Chapter 13 - Concurrency](#concurrency)
9. [Chapter 17 Smell and Heuristics](#smell-and-heuristics)

### Basic Concepts
****
1. Learning to write clean code is hard work. It requires more than just the knowledge of principles and patterns.
2. There is a difference between code that is easy to read and code that is easy to change.
3. Code without tests, is not clean.
4. Smaller code is better.
5. The code should be literate.
***
## Chapter 3 - Functions
1. First Rule:  Functions should be small
2. Second Rule: They should be smaller than that
3. Functions should do one thing. They should do it well. They should do it only.
4. Reading Code from Top to Bottom: Stepdown Rule


##### Functions Arguments 
Command Query Separation.  
Function should either do something or answer something but not both.  
Function should change the state of an object, or it should return some information about that object.  

##### Structured programming
Every function and every block within a function should have one entry and one exit. This means that there should only be one return statement in a function, no break or continue statement in a loop, and never any goto statements.

****

## Chapter 4 - Comments
Don't comment bad code try to rewrite it.
Good Comments are:
1. Legal Comments
2. Informative Comments
3. Explanation of Intent
4. Clarification

Bad Comments are:
1. Mumbling
2. Redundant Comments

****

## Chapter 5 - Formatting
#### Vertical Formatting

Try to keep max length around 500 lines long and smaller is better.  
Tomcat and Ant – several thousand lines long and at least half are over 200.  
Newspaper metaphor – read it vertically – headlines at the top detail increases as we go down the page.  
Separate concepts with blank lines.  
Closely associated code should be grouped together so it’s dense.  
Variable declarations should be as close to their usage as possible.  
If the methods are short, then the variable declarations should be at the top of the function.  
Control variables for loop should be defined within the loop.  
Instance variables should be declared at the top of a class.  
When one function calls another, those should be close vertically in the file.  
Conceptual affinity – when methods do similar things or are named similarly, they should also appear close to each other.  
Vertical ordering of methods – the caller should be first, then the callee, and that method’s callee, etc…on down the page.  

****
## Chapter 9 - Unit Testing
The Three Laws of TDD:  
TDD asks us to write unit tests first, before we write production code. Consider the following three laws:  
**First Law**: You may not write production code until you have written a failing unit test.  
**Second Law**: You may not write more of a unit test than is sufficient to fail, and not compiling is failing.  
**Third Law**: You may not write more production code than is sufficient to pass the currently failing test.  


#### What makes clean test?
•	Readability, Readability, Readability. Readability is perhaps even more important in unit tests than it is in production code.  
•	What makes tests readable? The same thing that makes all code readable: clarity, simplicity, and density of expression.  

Clean tests follow five other rules that form the above acronym:
##### F.I.R.S.T  
F - Fast  
I - Independent  
R - Repeatable  
S - Self-Validating  
T - Timely  

****

## Chapter 10 – Classes
Classes Should be small.
Following the standard Java convention, a class should begin with a list of variables. Public static constants, if any, should come first. Then private static variables, followed by private instance variables. There is seldom a good reason to have a public variable.
Public functions should follow the list of variables. We like to put the private utilities called by a public function right after the public function itself. This follows the stepdown rule and helps the program read like a newspaper article.

1. First rule. Classes should be small.
2. Second rule. The second rules of classes is that they should be smaller than that.

These rules  are measured or counted by responsibilities.
#### The Single Responsibility Principle
The Single Responsibility Principle (SRP) states that a class or module should have one, and only one, reason to change. This principle gives us both a definition of responsibility, and a guidelines for class size. Classes should have one responsibility—one reason to change.
#### Cohesion
Classes should have a small number of instance variables. Each of the methods of a class should manipulate one or more of those variables. In general the more variables a method manipulates the more cohesive that method is to its class. A class in which each variable is used by each method is maximally cohesive.
In general it is neither advisable nor possible to create such maximally cohesive classes; on the other hand, we would like cohesion to be high. When cohesion is high, it means that the methods and variables of the class are co-dependent and hang together as a logical whole.

***

## Chapter 11 – Systems
#### Dependency Injection
A powerful mechanism for separating construction from use is Dependency Injection (DI), the application of Inversion of Control (IoC) to dependency management. Inversion of Control moves secondary responsibilities from an object to other objects that are dedicated to the purpose, thereby supporting the Single Responsibility Principle.
In the context of dependency management, an object should not take responsibility for instantiating dependencies itself. Instead, it should pass this responsibility to another “authoritative” mechanism, thereby inverting the control. Because setup is a global concern, this authoritative mechanism will usually be either the “main” routine or a special-purpose container.
The Spring Framework provides the best known DI container for Java. You define which objects to wire together in an XML configuration file, then you ask for particular objects by name in Java code. 

***

## Chapter 12 – Emergence
**Four rules of simple design are:**
1. Runs all the tests
2. Contains no duplication
3. Expresses the intent of the programmer
4. Minimizes the number of classes and methods

#### Simple Design Rule 1: Runs All the Tests
First and foremost, a design must produce a system that acts as intended. A system might have a perfect design on paper, but if there is no simple way to verify that the system actually works as intended, then all the paper effort is questionable.
A system that is comprehensively tested and passes all of its tests all of the time is a testable system. That’s an obvious statement, but an important one. Systems that aren’t testable aren’t verifiable. Arguably, a system that cannot be verified should never be deployed.
Fortunately, making our systems testable pushes us toward a design where our classes are small and single purpose. It’s just easier to test classes that conform to the SRP. The more tests we write, the more we’ll continue to push toward things that are simpler to test. So making sure our system is fully testable helps us create better designs.
Tight coupling makes it difficult to write tests. So, similarly, the more tests we write, the more we use principles like DIP and tools like dependency injection, interfaces, and abstraction to minimize coupling. Our designs improve even more.
Remarkably, following a simple and obvious rule that says we need to have tests and run them continuously impacts our system’s adherence to the primary OO goals of low coupling and high cohesion. Writing tests leads to better designs.
#### Simple Design Rules 2–4: Refactoring
Once we have tests, we are empowered to keep our code and classes clean. We do this by incrementally refactoring the code. For each few lines of code we add, we pause and reflect on the new design. Did we just degrade it? If so, we clean it up and run our tests to demonstrate that we haven’t broken anything. The fact that we have these tests eliminates the fear that cleaning up the code will break it!
During this refactoring step, we can apply anything from the entire body of knowledge about good software design. We can increase cohesion, decrease coupling, separate concerns, modularize system concerns, shrink our functions and classes, choose better names, and so on. This is also where we apply the final three rules of simple design: Eliminate duplication, ensure expressiveness, and minimize the number of classes and methods.

***
## Chapter 13 - Concurrency
##### Concurrency
Objects are abstractions of processing. Threads are abstractions of schedule.”

##### Myths and Misconceptions
1. Concurrency always improves performance. Concurrency can sometimes improve performance, but only when there is a lot of wait time that can be shared between multiple threads or multiple processors. Neither situation is trivial.
2. Design does not change when writing concurrent programs. In fact, the design of a concurrent algorithm can be remarkably different from the design of a single-threaded system. The decoupling of what from when usually has a huge effect on the structure of the system.
3. Understanding concurrency issues is not important when working with a container such as a Web or EJB container.
4. Concurrency incurs some overhead, both in performance as well as writing additional code.
5. Correct concurrency is complex, even for simple problems.
6. Concurrency bugs aren’t usually repeatable, so they are often ignored as one-offs instead of the true defects they are.
7. Concurrency often requires a fundamental change in design strategy.

##### Concurrency Defense Principles
What follows is a series of principles and techniques for defending your systems from the problems of concurrent code.
#### Single Responsibility Principle
***Keep your concurrency-related code separate from other code
Corollary: Limit the Scope of Data
Corollary: Threads Should Be as Independent as Possible
Thread-Safe Collections***

There are several other kinds of classes added to support advanced concurrency design. Here are a few examples:      

Classes | Description
| ------------- |:-------------|
|**ReentrantLock**|  A lock that can be acquired in one method and released in another.|
|**Semaphore**| An implementation of the classic semaphore, a lock with a count.|
|**Semaphore**| A lock that waits for a number of events before releasing all threads waiting on it. This allows all threads to have a fair chance of starting at about the same time.|
    

#### Know Your Execution Models  
Classes | Description
| ------------- |:-------------|
|**Bound Resources**| Resources of a fixed size or number used in a concurrent environment. Examples include database connections and fixed-size read/ write buffers.|
|**Mutual Exclusion**| One thread or a group of threads is prohibited from proceeding for an excessively long time or forever. For example, always letting fast-running threads through first could starve out longer running threads if there is no end to the fast-running threads.|
|**Livelock**| Threads in lockstep, each trying to do work but finding another “in the way.” Due to resonance, threads continue trying to make progress but are unable to for an excessively long time— or forever.|

Bound Resources	Resources of a fixed size or number used in a concurrent environment. Examples include database connections and fixed-size read/ write buffers.
Mutual Exclusion  
	Only one thread can access shared data or a shared resource at a time.  
Starvation	One thread or a group of threads is prohibited from proceeding for an excessively long time or forever. For example, always letting fast-running threads through first could starve out longer running threads if there is no end to the fast-running threads.  
Deadlock	Two or more threads waiting for each other to finish. Each thread has a resource that the other thread requires and neither can finish until it gets the other resource.  
Livelock	Threads in lockstep, each trying to do work but finding another “in the way.” Due to resonance, threads continue trying to make progress but are unable to for an excessively long time— or forever.  


### Producer-Consumer
One or more producer threads create some work and place it in a buffer or queue. One or more consumer threads acquire that work from the queue and complete it. The queue between the producers and consumers is a bound resource. This means producers must wait for free space in the queue before writing and consumers must wait until there is something in the queue to consume.   
Coordination between the producers and consumers via the queue involves producers and consumers signaling each other. The producers write to the queue and signal that the queue is no longer empty. Consumers read from the queue and signal that the queue is no longer full. Both potentially wait to be notified when they can continue.

### Readers-Writers
When you have a shared resource that primarily serves as a source of information for readers, but which is occasionally updated by writers, throughput is an issue. Emphasizing throughput can cause starvation and the accumulation of stale information. Allowing updates can impact throughput. Coordinating readers so they do not read something a writer is updating and vice versa is a tough balancing act. Writers tend to block many readers for a long period of time, thus causing throughput issues. The challenge is to balance the needs of both readers and writers to satisfy correct operation, provide reasonable throughput and avoiding starvation. A simple strategy makes writers wait until there are no readers before allowing the writer to perform an update. If there are continuous readers, however, the writers will be starved. On the other hand, if there are frequent writers and they are given priority, throughput will suffer. Finding that balance and avoiding concurrent update issues is what the problem addresses.

### Dining Philosophers
Imagine a number of philosophers sitting around a circular table. A fork is placed to the left of each philosopher. There is a big bowl of spaghetti in the center of the table. The philosophers spend their time thinking unless they get hungry. Once hungry, they pick up the forks on either side of them and eat. A philosopher cannot eat unless he is holding two forks. If the philosopher to his right or left is already using one of the forks he needs, he must wait until that philosopher finishes eating and puts the forks back down. Once a philosopher eats, he puts both his forks back down on the table and waits until he is hungry again. Replace philosophers with threads and forks with resources and this problem is similar to many enterprise applications in which processes compete for resources. Unless carefully designed, systems that compete in this way can experience deadlock, livelock, throughput, and efficiency degradation.
Most concurrent problems you will likely encounter will be some variation of these three problems. Study these algorithms and write solutions using them on your own so that when you come across concurrent problems, you’ll be more prepared to solve the problem.
***
## Chapter 17 Smell and Heuristics
#### Comments
Inappropriate Information  
Obsolete Comment  
Redundant Comment  
Poorly Written Comment  

#### Environment
Build Requires More Than One Step  
Tests Require More Than One Step  

#### Functions
Too Many Arguments  
Output Arguments  
Flag Arguments  
Dead Function  

#### General
1. Multiple Languages in One Source File  
2. Obvious Behavior Is Unimplemented  
3. Incorrect Behavior at the Boundaries  
4. Overridden Safeties  
5. Duplication  
6. Code at Wrong Level of Abstraction  
7. Base Classes Depending on Their Derivatives  
8. Too Much Information  
9. Dead Code  
10. Vertical Separation  
11. Inconsistency  
12. Clutter  
13. Artificial Coupling  
14. Feature Envy  
15. Selector Arguments  
16. Obscured Intent  
17. Misplaced Responsibility  
18. Inappropriate Static  
19. Use Explanatory Variables  
20. Function Names Should Say What They Do  
21. Understand the Algorithm  
22. Make Logical Dependencies Physical  
23. Prefer Polymorphism to If/Else or Switch/Case  
24. Follow Standard Conventions  
25. Replace Magic Numbers with Named Constants  
26. Be Precise  
27. Structure over Convention  
28. Encapsulate Conditionals  
29. Avoid Negative Conditionals  
30. Functions Should Do One Thing  
31. Hidden Temporal Couplings  
32. Don’t Be Arbitrary  
33. Encapsulate Boundary Conditions  
34. Functions Should Descend Only One Level of Abstraction  
35. Keep Configurable Data at High Levels  
36. Avoid Transitive Navigation  

#### Java
Avoid Long Import Lists by Using Wildcards  
Don’t Inherit Constants  
Constants versus Enums  

#### Names
1. Choose Descriptive Names  
2. Choose Names at the Appropriate Level of Abstraction  
3. Use Standard Nomenclature Where Possible  
4. Unambiguous Names  
5. Use Long Names for Long Scopes  
6. Avoid Encodings  
7. Names Should Describe Side-Effects  

#### Tests
1. Insufficient Tests  
2. Use a Coverage Tool!  
3. Don’t Skip Trivial Tests  
4. An Ignored Test Is a Question about an Ambiguity  
5. Test Boundary Conditions  
6. Exhaustively Test Near Bugs  
7. Patterns of Failure Are Revealing  
8. Test Coverage Patterns Can Be Revealing  



