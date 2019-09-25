---
Title: Project Requirements
Author: Neil Ernst 
---

# Overview
The course project is a semester long effort to design and implement a web application using Typescript as the programming language, Node.js as the server, and Express as middleware. While the world is <strike>cursed</strike>blessed with a plethora of Javascript web frameworks, in this course we will implement those concepts (i.e, MVC or some iteration thereof) ourselves.

There is no specified topic for the project. Your team will define the requirements and stakeholders as part of the deliverables, and then implement those requirements. I suggest focusing on an app that has some CRUD-style interaction (Create, Read, Update, Delete). Typically this is a standard intro to web development, e.g. Spring [PetClinic](https://github.com/spring-projects/spring-petclinic) or Node [Library](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/skeleton_website) examples.

Some examples:
- manage gaming identities on Xbox, Playstation, etc.
- keep track of a sports pool
- list of user weather stations

## Detailed Requirements

The following list contains a set of requirements for your course project. They are purposefully not written as a formal software requirements specification, as your first task will be to create and formalize such a specification. If you are unclear about anything here, please post your question to Slack. If a requirement is changed, I'll capture that in italics, or with a strikethrough. Also use Github's diff capability to see changes.

1. The app shall be Web-based and use the technologies introduced in the labs, in particular TypeScript, Node, Express, MongoDB.
2. The app shall not use <s>view/CSS templates (like Jade),</s> view engines (React). *Template engines like Pug/Jade/Mustache etc are acceptable*.
3. The app shall not use ORM tools such as Mongoose.
4. The app shall not use MVC frameworks *like Angular*.
4. For other libraries or APIs, check with your lab TA. *In general if it is intended to help make your app cool, I'm ok with it. If it is doing the design for you, less so.*
2. The app shall support different user IDs, each user ID should be able to create (update and delete) different aspects of your app. 
    1. Note: to keep the complexity of the project in check, you will not have to implement user authentication. The app should simply have a “user ID list” view that shows all known user IDs and allows the user to select one of them. 
    2. The app should support a special user ID “admin”. This user ID cannot be deleted and has the special ability to create or delete other (regular) user IDs.
		3. <s>Users can invite other users to *view* or *edit* their projects. However, only the project *owner* can delete a project. Users can surrender project ownership to another user.</s>
4. The app user interface should provide a structured, forms-based interface for entering and updating content. 
5. The app shall provide an overview page.
6. The app shall follow web accessibility practices as defined by Web Content Accessibility Guidelines (WCAG), Version 2.0, checkable at https://achecker.ca/checker/index.php
7. Check your code quality with an online tool like [BetterCodeHub](https://bettercodehub.com/ "Better Code Hub"), [SonarQube](https://www.sonarqube.org/ "SonarQube"), [Code Climate](https://codeclimate.com/ "Code Climate"), or [Code Inspector](https://www.code-inspector.com/ "Code Inspector Static Analysis Tool").

## Dates
See [the syllabus for all due dates](README.md). 

## Milestones

- **M0.** team formation and Github (0%, -10 if not done)
- **M1.** requirements and scenarios (10%)
- **M2.** detailed design (20%)
- **M3.** code iteration 1 (20%)
- **M3.5** code iteration 2 (5%)
- **M4.** code iteration 3 (30%)
- **M5.** demo (10%)
- **M6.** post-mortem report (5%)

## Teams
The project will be performed in groups of 3-4 students. All students in one group must be registered in the same lab section, as the lab time will be used to work on the project. The Project TAs will assign groups by Wednesday Sept. 11. You can email him any preferences to be assigned to the same group as your friend/classmate by Sept. 9th. (There is no guarantee that all preferences can be met.)

- If you are having trouble with your team (lazy group members, poor communication, technical trouble, etc.) **come see me or a TA as early as possible**. We cannot help you if you don't let us know. Telling me in April that the team was not effective will not be an excuse.
- A regular meeting schedule is highly recommended to keep everyone on track. You might want to follow a [Scrum style standup](https://www.mountaingoatsoftware.com/agile/scrum/meetings/daily-scrum): each team member says:
    -   What did you do since last meeting?
    -   What will you do before the next meeting?
    -   Are there any impediments in your way?
- You can organize how you wish, but everyone must contribute, and one person should be in charge of overall planning. 

All students are expected to participate equally in discussions, design and development. The instructor will make marking adjustments for individual students where this participation has not occurred; this may result in a failing grade for the project. At the mid-point and conclusion of the project you will be asked to evaluate your colleagues on the team. Your peer review score and participation on Github/Slack will strongly influence what percentage of the project mark you get. 

# Formats and Logistics
We will be using CI with [Travis](https://travis-ci.com/ "Travis CI") and Github. Table stakes for project marking is evidence that CI pipelines are being used and used effectively. Testing your code is mandatory, and tests should be relevant, informative, and passing.

Ensure your code works as a Docker container. We will mark by pulling the latest from DockerHub (milestone 4). 

# Milestones

## 0. Github (-10% if not done)

### Deliverables
- Create a repository using the Github Classroom link
- <s>send your Github IDs to TAs</s>
- update the Readme with your team's name, and 3 project *ideas*.

### Marking Guide
Simple. Do the above.

## 1. Features and Architecturally Significant Requirements (ASRs) 

### Deliverables
1. 7 user stories explaining features of your app at a high level. Add these as issues in Github.
2. 7 quality attribute scenarios, 3 of which you intend to test in your CI pipeline. They must be from 3 different Quality Attributes (e.g., usability, testability, maintainability). Add these as issues in Github, and explain the test procedure there as well. 

### Marking Guide
- Relevance of the ASRs to the project idea. 
- Appropriateness of scenarios.
- Thoughtfulness of user stories

## 2. Detailed design
Describe, in <5 pages, how you intend to solve the problem and implement user stories and the ASRs from M1. Include how you will continuously integrate and deploy the app and how you will test it. Since we know this is a web app, assume the reader is familiar with basic app design and instead elaborate on how you will make the app conform to the ASRs (e.g., ensure performance is satisfied).

### Deliverables
1. PlantUML or JetUML class and behavior diagrams. This should explain the module structure and runtime/C&C structure of your app. 
2. Design rationale, as Arch Decision Record

### Marking Guide
- 

## 3. Code iteration 1

### Deliverables
1. Commit latest, working code to Github tagged "sprint1"
2. Static analysis report
3. Passing Travis builds
4. Code coverage report.

### Marking Guide
- Code compiles (no marks otherwise)
- No huge problems reported by linters and analyses
- Test coverage and quality is good
- Software priniciples like good naming, comments, high cohesion are followed.

## 3.5. Code iteration 2
This is a check-in milestone, to ensure code is being written.

### Deliverables
1. As in iteration 1, but add a short note in the readme explaining what has improved.

### Marking Guide
- As in iteration 1

## 4. Code iteration 3

### Deliverables
1. Commit final, working code to Github tagged "sprint1"
2. As in iteration 2

### Marking Guide
- As in iteration 1/2

## 5. Final Demo 
During the last week of class, schedule some time with me and the TAs to show your final project, and walk us through the code/design.

### Other aspects to keep in mind


### Deliverables
Presentation must be attended by all group members, all of whom may be asked questions about the project.

### Marking Guide

## 6. Post-mortem
After class and the project are done, create a group retrospective document as a Markdown file called `retro.md`. It should reflect on what you learned, what you could do better, and how your design can be improved. 

### Other aspects to keep in mind


### Deliverables


### Marking Guide


# Helpful Links
* [Student's Guide to SE projects](http://www.cdf.toronto.edu/~csc301h/fall/csc301.pdf) 
* See [lab page](labs.md) for details on the technology. 
