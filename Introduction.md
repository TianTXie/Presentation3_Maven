# Introduction to Maven
------------


 ## What is Maven?  
 -----------------

Maven is an advanced build tool to support the developer at the whole process of a software project. Typical tasks of a build tool are the compilation of source code, running the tests and packaging the result into JAR files. In additional to these typical build capabilities, Maven can also perform related activities, e.g., create web sites, upload build results or generate reports.
Maven allows the developer to automate the process of the creation of the initial folder structure for the Java application, performing the compilation and testing and the packaging and deployment of the final product. It is implemented in Java which makes it platform-independent. Java is also the best work environment for Maven.

##Key features of Maven   
------------


Apache Maven can be used in environments where common build tools like GNU Make or Apache Ant were used. The key features of Maven are:


 -  Convention over configuration: Maven tries to avoid as much configuration as possible, by choosing real world default values and supplying project templates (archetypes).  

 - Dependency management: it is possible to define dependencies to other projects. During the build, the Maven build system resolves the dependencies and, if needed, it also builds the dependent projects.

 - Repository: project dependencies can be loaded from the local file system, from the Internet or public repositories. The company behind the Maven project also provides a central repository called Maven Central.


 - Extensible via plug-ins: The Maven build system is extensible via plug-ins, which allows keeping the Maven core small. The Maven core does for example not know how to compile Java source code, this is handled by the compiler plug-in.



 - Installing Maven  



In case you want to be able to use Maven from the command line you need to install the Maven command line support. If you plan to use Maven only from within your Eclipse IDE this installation is not required.
 For a manual installation you can download Maven from the following URL [Maven Download page!](http://maven.apache.org/download.cgi). Extract the downloaded distribution to a selected folder on your computer and add the M2_HOME environment pointing to this directory. Add M2_HOME/bin to your path variable.See Maven installation description for a detailed installation guide.  
 


 ## Maven Overview-Core Concepts  
 -----------------------------

Maven is centered around the concept of POM files (Project Object Model). A POM file is an XML representation of project resources like source code, test code, dependencies (external JARs used) etc. The POM contains references to all of these resources. The POM file should be located in the root directory of the project it belongs to.

Here is a diagram illustrating how Maven uses the POM file, and what the POM file primarily contains:
![alt text](http://tutorials.jenkov.com/images/maven/maven-overview-1.png)
           **Overview of Maven core concepts**    


  **POM Files**
  When you execute a Maven command you give Maven a POM file to execute the commands on. Maven will then execute the command on the resources described in the POM.  

  **Build Life Cycles, Phases and Goals**
  The build process in Maven is split up into build life cycles, phases and goals. A build life cycle consists of a sequence of build phases, and each build phase consists of a sequence of goals. When you run Maven you pass a command to Maven. This command is the name of a build life cycle, phase or goal. If a life cycle is requested executed, all build phases in that life cycle are executed. If a build phase is requested executed, all build phases before it in the pre-defined sequence of build phases are executed too.  

  **Dependencies and Repositories**
  One of the first goals Maven executes is to check the dependencies needed by your project. Dependencies are external JAR files (Java libraries) that your project uses. If the dependencies are not found in the local Maven repository, Maven downloads them from a central Maven repository and puts them in your local repository. The local repository is just a directory on your computer's hard disk. You can specify where the local repository should be located if you want to (I do). You can also specify which remote repository to use for downloading dependencies. All this will be explained in more detail later in this tutorial.  

  **Build Plugins**
  Build plugins are used to insert extra goals into a build phase. If you need to perform a set of actions for your project which are not covered by the standard Maven build phases and goals, you can add a plugin to the POM file. Maven has some standard plugins you can use, and you can also implement your own in Java if you need to.  

  **Build Profiles**
  Build profiles are used if you need to build your project in different ways. For instance, you may need to build your project for your local computer, for development and test. And you may need to build it for deployment on your production environment. These two builds may be different. To enable different builds you can add different build profiles to your POM files. When executing Maven you can tell which build profile to use.  


[NEXT](Maven_Environment Setup.md)
