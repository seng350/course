# Software Architecture and Design: SENG 350
-------------------------
**DRAFT**

## Schedule and Topics

The following schedule is subject to change. All deadlines and due dates listed here are the official dates. 

| Module & Topics | Other Resources | Readings  | Deadlines |
| --------------------------------------------------------- | --------- | ---------------- |------- |
|  Intro; introductions; Project outlined. [What is Software Architecture](https://github.com/SENG480/course/blob/master/lectures/1-intro.md)? | | text chapter 1 | |
|  [Software arch overview](https://github.com/SENG480/course/blob/master/lectures/2-arch.md). | | text chapter 2 | |
|  Github/Git tutorial || |
|  [Reading Code.](https://github.com/SENG480/course/blob/master/lectures/3-reading.md) | | chapter 3 text, source code of TBD | | 
|  [Architecture Stakeholders and Requirements](https://github.com/SENG480/course/blob/master/lectures/4-req.md). | | text chapter 16  |  |
|  Midterm 1 | | | **Midterm** |
| [Views on Architecture - Modules](https://github.com/SENG480/course/blob/master/lectures/5-modules.md) | | text chapter 18 |  |
| [Views part 2 - C&C](https://github.com/SENG480/course/blob/master/lectures/6-cc.md) | [SEI view example](https://wiki.sei.cmu.edu/sad/index.php/OPC_Module_Uses_View) | text chapter 4 | | 
| [Architecture and Design](https://github.com/SENG480/course/blob/master/lectures/7-design.md) | [What is Architectural Design](http://www.informit.com/articles/article.aspx?p=2738304&seqNum=2) | text chapter 17  |  | |
|  [Documenting behavior](https://github.com/SENG480/course/blob/master/lectures/8-behavior.md)  | | [SEI behavior tech report](https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=5847) | || |
|  Midterm  2 | | | **Midterm** |
|   [API and Interface documentation](https://github.com/SENG480/course/blob/master/lectures/9-interfaces.md).  | | [Interface documentation](https://resources.sei.cmu.edu/asset_files/TechnicalNote/2002_004_001_13973.pdf) |   |
| [Architecture analysis](https://github.com/SENG480/course/blob/master/lectures/12-analysis.md) | | ch 21  |
|   [Technical Debt and Metrics](https://github.com/SENG480/course/blob/master/lectures/10-td.md) | | my [Field Study of TD](https://insights.sei.cmu.edu/sei_blog/2015/07/a-field-study-of-technical-debt.html) • [metrics and TD](https://almossawi.com/firefox/prose-part-two/) | |
|  Midterm 3 | | | **Midterm** |

## Preambular
*Calendar Entry*: An introduction to analysis and design of software architectures with architecture description languages and their subsequent synthesis at the program level. Topics include requirements analysis, analysis and design of static and dynamic view points of architectures and model driven engineering. Architectural styles and tactics are introduced and applied as solutions to recurring design problems. Students are familiarized with component reuse, event-driven programming and computer-aided software engineering tools. The course includes a major design project.

(the official course syllabus is [distributed via HEAT](https://heat.csc.uvic.ca/coview/outline/2019/Fall/SENG/350?unp=t))

### Past versions:

* 

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

[Slack](https://seng350-f17.slack.com) will be the primary mechanism used for communication in the class. My rationale (apart from being tools used in practice) is to expose the class as a whole to questions about assignment and lectures. 

Grades are distributed via Connex for privacy compliance.

University and department policies on professional conduct and integrity are applicable. Feel free to see me in person, or via UVic email, for personal questions.

## Marking Overview
The final mark is weighted as following:
- 1% assignment, 
- 60% midterms,
- 9% participation,
- 30% substantial group project

### Assignments
One individual assignment worth 1%.

### Participation
9%, based on class attendance, project participation, and activity in Github and Slack.

### Project
One group project, 30% of the mark. Group project marks are scaled according to individual performance. This is assessed by instructor observation and peer evaluation.

### Midterms
early Oct, 20% of final grade.
late Oct/early Nov, 20% of final grade.
late Nov, 20% of final grade.

Missing a midterm reweights the other midterms to 30%. 

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


