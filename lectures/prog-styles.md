---
title: programming stylesheet
author: Neil Ernst
date: oct 2021
paginate: true
marp: true
---

# Programming Styles
Derived from T. Latoza, SWE 621, GMU

----
# Learning Objectives
* understand some examples of different programming styles
* compare and contrast the advantages of the different constraints 
* read code in Python that implements the styles
* differentiate between architectural style, design pattern, and programming style
  
----
#  Programming Style
A set of **constraints** on how code is written which help achieve specific requirements or quality attributes.

A **style** is creation under constraints. 

Programming modalities: 

1. Write code to produce machine instructions via compiler/interpreter/linker 
2. Write code to help humans understand what the code should be doing. 

In this sense modality 2 is like the HCI of software: how humans interact with the computer.

---

# Programming Style:

Describe alternative ways in which code might be written

* make it object-oriented (why)
* lazily load data from input source (why)
* give each element a separate thread (why)
* make it functional (why)

----
# Different Abstractions Levels in Software
All three embody best/good practices to solving common problems and constraints.

| Approach | Breadth | Abstraction | Sources | |
| ---| ---|---|---|---|
| Arch Tactic | System/sub-system | Expressed in natural language/models | ||
| Design Pat. | Module | Diagram | GoF book; OO | |
| Progr Style | File | Code | Languages | |


----
# Book: Exercises In Programming Style
Presentation is centred around an example problem.

Each program offers the same baseline behavior (sometimes adding an additional feature)

Can directly compare and contrast how the same problem is solved each style 

Directly illustrates the diversity of ways of programming

Some are related to programming language features (e.g., OO, functional, reflection)

But many modern languages support a range of language features that support a diversity of styles

E.g. **all examples written in Python**

----
# Working Problem: Term Frequency

Given a text file, print the 25 most frequent words and corresponding frequencies
Sort from most frequent to least frequent
Normalize for capitalization and ignore "stop" words (e.g., the, for, ...)

**Input**
Tigers live mostly in India 
Wild lions live mostly in Africa
**Output**
live - 2 
mostly - 2 
africa - 1 
india - 1 
lions - 1 
tigers - 1 
wild - 1

----
# What To Watch For
1. How long the program is (LOC)
2. How long the explanation is (complexity)
3. How Python might have to be abused to make the style work
4. How such a style might exist as an Architecture Tactic or Design Pattern.

----
## Chapter 3, Monolithic
- one piece of code, no abstractions, no library calls
- "old school" (Basic) and GoTo 

```
10 LET N=10
20 FOR I=1 TO N
30 PRINT "Hello, World!"
40 NEXT I
```

Compare with Monolithic architecture

----

## Chapter 4, Cookbook
- break program into chunks
- use globals to share state
- procedures each affect state and depend on state (idempotence)
- early programs using *structured programming*
- systems: common pattern with database access

----

## Chapter 7, Infinite Mirror
- aka induction
- tail recursion optimization (constraints of Python)
- maps naturally to many mathematical problems
- where is this found in Systems? 
----

## Chapter 13 Abstract Things
- depend on an abstraction not the thing itself
- define abstract things to use, then implementations thereof
- `I<Name>` syntax defines a Thing
- Strongly typed
- When do we need the abstractions vs the concrete classes? 
- Very common in Design Patterns and Tactics

----
## Chapter 16, Introspective and 17, Reflective
- Programs which "know themselves"
- in Introspection, examine who the Caller is and restrict access
- adds another layer of indirection and what you see may not be what is happening (cf operator overloading)
- in Reflective, define function as a string and then call `exec`
- useful when we expect to add *new things* to our code (i.e. dynamically)
----

## Chapter 18, Aspects
- leverage reflection to add functionality that **cross-cuts** primary functionality
- (profiling)
- a weaver uses reflection to add the new aspect
- similar to Python's `decorator` but without attaching directly to the function (which may be far away from the aspect code)
- 
----

## Chapter 25, Persistent Tables
* constraint is to persist data beyond just this use
* do not optimize data storage for a single use (relational)
* very common in the shared-data style; this programming style is essentially an architecture style in one file.
  
----
## Chapter 27, Lazy Rivers
- we don't know how much data we will be reading; or, we are reading from input larger than memory
- make use of Python's `yield` to return to where the fn left off
- contrast with a Pipeline where data is passed entirely 
- Systems: quite common in event-based systems and the Command Query Responsibility Segregation style
  
----

## Chapter 28, Actors
- program elements are essentially inboxes that send/receive messages
- actors have independent threads of execution
- Python lacks native support - hence the extra code prefixed `_`
- Systems: big part of distributed systems eg Erlang or [Elixir](https://home.cs.colorado.edu/~kena/classes/5828/f14/lectures/16-actors.pdf) which is built around Actors


----
# Summary
* Many choices about how to implement a solution
* Programming styles offer a vocabulary for talking about alternative implementations
* Makes explicit the constraints which lead to a specific style of programming
* Can consider explicitly the consequences of following these constraints
* Many styles map to equivalent tactics or patterns over more modules


----
# Activity: Sketch Implementation In Lazy River Style
Work individually, pick an OO language (e.g., Java, Python, C#) 

Sketch an implementation of the following
> Given a text file, output all words alphabetically, 
> along with the page numbers on which they occur. 
> Ignore all words that occur more than 100 times. 
> Assume a page is a sequence of 45 lines.

```
abatement - 89
abhorrence - 101, 145, 152, 241, 274, 281 
abhorrent - 253
abide - 158, 292
```

Does not need to compile and run, just looking for a sketch that illustrates following the programming style for this problem





