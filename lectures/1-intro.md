---
Title: Module  1 - Introduction to Software Architecture
Author: Neil Ernst
---

# Introductions
I am [Neil Ernst](http://neilernst.net), assistant professor in the Department of CS, formerly a senior researcher and consultant at the SEI. I've approached software architecture from both an academic/research perspective, as wel l as a consulting engineer. In my four years at the SEI, I helped evaluate, document, and design software architectures in government and scientific settings.

<!-- show Github and Brightspace channels -->

This course looks at Software Architecture and Design. It has two main approaches.

 One---**Documenting**---is to prepare you to prepare and describe architectures you will be responsible for. For example, you move out into a government IT job. You are asked to prepare a modernization strategy for the Department of Finance. You will present that strategy to senior leaders who want to know the technical and non-technical details about your plan.

The second objective---**Understanding**---is to enable you to work on the opposite side. Given a software system, come up with intelligent questions and analysis to understand a) how it works b) what key requirements it satisfies c) what evidence supports that.

# Course Format
See the syllabus and [Readme](README.md) file.

# Project outline
The main deliverable in this course is a major, term-long project you will do with 2-3 other students, in groups of your choosing. I strongly suggest you pick students in the same lab section as that simplifies meeting times, and several labs are purely for project work. 

The overall goal of the project is to document and reverse-engineer the architecture, architectural choices, and abstractions of a large open-source system. 

Your *individual* project mark will reflect your team's performance, adjusted by a peer / instructor participation factor. If you do **nothing**, you can expect a 0 for the project (and will fail the course).

Group projects are best summarized by Dickens:

> It was the best of times, it was the worst of times, it was the age of wisdom, it was the age of foolishness, it was the epoch of belief, it was the epoch of incredulity, it was the season of Light, it was the season of Darkness, it was the spring of hope, it was the winter of despair, we had everything before us, we had nothing before us ... (A Tale of Two Cities)

We will go into detail about functioning well in groups, but you should not assume that your group's problems will be an excuse for poor performance. Turn the *winter of despair* into a *spring of hope* as early as you can.

# Software Architecture - What Is It?

(we brainstormed ideas on the blackboard)

## Definitions

Here are three definitions. 

1. "the important stuff ... whatever that is ([Martin Fowler](http://files.catwell.info/misc/mirror/2003-martin-fowler-who-needs-an-architect.pdf))" 
2. “Architecture is the decisions that you wish you could get right early in a project.” Ralph Johnson
3. the “...significant design decisions (where significant is measured by the cost of change).” (Grady Booch)

<!--  (we discussed each definition)  -->

## Our definition
Here is the definition we will use. It is designed to orient us to the notion that there is not just one **thing** to call the architecture, but rather a set of *structures* that help us reason about what the system is doing.

> The software architecture of a system is the set of structures needed to reason about the system, which comprise the software elements, relations among them, and properties of both. (text p.4)

<!-- first lecture here -->

