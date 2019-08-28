# Software Architecture and Design: SENG 350
-------------------------
**DRAFT**

## Schedule and Topics

The following schedule is subject to change. All deadlines and due dates listed here are the official dates. 

This semester I'm doing the schedule differently. Instead of detailed day by day schedules, I'll list the main modules, the slides, and then key dates. Modules are sequential, and I aim to do one module per week. If you miss a class, I assume you can figure out what you missed. If not, see your classmates. 

Lectures are **M,W,Th 3:30pm-4:30pm** (note, this is off cycle for the standard MR/TWF schedule). Class is in Cornett A221. Labs are in ELW B238.

### Modules

| Module | Topics | Other Resources | Readings  | 
|---| --------------------------------------------------------- | --------- | ----------------|
| 1 |   [What is Software Architecture?](https://github.com/SENG350/course/blob/master/lectures/1-intro.md) | | text chapter 1  |
| 2 |  [Software arch overview](https://github.com/SENG350/course/blob/master/lectures/2-arch.md) | | text chapter 2 ; [Architect Roles Map](https://eltjopoort.nl/blog/2019/06/25/a-map-to-waterfall-wasteland-and-the-agile-outback/)| 
|3 |  [Architecture Stakeholders and Quality Attributes](https://github.com/SENG350/course/blob/master/lectures/4-req.md). | | text chapter 16  | 
|4 | [Architecture Tactics]() | | text chapter 13, quality attribute chapters 5,7,8,9 | 
| 5 | [Views on Architecture - Modules](https://github.com/SENG350/course/blob/master/lectures/5-modules.md) | | text chapter 18 | 
| 6 | [Views on Architecture - C&C](https://github.com/SENG350/course/blob/master/lectures/6-cc.md) | [SEI view example](https://wiki.sei.cmu.edu/sad/index.php/OPC_Module_Uses_View) | text chapter 4 | 
| 7 | [Architecture and Design](https://github.com/SENG350/course/blob/master/lectures/7-design.md) | [What is Architectural Design](http://www.informit.com/articles/article.aspx?p=2738304&seqNum=2) | text chapter 17  | 
| 8  | [Architecture analysis](https://github.com/SENG350/course/blob/master/lectures/12-analysis.md) | | text chapter 21  |


### Key Dates
| Event | Deadline |
|-----|-----|
| Project: M0 | September 13 |
| Project: M1 | September 25 | 
| Quiz 1 | September 18 | 
| Project: M2 | Oct 4 |
|  Thanksgiving Day | **Oct 14** |
|  Quiz 2 |  |
| Project M3| Oct 25 |
|  Midterm  | **Oct 31** |
| Reading Break | Nov 11-13 (no class) |
|  Quiz 3  | |
| Project M3.5 | Nov 15 |
|  Quiz 4  | |
|  Quiz 5 | **Nov 28** |
| Project M4/5 demos and code reviews | Dec 2-5 |
| Last class | Dec 4 | 
| Project: M6 | Dec 11 |

### Lab Schedule
* [Lab schedule](labs.md)

## Preambular
*Calendar Entry*: An introduction to analysis and design of software architectures with architecture description languages and their subsequent synthesis at the program level. Topics include requirements analysis, analysis and design of static and dynamic view points of architectures and model driven engineering. Architectural styles and tactics are introduced and applied as solutions to recurring design problems. Students are familiarized with component reuse, event-driven programming and computer-aided software engineering tools. The course includes a major design project.

(the official course syllabus is [distributed via HEAT](https://heat.csc.uvic.ca/coview/outline/2019/Fall/SENG/350?unp=t))

### Past versions:

* somewhere in the vast abyss of unrecoverable knowledge that is Connex/Coursespaces

## Instructors
* [Neil Ernst](http://neilernst.net), instructor. Room ECS 560, office hours TBA, or by appt.

Please use Slack to message the TAs first.

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

## Deliverables
The class will use [Github](https://github.com/SENG350) and [Slack](https://join.slack.com/t/seng350uvic/signup). Students will have to register their Github username (either a permanent one or a throwaway) with the instructors. Those with an objection to using Github or Slack, please contact the instructor for workarounds. All Github activity is private to the class organization. Please see the privacy notice on the Connex site.

[Slack](https://seng350.slack.com) will be the primary mechanism used for communication in the class. My rationale (apart from being tools used in practice) is to expose the class as a whole to questions about assignment and lectures.  Please use the `general_2019` channel for discussion, as this Slack gets re-used year to year.

Grades are distributed via Connex for privacy compliance.

University and department policies on professional conduct and integrity are applicable. Feel free to see me in person, or via UVic email, for personal questions.

## Marking Overview
The final mark is weighted as following:
- 25% midterm,
- 10% participation,
- 10% quizzes
- 55% substantial group project

### Participation
10%, based on class attendance, lab attendance, and activity in Github and Slack. Project participation marks are marked separately and over/under-weight your group's mark.

### Project
One group project, 55% of the mark. Group project marks are scaled according to individual performance. This is assessed by instructor observation and peer evaluation.

### Midterms
Oct 31, 25% (tentative)

You must pass both the midterm and project to pass the course.
### Quizzes
5 short inclass quizzes will be used to gauge understanding of the material.

### Final
There is no final.

## Resources

1. [Slack](https://seng330uvic.slack.com)
2. [Github help pages](https://help.github.com)
3. [Github bootcamp](https://help.github.com/articles/set-up-git/)

### Books
* SEI Software Architecture in Practice, Len Bass, Paul Clements, Rick Kazman. 3rd Edition. 2013.

### Other texts
* Design It! From Programmer to Software Architect, by Michael Keeling, Pragmatic Programmers 2017.
* Just Enough Software Architecture, by George Fairbanks, Marshall and Brainerd, 2010.
* Documenting Software Architectures, by Paul Clements et al., Addison-Wesley, 2011.
* Designing Software Architecture, A Practical Approach, by Humberto Cervantes and Rick Kazman, Addison-Wesley 2017.
* Software Systems Architecture: Working with Stakeholders Using Viewpoints and Perspectives, by Nick Rosanski and Eoin Woods, Addison-Wesley, 2011.
* Applied Software Architecture, Christine Hofmeister, Rod Nord, Dilip Soni, Addison-Wesley, 2000. 
* Essential Software Architecture, by Ian Gorton, Springer, 2011.
* Software Architecture: Perspectives on an emerging discipline, Mary Shaw and David Garlan, Prentice-Hall, 1996.
* Architecture of Open-Source Applications, Amy Brown and Greg Wilson, eds. http://aosabook.org


