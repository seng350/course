---
title: Abstraction
author: Neil Ernst/Thomas Latoza
date: Aug 24, 2021
mar$$

$$p: true
---
# Abstractions
Based on original notes from Thomas Latoza (GMU).

----

# What is an Abstraction?

The ability to interact with an idea while safely ignoring some of its details. A set of operations on shared state that make solving problems easier. Examples:

- **Data**: String, Integer, ComplexNumber
- **Collections**: array, list, stack, queue, map, set, ...
- **Concurrency**: Actors, semaphores, promises, 
- **AI**: TensorFlow, PyTorch
- **Web**: HTTP verbs
- **Business**: Person, Customer, AnimalSighting

----
# Benefits
* **communication**: Abstractions (and as we will see, design patterns, implementation styles, architectural tactics ...) are a communication mechanism and a shorthand.
* **shared** **abstractions**: allow for quicker and more effective understanding of the code.
* **naturalness**: Some abstractions might come directly from the domain (e.g., a `Customer` class) (all of OO is arguably premised on this idea)
* **simplify**: hide complexity and implementation details
* **interoperability**: pass data around e.g. in JSON


All models are wrong; some are useful. 

----

# Activity: List API
Write a function to reverse a list with element-wise operations 
* `Node.getNext()`
* `Node.setNext()`


----
# Activity
Now write the same function for a list with list operations
* `List.get(i)`
* `List.set(i)`
* `List.remove(i)`

----
# Activity
Finally, write the function with element operations
* `Node.getNext()`
* `Node.setNext()`
* `Node.getPrev()`
* `Node.setPrev()`

What does [Java](https://docs.oracle.com/javase/8/docs/api/java/util/List.html) do in this case? What about Python? 

----
# Lists
Many different operations and syntactic formulations (list comprehensions, direct access, function access).

Like all abstractions, hides some irrelevant information from the user (in this case, how it is stored on disk).

Good abstraction leaves implementation details to talented developer (e.g. Java collections framework).

----
# Example: Promises 

Concurrency is a well known challenge for people to comprehend. One tricky part in Javascript (among others) has been the idea of callbacks. A callback is something like
```
function myfunc(callback, param1) {
    //do stuff
    callback(result);
}
```
And the advantage is it can execute asynchronously. But you can end up with long nested chains of callbacks, making this abstraction hard to parse.

----
# Example: Promises
A new abstraction called `Promise` was introduced to manage this chaining. 

```
let myPromise = new Promise(function(myResolve, myReject) {
    // slow code (e.g. network access)

    myResolve(); // when successful
    myReject();  // when error
});
```
And then the caller uses a Promise consumer: 
```
myPromise.then(
  function(value) { /* code if successful */ },
  function(error) { /* code if some error */ }
);
```
and the promise knows to call the appropriate function. 

----
# Promise Advantages
The big advantage is chaining Promises, so we avoid deeply nested callback chains. Instead, we get some guarantees of how the Promises return, and can attach a single error handler. 

There are [more reasons to use Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises), and their evolution, `async/await` but this covers the abstraction and what it enables. 

Note the development here: blocking functions --> asynchronous callbacks --> Promises --> Async/Await --> ...


----
# Good Abstractions
- Should do one thing and do it well
  - If hard to name, that's a bad sign 
- Implementation should not leak into abstraction
  - If there's details that do not need to be exposed, do not 
- Names matter
  - Be self-explanatory, consistent, regular

----
# Challenges
- What operations to include? (a.ka., interface)
  - Choices of operations has many consequences
- How to version your abstraction? Abstractions get stale.
- How does your abstraction fit with others? 

<!-- ----
# Designing a Good Abstraction
(see [Joshua Bloch](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/32713.pdf)) -->


----
# Caveat: Leaky Abstractions
Think about our List example. Where could our abstraction get us into trouble? 

A *leaky abstraction* is an abstraction in which the hidden details can leak out of the abstraction boundaries. For example, thinking of time as a single, 24h cycle without understanding time zones or leap seconds. Or not understanding that [the world isn't ASCII-based](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/).

---- 
# Build an Abstraction
* Groups of 2
* On paper/tablet:
    * Design an abstraction for managing a list of endangered species in BC. 
      * Species may be in the same Family
      * Families are contained by Classes which are contained by Phyla.
      * Species 

----
# Use An Abstraction
* Pass your paper to another group. 
* Now create an algorithm to (tbd)