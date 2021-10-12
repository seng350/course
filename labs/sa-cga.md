---
author: nernst
date: Oct 2021
Title: Call Graph Analysis
---

# Types of Static Analysis

Last lab we talked about static rule-checking -- *code quality* -- with tools like CodeScene. Those tools take a list of potential problems, like a linter, e.g. [FindBugs](http://findbugs.sourceforge.net/), and scan the source code to see if there are violations. In some cases they expand the types of rules to include things like social problems (too few developers over time, for example). 

But static analysis (analysis of code that is not compiled) is much more than that. In this lab we will explore one of those other facets, **call-graph analysis**. 

## Proving Properties with Static Analysis 

There are two major goals of static analysis (SA). The *first* is to help build program understanding. In running SA tools, you develop a sense for the complexity and nuance in the program's source code. 

The *second* goal is to find errors. Not infrequently bugs are difficult to reason over just by **inspecting** the code. For example, humans tend to be poor at understanding complex conditionals. We struggle to understand whether a particular pointer is actually initialized or not. We write for loops that allow for arbitrary code exection. And so on.

## Defects of Interest

-  Uncomon execution paths (edge cases, rare contexts)
- Brute forcing execution of all paths is infeasible
- SA checks compliance to simple rules:
  - Buffer overruns, input validation
  - Memory safety: unitialized data
  - Resource leaks
  - API protocols like device driver interfaces
  - Concurrency problems like data races

These are often lumped together under the term "formal methods", because they typically use symbolic logic to establish properties. For example we can use computation tree logic (CTL) to establish that a certain variable never dereferences a null value (and crashes).

In general, proving any property about a program is undecidable, and so we cannot guarantee we find ALL bugs, that ALL bugs found are bugs, or that the approach terminates.

# The Heartbleed bug

OpenSSL is a critical security library for SSL communication over the internet. In 2014 a [bug](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-0160) was found in it that allowed buffer over-read, i.e. you could ask for more information than you should be getting, including other people's keys. The erroneous code was in [this commit](https://github.com/openssl/openssl/commit/96db9023b881d7cd9f379b0c154650d6c108e9a3).

![](https://imgs.xkcd.com/comics/heartbleed_explanation_2x.png)

Possible Preventions:

- Risk analysis
- Fuzz testing / [robustness testing with more inputs](https://web.archive.org/web/20170202064748/https://www.dwheeler.com/essays/heartbleed.html)
- Inspection / code review of critical libraries
- Static analysis! 

# Call Graph Analysis

One important input to these more formal analyses is a precise representation of the program itself. We could create an abstract syntax tree to capture the program syntax. This shows how the program is constructed. Another question however is how the program executes. To examine this it would be helpful to examine how the program's units - files, functions, modules - connect to each other. Most often this means following paths through the execution of a program, e.g., branches and function calls. This is a **call graph**. To simplify analysis it often helps to abstract the details of Java programs into an intermediate representation (below called Jimple), which hides irrelevant information. 

## Generating Call Graphs

There are many libraries for creating call graphs (none of them are perfect). These include [Depends](https://github.com/multilang-depends/depends), PyCG, and [Soot](https://github.com/noidsirius/SootTutorial/tree/master/docs/1), which we will examine in this lab.

## Running Soot

Follow the instructions [on the "HelloSoot" tutorial](https://github.com/noidsirius/SootTutorial/tree/master/docs/1). Soot is a call graph and static analysis tool for Java programs. You will need to use gradle to build the code, and run the analysis. 

## The sample program

```java
public class FizzBuzz {

    public void printFizzBuzz(int k){
        if (k%15==0)
            System.out.println("FizzBuzz");
        else if (k%5==0)
            System.out.println("Buzz");
        else if (k%3==0)
            System.out.println("Fizz");
        else
            System.out.println(k);
    }

    public void fizzBuzz(int n){
        for (int i=1; i<=n; i++)
            printFizzBuzz(i);
    }
}
```

We want to capture the call graph for this simple program. To do this we attach Soot instrumentation to the Java classes and print out the execution flows. Check out the Soot code in `src/main/java/dev/navids/soottutorial/hellosoot/HelloSoot.java`.

# So What?

This basic CFG shows us what the demo programs possible execution paths are. It tells us how the program is structured; it allows us to communicate that structure to others; to design tests to ensure the paths are all covered

# See also

* CMU, [Introduction to Program Analysis](https://cmu-program-analysis.github.io) course notes.
