#Maven Plug-ins, Goals and Life Cycle
----------------------------

##  Maven Plug-ins and goals
------------------------------------------
A Maven plugin is a collection of one or more goals. A goal is a “unit of work” in Maven. It is possible to execute goals independently or a part of a larger chain of goals.

Goals can define parameters, which may have default values. Plugin goals can be attached to a life cycle phase. The goals are executed based on the information found in the POM of the project, e.g., the compiler:compile goal checks the POM for relevant parameters.

##Maven life cycle
Every build follows a specified life cycle. Maven comes with a default life cycle that includes the most common build phases like compiling, testing and packaging.

The following lists gives an overview of the important Maven life cycle phases.

 - validate - checks if the project is correct and all information is available
 - compile - compiles source code in binary artifacts
 - test - executes the tests
 - package - takes the compiled code and package it, for example into a JAR file.
 - integration-test - takes the packaged result and executes additional tests, which require the packaging
 - verify - performs checks if the package is valid
 - install - install the result of the package phase into the local Maven repository
 - deploy - deploys the package to a target, i.e. remote repository

For a complete list of the Maven phases see [Maven life cycle reference](http://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#Lifecycle_Reference).

If you instruct Maven to execute a phase, Maven executes all existing phases n the pre-defined sequence until has executed the defined phase. All relevant goals are executed during this process. A goal is relevant for a phase if the Maven plug-in or the POM bind this goal to the corresponding Maven life cycle phase.

  
  [NEXT](Maven_Repository.md)