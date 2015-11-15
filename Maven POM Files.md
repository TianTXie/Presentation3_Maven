

#Maven POM files
A Maven POM file (Project Object Model) is an XML file that describe the resources of the project. This includes the directories where the source code, test source etc. is located in, what external dependencies (JAR files) your projects has etc.

The POM file describes what to build, but most often not how to build it. How to build it is up to the Maven build phases and goals. You can insert custom actions (goals) into the Maven build phase if you need to, though.

Each project has a POM file. The POM file is named pom.xml and should be located in the root directory of your project. A project divided into subprojects will typically have one POM file for the parent project, and one POM file for each subproject. This structure allows both the total project to be built in one step, or any of the subprojects to be built separately.

Example POM
```
<project xmlns="http://maven.apache.org/POM/4.0.0"
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
   http://maven.apache.org/xsd/maven-4.0.0.xsd">
   <modelVersion>4.0.0</modelVersion>

   <groupId>com.companyname.project-group</groupId>
   <artifactId>project</artifactId>
   <version>1.0</version>

</project>
```
All POM files require the **project** element and three mandatory fields: **groupId, artifactId, version**.

The **groupId element** is a unique ID for an organization, or a project (an open source project, for instance). Most often you will use a group ID which is similar to the root Java package name of the project. For instance,  a banking group com.company.bank has all bank related projects.

The **artifactId** element contains the name of the project you are building. For example, consumer-banking. Along with the groupId, the artifactId defines the artifact's location within the repository.

The **version** element contains the version number of the project. If your project has been released in different versions, for instance an open source API, then it is useful to version the builds. That way users of your project can refer to a specific version of your project. The version number is used as a name for a subdirectory under the artifact ID directory. The version number is also used as part of the name of the artifact built.

If your project uses the Maven directory structure, and your project has no external dependencies, then the above minimal POM file is all you need to build your project.

If your project does not follow the standard directory structure, has external dependencies, or need special actions during building, you will need to add more elements to the POM file. These elements are listed in the Maven POM reference.

In general you can specify a lot of things in the POM which gives Maven more details about how to build your projects. See the Maven POM reference for more information about what can be specified.

All Maven POM files inherit from a super POM. If no super POM is specified, the POM file inherits from the base POM. Here is a diagram illustrating that:


![alt text](http://tutorials.jenkov.com/images/maven/maven-super-pom.png)
Super POM and POM inheritance

You can make a POM file explicitly inherit from another POM file. That way you can change the settings across all inheriting POM's via their common super POM. You specify the super POM at the top of a POM file like this:
```
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                      http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

        <parent>
        <groupId>org.code.csci</groupId>
        <artifactId>my-parent</artifactId>
        <version>2.0</version>
        <relativePath>../my-parent</relativePath>
        </parent>


    <artifactId>my-project</artifactId>
    ...
</project>
```
An inheriting POM file may override settings from a super POM. Just specify new settings in the inheriting POM file.

POM inheritance is also covered in more detail in the Maven POM reference.

With all this POM inheritance it may be hard to know what the total POM file looks like when Maven executes. The total POM file (result of all inheritance) is called the effective POM. You can get Maven to show you the effective POM using this command:
```
mvn help:effective-pom
```
This command will make Maven write out the effective POM to the command line prompt.
