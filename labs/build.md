---
Title: Building the projects
Author: Neil Ernst
Date: Sep 2021
---

# Lab 2: Building the Project

Building source code can be hugely frustrating (at least, that is MY experience!). In this lab the job is to download one of the projects you chose and get it built on one of your group's machines, or the lab machine. 

First, go through the [Docker tutorial](docker.md). Docker is becoming a pretty standard way to distribute working code, and I suggest it as a way to ensure your team are all using the same environment (for example, a particular version of Linux, NodeJS, and various libraries). Tons of time is wasted sorting out who has what version of a library. 

Next, pick one of the projects from the list you submitted, and get that project built. The TA will help you with config problems. Pick the team mate with the most modern computer, get Docker working, and then use Docker to build the project (in the 'clean' environment). 

The TA will walk you through two of the basic build tools: Make and Gradle, and how they differ from *package managers* like NPM.

## Make

The original and still in widespread use. Make simply takes directives and runs the targets specified in something called `Makefile`, e.g. `make clean` runs the task clean:

```
clean:
	rm -rf *.o
```

Caveat: whitespace is important in Make and makefiles, and a source of problems.

* [A decent tutorial](https://www.tutorialspoint.com/makefile/why_makefile.htm)

## Gradle

After `make` came a number of Java build tools (my sense is Make was acceptable in C development, although C has a number of build tools as well). The first was Ant, which used XML to specify build rules, and then Maven, which combined *build rules* - e.g., how to set a class path, where to find image files, how to run tests—with *package and dependency management*, e.g., I need the hibernate.jar libraries for this project. Maven was also verbose and XML based, and was also a programming language in itself, which leads to complex build files. 

[Gradle (link to tutorial)](https://docs.gradle.org/current/userguide/getting_started.html) is a more terse version of Maven with good support from the major IDEs. I like its simplicity and focus on the core aspects of getting a project to build on multiple different platforms. In theory, a Gradle script should be relatively cross platform. The way Gradle (and Maven) work best if if you follow the Gradle [file location conventions](https://docs.gradle.org/current/userguide/organizing_gradle_projects.html): for Java this means a folder structure like `src/main/java` and `src/test/java`. When you follow that, Gradle automatically knows where the src lives and your gradle file can be as simple as:

```
plugins {
    id 'application' 
}

repositories {
    mavenCentral() 
}

dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter:5.7.2' 

    implementation 'com.google.guava:guava:30.1.1-jre' 
}

application {
    mainClass = 'demo.App' 
}

tasks.named('test') {
    useJUnitPlatform() 
}
```

This specifies the place to find libraries, what file to run (i.e. where main() lives), and how to run tests (e.g., with `gradle test`). 

## Other tools

It seems like every time someone uses a build tool, they find a problem, and thus we have another build tool. So the universe of build tools is pretty infinite and language dependent. For Python, for example, you might see a constellation of tools like setuptools and pip to manage dependencies. 

As mentioned earlier, it is very useful to create a virtualized environment to manage the build and keep libraries independent (e.g., if your project needs Hibernate 6 but your personal project needs Hibernate 5). Therefore a clean install on a blank Docker image can be more useful than anything else. Virtual environments like `rbenv`, `virtualenv`, [`nvm`](https://github.com/nvm-sh/nvm) etc.