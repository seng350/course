---
Title: Project Requirements
Author: Neil Ernst 
---

# Overview
The course project is a semester long effort to apply the ideas behind code reading and communication to a realistic project.

## Dates
See [the syllabus for all due dates](). 

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

- Instructor assigned - see Slack
- If you are having trouble with your team (lazy group members, poor communication, technical trouble, etc.) **come see me or Omar as early as possible**. We cannot help you if you don't let us know. Telling me in April that the team was not effective will not be an excuse.
- A regular meeting schedule is highly recommended to keep everyone on track. You might want to follow a [Scrum style standup](https://www.mountaingoatsoftware.com/agile/scrum/meetings/daily-scrum): each team member says:
    -   What did you do since last meeting?
    -   What will you do before the next meeting?
    -   Are there any impediments in your way?
- You can organize how you wish, but everyone must contribute, and one person should be in charge of overall planning. 

All students are expected to participate equally in discussions, design and development. The instructor will make marking adjustments for individual students where this participation has not occurred; this may result in a failing grade for the project. At the mid-point and conclusion of the project you will be asked to evaluate your colleagues on the team. Your peer review score and participation on Github/Slack will strongly influence what percentage of the project mark you get. 

# Formats and Logistics
We will be using CI with Travis and Github. Table stakes for project marking is evidence that CI pipelines are being used and used effectively. Testing your code is mandatory, and tests should be relevant, informative, and passing.

Deploy your code using DockerHub and containers. We will mark by pulling the latest from DockerHub. 

# Milestones

## 0. Github (-10% if not done)

### Deliverables
- Create a repository using the Github Classroom link
- send your Github IDs to Omar
- update the Readme with your team's name, and 3 projects of interest.

### Marking Guide
Simple. Do the above.

## 1. Architecturally significant requirements (ASRs) 

### Deliverables
1. The list of ASRs
2. A fully worked out utility tree, with at least 7 prioritized quality attribute scenarios, 3 (of the 7) in template form.

### Marking Guide
- Relevance of the ASRs to the project. 
- Appropriateness of scenarios.
- Quality of scenarios.

## 2. Detailed design
Describe, in <5 pages, how you intend to solve the problem and implement the ASRs from M1. Include how you will continuously integrate and deploy the app and how you will test it. 

### Deliverables
1. PlantUML or JetUML class and behavior diagrams
2. Design rationale, as Arch Decision Record

### Marking Guide
- 

## 3. Code iteration 1

### Deliverables
1. Commit latest, working code to Github tagged "sprint1"
2. BetterCodeHub report
3. Passing Travis builds.
4. Code coverage report.

### Marking Guide
- Code compiles (no marks otherswise)
- BetterCodeHub score > 8
- Test coverage and quality is good
- Con


## 5. Final Demo 
During the last week of class, schedule some time with me and the TAs to show your final project, and walk us through the code/design.

### Other aspects to keep in mind


### Deliverables
Presentation must be attended by all group members, all of whom may be asked questions about the project.

### Marking Guide

## 6. Post-mortem
During the last week of class, schedule some time with me and the TAs to show your final project, and walk us through the code/design.

### Other aspects to keep in mind


### Deliverables
Presentation must be attended by all group members, all of whom may be asked questions about the project.

### Marking Guide


# Helpful Links
* [Student's Guide to SE projects](http://www.cdf.toronto.edu/~csc301h/fall/csc301.pdf) 
* [Spring MVC](https://spring.io/guides/gs/serving-web-content/)
* [GWT](http://www.gwtproject.org/doc/latest/tutorial/index.html)
