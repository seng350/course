# Software Architecture and Design: SENG 350
-------------------------

## Schedule and Topics

See the schedule on Brightspace for quizzes and project milestones. All submissions occur on Brightspace. Videos are posted on Brightspace in the Echo360 section. 

### Modules

| Module | Topics | Other Resources | Readings  |
|---| --------------------------------------------------------- | --------- | ----------------|
| 1 | [What is Software Architecture?](https://github.com/SENG350/course/blob/master/lectures/1-intro.md) • [Reading Code](lectures/3-reading.md) | [500L Web Server](http://aosabook.org/en/500L/a-web-crawler-with-asyncio-coroutines.html) and [src](https://github.com/aosabook/500lines/tree/master/crawler) | text chapter 1  |
| 2 |  [Software arch overview](https://github.com/SENG350/course/blob/master/lectures/2-arch.md) | [cost of change](http://www.agilemodeling.com/essays/costOfChange.htm) • [arch role](https://raw.githubusercontent.com/seng350/course/master/lectures/img/add3.jpg) • [Boehm cost curve](lectures/img/How-Much-Architecting-is-Enough.png) | text chapter 2 • [Architect Roles Map](https://eltjopoort.nl/blog/2019/06/25/a-map-to-waterfall-wasteland-and-the-agile-outback/) • [node module problems](https://www.davidhaney.io/npm-left-pad-have-we-forgotten-how-to-program/); |
|3 |  [Architecture Stakeholders and Quality Attributes](https://github.com/SENG350/course/blob/master/lectures/4-req.md) | | text chapter 3, 22.8, 19  |
| 4 | [Abstractions](lectures/abstraction.md) | | [Fairbanks](https://www.georgefairbanks.com/e-book/) chapter 10.1-10.5 inclusive, 11 all |
| 5 | [Architecture Views & Styles](https://github.com/SENG350/course/blob/master/lectures/5-modules.md) • [Views on Architecture - C&C](https://github.com/SENG350/course/blob/master/lectures/6-cc.md) |[SEI view example](https://wiki.sei.cmu.edu/sad/index.php/OPC_Module_Uses_View)  | text chapter 22.1-4 |
| 6 | [Architecture and Design](https://github.com/SENG350/course/blob/master/lectures/7-design.md) • [OO Principles](lectures/ooprinciples.md) | [What is Architectural Design](http://www.informit.com/articles/article.aspx?p=2738304&seqNum=2) | [HomeAssistant sections 0-5](home_assistant_arch.pdf) • text chapter 20  |
| 7 | [Design Patterns](lectures/patterns.md) | [Head-first design patterns](https://www-oreilly-com.ezproxy.library.uvic.ca/library/view/head-first-design/9781492077992/) | [DesignPatterns paper](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.44.9717) • source code |
| 7 | [Programming Styles]() | | Lopes ["Exercises in Programming Style"](https://learning-oreilly-com.ezproxy.library.uvic.ca/library/view/exercises-in-programming/9781482227376/cover.xhtml) (Uvic access required)|
| 8 | [Architecture analysis](https://github.com/SENG350/course/blob/master/lectures/12-analysis.md) | | text chapter 21  |

For module 7, readings are 
Prologue
Chapter 3, Monolithic
Chapter 4, Cookbook
Chapter 7, Infinite Mirror
Chapter 16, Introspective
Chapter 17, Reflective
Chapter 18, Aspects
Chapter 25, Persistent Tables
Chapter 26, Spreadsheet
Chapter 27, Lazy Rivers
Chapter 28, Actors

We will also cover these specific architecture tactics if time permits.
| Module | Topics | Other Resources | Readings  |
|---| --------------------------------------------------------- | --------- | ----------------|
| A1 | [Architecture Tactics-Availability](lectures/avail.md) | | text chapter 4, quality attribute chapters 5 |
| A2 | [Architecture Tactics - Modifiability](lectures/modifiability.md) | [Ambler CRC](http://www.agilemodeling.com/artifacts/crcModel.htm) | text chapter 8 |
| A3 | [Architecture Tactics - Privacy](lectures/privacy.md) | [Privacy Patterns](https://privacypatterns.org/) | none |
| A4 | [Architecture Tactics - Performance](lectures/performance.md) |  | Text chapter 9 |
| A5 | [Architecture Tactics - Safety](lectures/safety.md) || Text ch. 10 |


### Lab Schedule
* [Lab schedule](labs.md)

## Preambular
*Calendar Entry*: An introduction to analysis and design of software architectures with architecture description languages and their subsequent synthesis at the program level. Topics include requirements analysis, analysis and design of static and dynamic view points of architectures and model driven engineering. Architectural styles and tactics are introduced and applied as solutions to recurring design problems. Students are familiarized with component reuse, event-driven programming and computer-aided software engineering tools. The course includes a major design project.

(the official course syllabus is [distributed via HEAT](https://heat.csc.uvic.ca/coview/outline/2019/Fall/SENG/350?unp=t))

### Past versions:

* See repo history tag "Fall2019"

## Instructors
* [Neil Ernst](http://neilernst.net), instructor. Office hours on Zoom Tuesday 12:20-2:30 or by appt.
* TBD

Please use Brightspace to message the TAs first.

## Course Overview
Software is a long-lived and complex thing. This course is about understanding software in the large. 
We use the SEI text as a framework for understanding large-scale software systems. Topics include:

* what is architecture? Who are architects?
* what structures are important to understand?
* views on software systems
* software quality attributes
* architecture analysis and recovery
* architecture-driven design
* agile architecture
* design, architecture, and technical debt

After the course, students are able to:

* Apply software patterns and architectural styles to solve design problems
* Understand the value of quality attributes and scenarios in testing potential designs
* Analyse architectural approaches using rigorous techniques
* Understand what decisions are the architecturally significant decisions, and which should be left to developers.
* Languages and notations, including the UML, for abstracting design models.

## Course Success
This course is divided into ten main modules, each addressing a major topic in software architecture. Modules are spread over two lectures and involve mandatory reading and practice exercises. To be able to follow the pace of the course, the reading must be done before the module lectures and the exercises must be completed within one week of the end of the second lecture of the module.

It's very hard to get good at anything without practice, and software design is no exception. Practice exercises are organized in terms of the module structure and are available on their individual pages. The exercises are designed to help you learn as effectively as possible: you can do them at your own pace, individually or in a group, repeat what's necessary, seek advice from anyone, and make mistakes and learn from them. For these and other reasons, they would be a poor choice for testing your knowledge of the material, so they are not graded. Instead, your practical skills will be evaluated through assignments.

Software design is a naturally abstract topic that needs to be applied to make any sense. The recipe for success in SENG 350 is to regularly prepare for lectures by doing the required readings in advance, attending the lectures and participating in the design and coding walk-throughs, then completing the related exercises as soon as possible. If you do this you may be pleased to discover that the material will grow on you almost subconsciously. The recipe for failure is to await the midterms and final, then furiously attempt to memorize the book and lecture material. Please opt for success.

## Operational Details

The class will use Brightspace to submit assignments and post grades, host videos, and facilitate discussion. Class notes are on Github. 

Please be aware our session is being recorded to allow students who are not able to attend to watch later. The recording will be posted in Brightspace. Students who have privacy concerns can contact me and may have the option to limit their personal information shared in the recording. If you have other questions or concerns regarding class recording and privacy please contact privacyinfo@uvic.ca.

University and department policies on professional conduct and integrity are applicable. Feel free to see me in person, or via UVic email, for personal questions.

## Marking Overview

Available on HEAT:

| **Coursework** | **Weight (out of 100%)** |
| :------------- | :----------------------- |
| 5 Quizzes      | 10%                      |
| Midterm Exams  | 30%                      |
| Project        | 60%                      |

Project details and the quizzes are on Brightspace. Quizzes will be completed on Brightspace so please bring something with internet access on those days.

## Resources

### Books
* SEI Software Architecture in Practice, Len Bass, Paul Clements, Rick Kazman. <s>3rd</s> 4th Edition. 2021
* Exercises in Programming Style, Crista Lopes, 2015 (there's a new version as well, but we have access to the first)
* [Just Enough Software Architecture](https://www.georgefairbanks.com/e-book/), by George Fairbanks, Marshall and Brainerd, 2010.

### Other texts

* Design It! From Programmer to Software Architect, by Michael Keeling, Pragmatic Programmers 2017.
* Documenting Software Architectures, by Paul Clements et al., Addison-Wesley, 2011.
* Designing Software Architecture, A Practical Approach, by Humberto Cervantes and Rick Kazman, Addison-Wesley 2017.
* Continuous Architecture in Practice, Erder, Pureur, Woods, Pragmatic Press, 2020.
* Software Systems Architecture: Working with Stakeholders Using Viewpoints and Perspectives, by Nick Rosanski and Eoin Woods, Addison-Wesley, 2011.
* Applied Software Architecture, Christine Hofmeister, Rod Nord, Dilip Soni, Addison-Wesley, 2000. 
* Essential Software Architecture, by Ian Gorton, Springer, 2011.
* Software Architecture: Perspectives on an emerging discipline, Mary Shaw and David Garlan, Prentice-Hall, 1996.
* Architecture of Open-Source Applications, Amy Brown and Greg Wilson, eds. http://aosabook.org

